# Dale Color / ColourHunt

**Código privado.** Se presenta como caso descriptivo, sin publicar el código del producto.

**Una aplicación nativa de iPhone que convierte una idea de juego en un recorrido multijugador completo.**

Dale Color es el nombre actual del proyecto cuya carpeta local se llama `ColourHunt`. Grupos privados de dos a ocho personas crean una sala, reciben colores, reúnen fotos, preparan collages, votan y revisan el resultado.

El repositorio es privado. La última entrega documentada mantiene pendientes TestFlight y App Store; este caso no presenta la aplicación como publicada.

## Producto y arquitectura

| Parte | Responsabilidad |
| --- | --- |
| App de iPhone en SwiftUI | Crear y unirse a salas, cámara y galería, edición de collages, votación y compartir. |
| Paquete de dominio en Swift | Reglas del juego, asignación de colores, transiciones de estado y lógica de votación. |
| Backend Appwrite | Operaciones autoritativas de las partidas, persistencia, acceso privado a fotos y procesamiento en segundo plano. |
| Portal en React | Documentos públicos de soporte y revisión humana protegida de reportes. |

El backend controla la secuencia:

`lobby → assigning → active → voting → review → completed`

Las animaciones muestran un resultado decidido por las reglas. Las notificaciones en tiempo real indican a los clientes que deben solicitar un estado actualizado y autorizado de la partida.

## Decisiones de ingeniería

- **Aplicar las reglas en el servidor.** Los clientes no escriben directamente en las tablas de dominio.
- **Separar reglas y pantallas.** Un paquete Swift permite probar el comportamiento central de forma independiente.
- **Mantener las fotos privadas.** El teléfono redimensiona y reexporta las imágenes sin metadatos EXIF/GPS antes de subirlas; el backend aplica permisos por archivo.
- **Permitir reintentos en segundo plano.** Un worker gestiona temporizadores, retención, reintentos de borrado y entrega de notificaciones mediante una cola de salida.
- **Generar los archivos para compartir en el dispositivo.** El iPhone produce collages en formatos para distintos destinos.

Esta versión no clasifica imágenes mediante IA ni comprueba automáticamente si una foto contiene el color asignado. Los reportes se revisan de forma humana.

## Evidencia y estado de lanzamiento

El documento de entrega registra comprobaciones locales del **24 de agosto de 2026**: 40 pruebas de dominio Swift, 16 del backend, 9 del portal, compilación del portal y compilación Release sin firma para el simulador de iOS.

Esas pruebas históricas no se repitieron al preparar este caso. La última entrega documentó Appwrite pausado; su estado remoto actual no se ha vuelto a comprobar. Restaurar y validar el backend, completar el recorrido multijugador en iPhones físicos, firmar y distribuir siguen siendo tareas de lanzamiento según esa entrega.

## Qué demuestra

Desarrollar un producto interactivo con reglas de dominio, estado multijugador persistente, manejo de medios, operaciones de backend, administración y un camino de lanzamiento documentado. Aporta evidencia de desarrollo móvil y coordinación entre clientes y servidor.

Pablo Moraga · Dasein Futures
