# Moltbook Observatory

**Código abierto (OSS).**

**De datos dispersos de una plataforma a un observatorio de investigación que se puede explorar y auditar.**

Moltbook Observatory conecta recolección de publicaciones y comentarios, procesamiento de lenguaje, análisis de interacciones y presentación web. El resultado reúne código de procesamiento, datos derivados, informes y una interfaz para examinar los resultados y su metodología.

[Repositorio público](https://github.com/SalvatierraPM/moltbook) · [Sitio del observatorio](https://analisis-moltbook.netlify.app)

## Flujo de trabajo

`Recolección → normalización → señales y representaciones semánticas → análisis de redes y cambios temporales → informes e interfaz web`

1. Recopilar datos públicos mediante API o, como alternativa, HTML.
2. Normalizar publicaciones, comentarios, autores y relaciones.
3. Derivar señales de lenguaje, difusión e interacción.
4. Explorar patrones entre comunidades y períodos.
5. Consultar resultados junto con sus fuentes, procedimientos y límites.

## Enfoque técnico

| Parte | Implementación revisada |
| --- | --- |
| Recolección y procesamiento | Paquetes y CLI en Python, scripts por etapa y archivos de datos intermedios. |
| Análisis de lenguaje | Módulos de señales lingüísticas, ontología y pragmática. |
| Representaciones semánticas | Backends intercambiables: TF-IDF, Sentence Transformers y un adaptador opcional para embeddings de Google. |
| Redes y tiempo | Extracción de relaciones, métricas de difusión, ventanas temporales y comparación de comunidades. |
| Evaluación | Muestreo estratificado para anotación humana y cálculo de métricas frente a esas etiquetas. |
| Presentación | Interfaz web de observatorio, exploración interactiva y metodología/auditoría. |

## Decisiones de ingeniería

**Conservar las etapas del procesamiento.** Los datos originales, normalizados y derivados permiten inspeccionar cómo se llegó a una salida.

**Separar representaciones y análisis.** La interfaz de embeddings permite comparar alternativas locales o alojadas sin confundir el proveedor con el resto del proceso. El adaptador alojado incorpora procesamiento por lotes y reintentos.

**Preparar la evaluación humana.** El código incluye generación de muestras y evaluación. Su existencia no significa que las anotaciones ya estén completadas ni que los indicadores estén validados.

**Presentar resultados con contexto.** El sitio distingue la visión general, la exploración y el material metodológico y de auditoría.

## Evidencia y límites

Este caso se apoya en el repositorio público y en la revisión estática de los módulos locales de procesamiento, embeddings y evaluación. La copia local puede contener cambios que aún no estén publicados.

La nota local de revisión humana del 26 de febrero de 2026 registra anotaciones pendientes y uso de un baseline offline. No se presenta ese baseline como un modelo validado. La selección de backend es configurable: no se afirma que todas las alternativas se hayan utilizado en cada informe.

No se volvió a ejecutar la recolección, el procesamiento completo ni las llamadas a proveedores durante esta revisión del portfolio. El acceso actual al sitio y la ejecución completa del pipeline requieren una comprobación independiente. Los patrones observacionales no demuestran causalidad ni conciencia de los agentes.

## Qué demuestra

Convertir una pregunta de investigación en un sistema de datos con procesamiento, integración de modelos, análisis, interfaz y trazabilidad. Complementa los productos operativos del portfolio con profundidad en lenguaje y datos.

Pablo Moraga · Dasein Futures
