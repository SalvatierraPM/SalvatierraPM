# SignalTwin

**Código privado.** Se presenta como caso descriptivo, sin publicar el código del producto.

**Un entorno de simulación utilizado en el trabajo de Dasein Futures.**

SignalTwin conecta documentos de un caso, contexto estructurado, simulaciones e informes dentro de una aplicación. Lo utilizo para realizar simulaciones en Dasein Futures.

## El problema

Una decisión parte de información fragmentada: documentos, actores, relaciones, supuestos y posibles cambios. La aplicación organiza ese contexto en un proceso que se puede inspeccionar y utilizar para explorar escenarios.

## Flujo de trabajo

1. Incorporar los documentos del caso y delimitar la decisión.
2. Estructurar actores, relaciones y contexto relevante.
3. Preparar y ejecutar una simulación.
4. Revisar los resultados y el material que los respalda.
5. Producir informes para su interpretación y discusión.

## Enfoque técnico

| Capa | Responsabilidad |
| --- | --- |
| Interfaz en Vue | Guiar al usuario por el caso, el grafo, la simulación y los informes. |
| Backend en Python | Coordinar los servicios de la aplicación y el procesamiento asistido por modelos. |
| Integración de grafos | Representar y recuperar relaciones del contexto del caso. |
| Orquestación de simulaciones | Preparar configuraciones, gestionar la ejecución y recopilar resultados. |
| Revisión de resultados | Comprobar evidencias, coherencia de entidades, estructura de informes y límites metodológicos. |

## Decisiones de ingeniería

**Hacer visible la estructura intermedia.** El grafo y la configuración de la simulación forman parte del proceso y se pueden inspeccionar.

**Separar generación y revisión.** Los resultados generados necesitan comprobación de evidencias e interpretación antes de convertirse en un informe útil.

**Distinguir implementación y metodología.** Que una simulación funcione no demuestra por sí solo su precisión predictiva.

## Alcance y origen

SignalTwin amplía componentes de simulación de código abierto con servicios y un flujo de aplicación específicos de Dasein. El proyecto tiene una implementación considerable en frontend y backend; su código privado también contiene material exploratorio e interno.

El sistema apoya la simulación y la interpretación; no garantiza precisión predictiva. Los casos internos de ejemplo se identifican por separado del trabajo para clientes, y los resultados generados requieren revisión.

Pablo Moraga · Dasein Futures
