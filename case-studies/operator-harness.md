# Pablo Operator Harness

**Un plano de control para operar proyectos con agentes de IA: identidades, contexto, cuentas, reglas de trabajo y sesiones recuperables.**

**Código abierto (OSS).** La demo enlazada utiliza configuración ficticia. Los registros personales, referencias operativas y estados reales de mis proyectos quedan fuera del paquete.

Lo desarrollé para trabajar con Codex y Claude Code en distintos productos, organizaciones y clientes sin reconstruir manualmente todo el contexto en cada sesión. Lo utilizo en mi propio trabajo.

El problema incluye decidir qué proyecto está activo, a quién represento, qué cuentas y fuentes corresponden, dónde debe guardarse cada artefacto y qué controles deben revisarse antes de cerrar.

## Un contrato de trabajo antes de empezar

El Harness resuelve un proyecto por identificador o ubicación y reúne:

| Capa | Qué define |
| --- | --- |
| Identidad y organización | A quién representa el trabajo y a qué ámbito pertenece. |
| Registros de cuentas | Propiedad, finalidad y referencias de credenciales, sin almacenar secretos. |
| Perfil y nivel de rigor | Convenciones y controles esperados según el tipo de proyecto. |
| Fuentes de verdad | Repositorios, documentos y almacenes de conocimiento que corresponden al contexto. |
| Rutas de artefactos | Dónde guardar código, documentos, decisiones, entregas y material temporal. |
| Estado de sesión | Objetivo, trabajo completado, decisiones, evidencias y próxima acción. |

La configuración establece una jerarquía de política del operador, identidad y organización, perfil, manifiesto del proyecto y objetivo de sesión. Los controles efectivos combinan el perfil con las reglas del proyecto.

## Ciclo de operación

`init → open → trabajo → checkpoint → close`

- **`init`:** crea un manifiesto local del proyecto y evita sobrescribir uno existente.
- **`open`:** resuelve el contexto y presenta identidad, fuentes, rutas, cuentas referenciadas y controles activos.
- **`checkpoint`:** guarda objetivo, avances, decisiones, evidencias, notas y siguiente acción. Fusiona el progreso con el estado anterior.
- **`close`:** inspecciona cambios de Git, identifica documentos fuera de rutas y posibles cruces de ámbito, y prepara el traspaso de sesión.
- **`doctor`:** comprueba registros, referencias, rutas, coherencia de manifiestos e instrucciones y otras condiciones del entorno.
- **`sync`:** previsualiza o actualiza instrucciones compartidas para Codex y Claude Code bajo reglas de escritura controlada.

## Límites entre proyectos y continuidad entre agentes

El registro central mantiene metadatos y referencias. El conocimiento permanece en las raíces declaradas de cada proyecto u organización.

La inspección del entorno identifica posibles cambios fuera del ámbito previsto y documentos sin una ruta declarada. Las excepciones intencionales de infraestructura compartida necesitan rutas explícitas y una razón. Es una detección basada en rutas y cambios del entorno, no un aislamiento del sistema operativo.

La generación de `AGENTS.md` y `CLAUDE.md` permite previsualizar el contenido, crear archivos faltantes o actualizar archivos marcados como gestionados. Rechaza sobrescribir instrucciones ajenas sin esa marca. Esto genera archivos coherentes; no demuestra por sí solo que cada agente haya cargado o seguido las instrucciones.

## Persistencia y controles de escritura

El núcleo es una CLI en Python con biblioteca estándar y registros JSON. Los puntos de control se escriben mediante sustitución atómica y los traspasos se guardan como material local de sesión.

El cierre presenta propuestas para devolver decisiones o contexto a sus destinos; no ejecuta esas escrituras externas. Los controles de calidad se resuelven y presentan como obligaciones de trabajo: el Harness no ejecuta automáticamente todas las pruebas de cada repositorio ni sustituye los permisos de las herramientas conectadas.

## Demo y verificación

**[Descargar la demo ejecutable](../downloads/operator-harness-demo.zip).** Requiere Python 3.11 o posterior. Incluye el núcleo, esquemas, configuración ficticia, un producto de ejemplo y 14 pruebas existentes, sin dependencias externas de Python.

El 20 de octubre de 2026 aprobaron las 14 pruebas y `doctor` no detectó errores ni avisos en la demo. También se comprobaron resolución del proyecto, creación de puntos de control, guardado del traspaso y ejecución tras extraer el ZIP en otra carpeta.

La revisión de arquitectura del 21 de octubre fue estática. La demo muestra el núcleo; no reproduce mi registro operativo ni implica que los adaptadores externos descritos como futuras fases estén implementados.

Pablo Moraga · Dasein Futures
