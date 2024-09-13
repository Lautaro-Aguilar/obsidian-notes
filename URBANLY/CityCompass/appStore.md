appStore es una de las [[stores]] principales de la aplicación.

La función principal de la appStore es la de gestionar el [[estado global]] de la aplicación e inicializar datos y [[web workers]].

# Init()
```
async init() {
        if (!this.initData && !this.appDataReady) {
            this.initData = true;
            this.initWorkers();
            this.initAppData();
        }
    }
```
# initWorkers()
Se encarga de inicializar varios [[web workers]]
# initAppData()
Se encarga de inicializar las siguientes [[stores]] y [[services]] de la aplicación: 
1. [[userStore]]
2. [[sessionStore]]
3. [[poisStore]]
4. [[parcelsService]]
5. [[tejidoService]]
6. [[gridStore]]
7. [[availableUnitsService]]
8. [[amenitiesStore]]
9. [[scenarioStore]]
10. [[buildingsStore]]
11. [[mapStore]]
12. [[poisTableStores]]


Si no es un entorno de pruebas, restaura las [[sessions]] a través de [[sessionStore]] utilizando la función `restoreStores`:
```javascript
await sessionStore.restoreStores(sessionStore.currentSession);
```