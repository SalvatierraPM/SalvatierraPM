# SignalTwin

**Sistema de simulación multiagente con un motor dual, propagación de eventos entre entornos y control de calidad iterativo.**

**Código privado.** Este caso describe la arquitectura y las decisiones de ingeniería; no distribuye código, configuraciones operativas ni datos de clientes.

Desarrollo SignalTwin para explorar decisiones estratégicas mediante actores simulados, relaciones, contexto documental y dinámicas de interacción. Lo utilizamos para simulaciones en Dasein Futures. El producto reúne investigación, construcción del modelo del caso, ejecución, extracción de evidencias e informes con QC.

## Motor dual: dos entornos acoplados

Los agentes interactúan en dos entornos con dinámicas diferentes:

- **Flujo abierto:** publicaciones, reacciones y circulación de narrativas.
- **Comunidad temática:** conversaciones, argumentación e interacción en torno a temas.

El modo coordinado avanza ambos entornos por rondas. Un puente de eventos analiza lo ocurrido en uno y transmite eventos al otro, con demoras y reglas configurables. Esto permite explorar cómo una conversación, una señal regulatoria o una presión pública puede repercutir entre entornos.

La arquitectura dual se refiere a esos dos espacios de interacción y su acoplamiento; no implica utilizar dos proveedores de modelos. El puente debe estar habilitado para producir propagación entre entornos.

## Del contexto a una ejecución inspeccionable

`Documentos e investigación → señales → ontología y grafo → configuración de agentes → simulación dual → evidencias → informes → QC y mejora`

| Subsistema | Trabajo de ingeniería |
| --- | --- |
| Contexto y modelo del caso | Estructurar actores, relaciones y conceptos a partir del material disponible. |
| Grafos | Adaptador de grafo local para almacenar y consultar entidades, relaciones y episodios mediante una interfaz común. |
| Comportamiento de agentes | Incorporar compromisos, actos de habla y quiebres como señales que influyen en activación y selección de agentes. |
| Ejecución dual | Coordinar rondas, recoger acciones y propagar eventos entre los dos entornos. |
| Evidencias | Procesar registros JSONL y SQLite para extraer actividad, coaliciones, citas, cambios temporales y referencias canónicas de actores. |
| Aplicación | Backend Python/Flask e interfaz Vue para configurar y recorrer el caso, el grafo, la simulación y los resultados. |

El modelo lingüístico de comportamiento tiene parámetros configurables. Su implementación permite experimentar con esos supuestos; no demuestra que estén calibrados contra comportamiento real.

## QC como subsistema del producto

El control de calidad distingue dos problemas que necesitan respuestas diferentes:

**Fallos técnicos:** configuración incompleta, actividad insuficiente, problemas de grafo o artefactos de simulación inconsistentes. El sistema dispone de comprobaciones previas y posteriores para diagnosticar esas condiciones.

**Fallos de calidad del informe:** actores omitidos, afirmaciones sin respaldo, análisis débil o problemas de coherencia. Una rúbrica de diez dimensiones evalúa el resultado; un módulo de mejora trabaja sobre las secciones deficientes y vuelve a evaluarlas, hasta alcanzar el objetivo configurado o el límite de iteraciones.

El ciclo conserva puntuaciones por dimensión, mejoras realizadas y estado final. Puede dejar un resultado pendiente de revisión humana. Los controles de grounding contrastan entidades y referencias con el contexto y las evidencias de la simulación.

## Decisiones que definen el sistema

- **Acoplar los entornos mediante eventos explícitos.** La interacción entre mundos forma parte del estado y del recorrido de ejecución.
- **Construir evidencia antes de redactar.** El informe recibe material estructurado de la ejecución para sostener sus afirmaciones.
- **Tratar QC como una etapa con estado.** Evaluación, mejora y diagnóstico quedan registrados y se pueden revisar.
- **Separar la interfaz, el runtime y los adaptadores.** Cada capa tiene responsabilidades propias dentro del mismo producto.

## Contribución, origen y alcance

SignalTwin partió de componentes abiertos de simulación y evolucionó con una aplicación y servicios específicos de Dasein: contexto y ontología, integración de grafos, coordinación dual, capa lingüística, extracción de evidencias, auditoría e informes con QC.

Este caso se basa en la revisión del código y la documentación del 21 de octubre de 2026. No se ejecutó una simulación ni una evaluación nueva para redactarlo. Las puntuaciones internas de QC miden criterios de la rúbrica; no son probabilidades de acierto ni una validación predictiva.

Pablo Moraga · Dasein Futures
