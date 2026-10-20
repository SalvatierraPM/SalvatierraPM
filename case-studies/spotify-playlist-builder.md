# Spotify Playlist Builder

**Código privado.** Se presenta como caso descriptivo, sin publicar el código del producto.

**Una aplicación a medida entregada para resolver una necesidad real de creación de listas musicales.**

Entregué esta herramienta como una aplicación pagada. Crea listas de Spotify a partir de una lista de origen o del catálogo de un artista, con modos de selección adaptados a la forma de trabajar del usuario.

## Flujo de trabajo

1. Conectar una cuenta de Spotify mediante OAuth.
2. Elegir una lista de origen o un artista.
3. Seleccionar un modo de generación.
4. Preparar la selección y crear la lista resultante en Spotify.
5. Abrir el resultado y seguir trabajando con él.

Los modos incluyen rondas equilibradas, una canción por artista y selecciones distribuidas entre los álbumes de un artista.

## Arquitectura

| Parte | Implementación |
| --- | --- |
| Aplicación web | Node.js, Express y TypeScript. |
| Integración con Spotify | Autenticación, listas de la cuenta, catálogos de artistas, creación de listas e incorporación de canciones. |
| Lógica de selección | Funciones específicas para distribuir selecciones entre conjuntos de artistas y álbumes. |
| Estado | Persistencia en archivos de las rondas, listas generadas y contextos de clientes. |

## Decisiones de ingeniería

**Separar la selección musical de las operaciones de API.** Las reglas que eligen canciones son independientes de las solicitudes a Spotify y de la presentación de la interfaz.

**Admitir distintas entradas.** Las listas existentes y los catálogos de artistas dan lugar a modos de selección diferentes.

**Conservar el contexto entre operaciones.** La aplicación guarda estado para dar continuidad al trabajo entre solicitudes.

## Evidencia y alcance

Es una herramienta a medida entregada. Su entrega no equivale al lanzamiento de un SaaS público para múltiples clientes. No demuestra una base de datos relacional; Revenue PRO es el ejemplo más relevante de esa parte de mi trabajo.

La integración depende de la autorización de Spotify y de los permisos concedidos por el titular de la cuenta. El comportamiento de selección depende del modo elegido y del estado de la aplicación.

El código permanece privado. Este caso presenta el flujo y las decisiones técnicas; el paquete público no incluye una copia de su código.

Pablo Moraga · Dasein Futures
