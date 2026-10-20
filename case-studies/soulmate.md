# Soulmate — edición personal

**Código abierto (OSS).**

**Una aplicación de escritorio para trabajar con música.**

Soulmate conecta listas musicales, búsqueda y coincidencia de canciones, y gestión de descargas de audio. El proyecto conjunto y mi edición personal local son partes distintas de su historia.

## Flujo de trabajo

`Lista musical → canciones → búsqueda y coincidencias → cola de descarga → archivos de audio locales`

La implementación de escritorio revisada integra Spotify, listas públicas y un servicio de Soulseek en segundo plano. Separa la interfaz de escritorio de la coordinación de servicios y del estado persistente de la aplicación.

## Enfoque técnico

- Estructura de una aplicación de escritorio, con interfaz y servicios en segundo plano.
- OAuth e integración con servicios musicales externos.
- Búsqueda de coincidencias entre canciones y gestión de una cola de descarga.
- Comunicación entre la interfaz y los procesos en segundo plano.
- Preferencias, estado persistente y seguimiento de las descargas.

El código de escritorio revisado utiliza Electron, TypeScript y React. Los módulos de servicios separan el acceso a listas, la búsqueda de coincidencias, la gestión de la cola y la interacción con el servicio de descarga.

## Contribución y versiones

El proyecto alojado bajo la cuenta `lhommeduchili` fue un trabajo conjunto. También mantengo una versión personal local. El trabajo compartido y la edición personal se presentan y atribuyen por separado.

Soulmate se presenta como proyecto de código abierto. La atribución distingue el trabajo conjunto de la edición personal local. Este lote de perfil no contiene una copia adicional de su código ni una aplicación empaquetada; tampoco presenta todas las funciones en desarrollo como parte de una versión publicada.

## Una aplicación distinta del descargador de YouTube

Soulmate se enfoca en un flujo de audio desde el escritorio. El [descargador de videos de YouTube](youtube-video-downloader.md) es otra aplicación, destinada a revisar candidatos y descargar archivos de video.

Pablo Moraga · Dasein Futures
