[[userStore]] es una clase en la aplicación que se encarga de gestionar el estado y las operaciones relacionadas con los usuarios. Utiliza MobX para la gestión del estado reactivo y Axios para las solicitudes HTTP.

#### Funcionalidades Principales:

1. **Estado del Usuario**:
    
    - [`token`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Token de autenticación del usuario.
    - [`user`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Información del usuario.
    - [`logged`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Estado de autenticación del usuario.
    - [`loading`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Estado de carga de las operaciones.
    - [`error`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Mensajes de error.
    - [`isGuest`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Indica si el usuario es un invitado.
    - [`ready`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Indica si las estructuras están inicializadas.
2. **Métodos**:
    
    - [`initStructs()`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Inicializa las estructuras necesarias.
    - [`cleanStorage()`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Limpia el token de autenticación del almacenamiento local.
    - [`saveStorage()`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Guarda el token de autenticación en el almacenamiento local.
    - [`saveGuestUser(username)`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Guarda la información del usuario invitado en el almacenamiento local.
    - [`cleanGuestUser()`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Limpia la información del usuario invitado del almacenamiento local.
    - [`getGuestUser()`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Obtiene la información del usuario invitado del almacenamiento local.
    - [`getStorage()`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Obtiene el token de autenticación del almacenamiento local y valida al usuario.
    - [`validUser()`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Valida el token de autenticación con el servidor.
    - [`logout()`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Cierra la sesión del usuario.
    - [`login(user, passwd, keep)`](vscode-file://vscode-app/c:/Users/LautaroPC/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html): Inicia sesión con las credenciales del usuario.