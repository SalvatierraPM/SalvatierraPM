# Revenue PRO

**Código privado.** Se presenta como caso descriptivo, sin publicar el código del producto.

**De una planilla de ingresos a una aplicación de operación hotelera.**

Revenue PRO lleva un proceso basado en planillas a una aplicación web para estimar ingresos adicionales de un hotel, registrar ventas y producir informes. El trabajo técnico conecta reglas de negocio, interfaz, datos persistentes y controles de acceso.

El repositorio es privado. Este caso describe la implementación sin publicar registros de clientes, credenciales ni código privado.

## Flujo de trabajo

1. Configurar un hotel, sus servicios y temporadas.
2. Simular ingresos potenciales según ocupación, precios y supuestos de contratación de servicios.
3. Registrar ventas reales para el servicio y la fecha correspondientes.
4. Comparar los ingresos registrados con la simulación.
5. Exportar informes en PDF o Excel.

La aplicación también incluye invitaciones al equipo, recuperación de cuentas, administración de hoteles y controles del estado de suscripción.

## Arquitectura

| Capa | Implementación |
| --- | --- |
| Interfaz | Next.js, React y TypeScript; panel, simulador, registro de ventas, informes y pantallas de equipo. |
| Servicios de aplicación | Rutas de servidor para informes, operaciones de equipo y acciones administrativas. |
| Persistencia | PostgreSQL mediante Supabase; migraciones SQL versionadas. |
| Acceso | Autenticación, membresía por hotel, políticas de seguridad por fila y comprobaciones administrativas en el servidor. |
| Salidas | Generación de Excel y PDF. |
| Verificación | Pruebas de reglas de negocio con Vitest, lint, comprobación de tipos y compilación de producción en GitHub Actions. |

## Diseño de base de datos

El esquema separa la configuración del hotel del historial de ventas:

- `hotels`, `hotel_members` y `subscriptions` representan el contexto del hotel y sus accesos.
- `hotel_services`, `season_periods` y `service_season_prices` guardan los parámetros configurables del negocio.
- `transactions` registra ventas; `transaction_audit` registra sus cambios.
- Las claves foráneas, restricciones de unicidad, comprobaciones numéricas e índices de fechas expresan reglas tanto en la base de datos como en la aplicación.

Las políticas por fila limitan el acceso a los datos según la membresía del hotel. Las políticas restrictivas también consideran el estado de suscripción. Un disparador de base de datos aplica el límite de miembros y otro registra los cambios en las transacciones para su auditoría.

Son controles implementados en el repositorio. Revisar el código no demuestra que todos estén correctamente configurados en un entorno desplegado.

## Decisiones relevantes

**Conservar los precios históricos.** Las pruebas cubren que una venta mantenga su precio registrado cuando cambia la configuración actual.

**Respetar el calendario.** Las pruebas cubren años bisiestos, límites de temporadas y meses que abarcan varias temporadas.

**Hacer explícita la moneda.** Las pruebas cubren la representación y conversión de CLP/USD sin alterar el valor económico subyacente.

**Distinguir persistencia de demo y operación alojada.** Sin la configuración del servicio alojado, la aplicación utiliza un modo de demostración local. Ese modo no demuestra aislamiento de base de datos ni entrega de correos.

## Evidencia y estado

La última ejecución revisada del flujo `Verify` aprobó el **20 de julio de 2026**, para el commit `b26a16a17f955a2d2bc26265619be9030a621b36`. Sus comprobaciones ejecutan lint, validación de TypeScript, pruebas unitarias y compilación.

Los permisos entre hoteles, las invitaciones, los correos de recuperación y la configuración de producción aún requieren verificación en el entorno conectado previsto. Este caso no afirma que existan clientes pagadores, aumentos de ingresos ni un lanzamiento comercial completado.

## Qué demuestra

La transformación de un modelo de negocio en una aplicación funcional, con una interfaz coherente, un modelo de datos relacional, operaciones de servidor, exportaciones y comprobaciones repetibles.

Pablo Moraga · Dasein Futures
