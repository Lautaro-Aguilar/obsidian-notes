El hook useEffect es un hook de [[React]] que permite sincronizar un componente con un sistema externo. 
```js
useEffect(setup, dependencies?)
```
`setup`: La [[funcion]] que vas a ejecutar en la lógica del useEffect,  la funcion que vas a ejecutar también puede opcionalmente devolver una función de limpieza. Cuando el componente se agrega al DOM, React va a ejecutar la función de configuración y después de cada re-renderizado con dependencias cambiadas, React primero va a limpiar y después ejecutara la función de configuración con los nuevos valores.
`dependencies`:  La lista de todos los valores reactivos referenciados dentro del código de configuración. Los valores reactivos incluyen props, state y todas las variables y funciones declaradas directamente dentro del cuerpo de tu componente. Si tu linter está configurado para React, verificará que cada valor reactivo esté correctamente especificado como una dependencia. La lista de dependencias debe tener un número constante de elementos y escribirse en línea como [dep1, dep2, dep3]. React comparará cada dependencia con su valor anterior usando la comparación [[Object.is]]. Si omites este argumento, tu efecto se volverá a ejecutar después de cada re-renderizado del componente. 

*Consulta la diferencia entre pasar una matriz de dependencias, una matriz vacía y ninguna dependencia.*