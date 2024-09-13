Este componente se encarga de la gestion del [[estado global]] de la aplicación, inicializa [[stores]] y condiciona renderizados importantes mediante el uso del hook [[useEffect]], como mostrar una pantalla de carga ([[loading]]) 

```js
useEffect(() => {
        // order is important
        if (logged && !appDataReady) {
            appStore.init();
            return;
        }
        const setup = async () => {
            appStore.setLoadingText(_("loading.scenario"));
        scenarioStore.setCurrentScenario(scenarioStore.currentScenario[0], 0, false)
           scenarioStore.setCurrentScenario(scenarioStore.currentScenario[1], 1, false)
            appStore.setLoadingText('');
        };
        setup();
    }, [logged, appDataReady]);
```
La funcion encargada de inicializar toda la aplicación es la de `appStore.init()` esta funcion pertenece a [[appStore]], si appDataReady es true establece el estado de "cargando" y después establece los escenarios.