# Operator Harness

**Código abierto (OSS).**

**Una herramienta que desarrollé y uso para mantener la coherencia del trabajo con IA entre distintos proyectos.**

Trabajar en varios productos con agentes de programación plantea un problema práctico: cada sesión necesita el proyecto, la identidad, las referencias de cuentas, las instrucciones y el objetivo correctos.

El Harness hace explícitas esas relaciones y permite mantener la continuidad entre sesiones.

## Flujo de trabajo

`Elegir proyecto → resolver contexto y controles → trabajar → guardar un punto de control → revisar el traspaso`

- Resolver un proyecto a partir de su identificador o directorio.
- Cargar su identidad, perfil de trabajo, fuentes relevantes y controles de calidad.
- Detectar diferencias en la configuración y las instrucciones.
- Guardar el trabajo completado y la próxima acción en un punto de control local.
- Previsualizar el traspaso a la siguiente sesión.

## Implementación

El núcleo es una CLI en Python sin dependencias externas. Registros JSON describen proyectos, perfiles, identidades y referencias de cuentas. Los archivos locales de puntos de control y traspaso conservan el estado de las sesiones.

El sistema incluye validación de esquemas, detección de conflictos entre límites de proyectos, generación de instrucciones con protección contra sobrescritura y pruebas de configuración, estado y comportamiento del entorno de trabajo.

## Alcance

El Harness proporciona contexto y controles deterministas para los agentes de IA. No entrena un modelo ni ejecuta de forma autónoma el trabajo de todos los proyectos registrados.

## Demo para revisión

Una copia independiente utiliza un producto ficticio y registros de cuentas vacíos. Demuestra la resolución de proyectos y la continuidad local entre sesiones sin incluir mi registro operativo, documentos de clientes, credenciales ni traspasos reales.

**[Descargar la demo ejecutable](../downloads/operator-harness-demo.zip).** Requiere Python 3.11 o posterior, sin cuentas externas ni dependencias de Python. El paquete incluye el código, la configuración de ejemplo y 14 pruebas existentes.

El 20 de octubre de 2026 aprobaron las 14 pruebas. La comprobación de estado de la demo no detectó errores ni avisos; también se verificaron la resolución del proyecto, la creación de puntos de control y el guardado local del traspaso.

Utilizo el sistema personal en mi propio trabajo; la demo es un ejemplo reproducible de su funcionamiento central.

Pablo Moraga · Dasein Futures
