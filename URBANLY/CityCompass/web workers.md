Un **Web Worker** es una característica de JavaScript que permite ejecutar scripts en segundo plano, en un hilo separado del hilo principal de la aplicación web. Esto es útil para realizar tareas que pueden ser intensivas en términos de procesamiento sin bloquear la interfaz de usuario.

### Características Principales

1. **Ejecución en Segundo Plano**: Los web workers permiten ejecutar código en un hilo separado, lo que evita que tareas intensivas bloqueen la interfaz de usuario.
2. **Comunicación con el Hilo Principal**: Los web workers se comunican con el hilo principal mediante mensajes (`postMessage` y `onmessage`).
3. **Contexto de Ejecución Aislado**: Los web workers no tienen acceso directo al DOM, `window`, `document`, o `parent`. Solo pueden acceder a un subconjunto limitado de funciones de JavaScript.