[[userStore]] es una clase en la aplicación que se encarga de gestionar el estado y las operaciones relacionadas con los usuarios. Utiliza [[MobX]] para la gestión del estado reactivo y Axios para las solicitudes HTTP.

#### Funcionalidades Principales:

1. **Estado del Usuario**:
    
    - `token`: Token de autenticación del usuario.
    - `user`: Información del usuario.
    - `logged` Estado de autenticación del usuario.
    - `loading`: Estado de carga de las operaciones.
    - `error`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Mensajes de error.
    - `isGuest`: Indica si el usuario es un invitado.
    - `ready`: Indica si las estructuras están inicializadas.
2. **Métodos**:
    
    - `initStructs()`: Inicializa las estructuras necesarias.
    - `cleanStorage()`: Limpia el token de autenticación del almacenamiento local.
    - `saveStorage()`: Guarda el token de autenticación en el almacenamiento local.
    - `saveGuestUser(username)`: Guarda la información del usuario invitado en el almacenamiento local.
    - `cleanGuestUser()`): Limpia la información del usuario invitado del almacenamiento local.
    - `getGuestUser()`:Obtiene la información del usuario invitado del almacenamiento local.
    - `getStorage()`: Obtiene el token de autenticación del almacenamiento local y valida al usuario.
    - `validUser()`: Valida el token de autenticación con el servidor.
    - `logout()`: Cierra la sesión del usuario.
    - `login(user, passwd, keep)`: Inicia sesión con las credenciales del usuario.

## Código
```javascript
import { action, makeObservable, observable, runInAction } from 'mobx';
import axios from 'axios';
import Config from '../services/Config';
import { USERS_SERVICE_URL } from '../configs';
class UserStore {
    token = '';
    @observable user = {};
    @observable logged = !Config.needLogin;
    @observable loading = true;
    @observable error;
    isGuest = false;
    ready = false;
    constructor() {
        makeObservable(this);
        this.getStorage();
    }
  
    @action
    async initStructs() {
        this.ready = true;
    }
  
    cleanStorage() {
        localStorage.setItem('token', '');
    }
  
    saveStorage() {
        localStorage.setItem('token', this.token);
    }
  
    saveGuestUser(username) {
        localStorage.setItem('isGuest', this.isGuest);
        localStorage.setItem('user', username);
    }
 
    cleanGuestUser() {
        localStorage.setItem('isGuest', false);
        localStorage.setItem('user', '');
    }
  
    getGuestUser() {
        const isGuest = localStorage.getItem('isGuest');
        const user = localStorage.getItem('user');
        if (isGuest && user) {
            this.isGuest = isGuest;
            this.user = user;
        } else
            this.isGuest = false;
            this.user = '';
    }
  
    @action
    getStorage() {
        const token = localStorage.getItem('token');
        if (token) {
            this.token = token;
            this.validUser();
        } else
            this.loading = false;
    }
  
    async validUser() {
        try {
            const url = USERS_SERVICE_URL + '/valid';
            const res = await axios.post(url, {}, { headers: { Authorization: 'Bearer '  this.token }});
            this.user = res.data.user;
            this.token = res.data.token;
            runInAction(() => {
                this.error = undefined;
                this.logged = true;
                this.loading = false;
            });
        } catch(err) {
            console.error('Error valid', err);
            this.token = undefined;
            runInAction(() => {
                this.error = undefined;
                this.logged = false;
                this.loading = false;
            });
        }
    }
  
    @action
    logout() {
        this.error = undefined;
        this.cleanStorage();
        this.logged = false;
    }
  
    async login(user, passwd, keep = false) {
        runInAction(() => {
            this.error = undefined;
            this.logged = false;
            this.loading = true;
        });
        const authObj = {
            user,
            passwd,
            region: Config.regionName
        };
        try {
            const url = USERS_SERVICE_URL + '/login';
            const res = await axios.post(url, authObj, {});
            this.user = res.data.user;
            this.token = res.data.token;
            runInAction(() => {
                this.logged = true;
                this.loading = false;
            });
            this.cleanStorage();
            if (keep) this.saveStorage();
        } catch(err) {
            console.error('Error login', err);
            runInAction(() => {
                this.error = "Invalid Username or Password";
                this.logged = false;
                this.loading = false;
            });
            return "Invalid Username or Password";
        }
    }
}
const userStore = new UserStore();
export default userStore;
```