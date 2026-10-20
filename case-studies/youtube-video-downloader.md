# Descargador de videos de YouTube

**Código privado.** Se presenta como caso descriptivo, sin publicar el código del producto.

**Una aplicación local para elegir videos y gestionar su descarga.**

Es el proyecto cuyo repositorio se llama `dj-video-prep`. Es independiente de [Soulmate](soulmate.md).

## Flujo de trabajo

1. Cargar una lista pública de Spotify como listado de canciones a preparar.
2. Buscar videos candidatos de YouTube para cada canción.
3. Previsualizar los candidatos y confirmar el video elegido.
4. Descargar selecciones individuales o un lote revisado.
5. Seguir el progreso y guardar los archivos terminados en la carpeta elegida.

La interfaz mantiene la selección bajo control del usuario. Las recomendaciones ayudan a revisar; no aprueban automáticamente candidatos para su descarga.

## Implementación

| Capa | Responsabilidad |
| --- | --- |
| Interfaz de navegador | Revisión de candidatos, previsualización integrada, selección, progreso de la cola y controles de destino. |
| Servidor en Python | Solicitudes de búsqueda, endpoints locales y coordinación de las descargas. |
| SQLite | Caché de búsquedas, registros de descargas y preferencias de destino. |
| Proceso de descarga | Tareas secuenciales, reintentos de fallos y prevención de tareas simultáneas duplicadas. |
| Herramientas multimedia | Descarga y combinación de pistas de video y audio en los archivos finales. |

## Decisiones que lo convierten en una herramienta útil

**Guardar las búsquedas en caché.** Los resultados almacenados se pueden reutilizar sin repetir la misma consulta externa cada vez.

**Conservar el estado de las tareas.** El trabajo terminado persiste tras un reinicio y las tareas interrumpidas se pueden reintentar.

**Permitir seguir trabajando durante una descarga.** La revisión de candidatos y la descarga de selecciones confirmadas son actividades independientes.

**Hacer explícito el destino.** El usuario elige una carpeta y la aplicación registra dónde corresponde guardar cada archivo.

## Alcance y evidencia

El proyecto documenta una descarga local completada y comprobada con `ffprobe`, incluyendo video, audio, duración y tamaño del archivo resultante.

La aplicación funciona localmente. Un servicio público alojado, las cuentas de múltiples usuarios y sus controles operativos requieren trabajo adicional. La calidad del video depende de la fuente y no aumenta por el hecho de descargarlo.

Pablo Moraga · Dasein Futures
