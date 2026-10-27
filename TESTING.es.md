<p align="right"><a href="TESTING.md">English version</a></p>

# Pruebas y validación

Este apéndice separa **activos de prueba**, **ejecuciones registradas con fecha** y **validación operativa**. Un recuento de archivos describe el tamaño de la suite, no cobertura ni una ejecución aprobada. Los registros siguientes corresponden a versiones históricas; no se han vuelto a ejecutar las aplicaciones para preparar esta actualización documental.

## Comportamientos y fronteras

| Caso | Qué abordan las pruebas o comprobaciones | Límite de esa evidencia |
|---|---|---|
| [Registro Online](projects/online-registration.es.md) | Identidad y aislamiento de tenant, intentos de pago, acciones de reintento, OTP y contratos de handlers de cola | Los servicios mockeados no validan la pasarela, el SMS ni la activación FileMaker en producción |
| [AudioNow](projects/audionow.es.md) | Procesamiento de audio, resampling, clientes de proveedor y ciclo de sesiones | La rama principal y la de validación OpenAI difieren; las pruebas unitarias no acreditan calidad perceptual ni tráfico canary |
| [PrintFlow](projects/printflow.es.md) | Comprobaciones de entrega de generación, conciliación, kiosco e impresión; infraestructura de tests configurada | La cobertura automática seguía como trabajo de desarrollo; la extensión de vídeo offline tenía un checkpoint humano propio |
| [Beacon Presence](projects/ble-presence.es.md) | Transiciones de filtro/estado, agregación, harness local y escenarios E2E/carga configurados | La configuración de un escenario no es un resultado de carga ejecutada ni una medición de precisión física |
| [Realtime Translation](projects/realtime-translation.es.md) | Registry de proveedores, orquestación de sesiones, fronteras API y perfiles de voz con mocks | Las pruebas reales/perceptuales y funciones con acceso restringido tienen gates separados |
| [Schedule Builder](projects/schedule-builder.es.md) | Mapeo, normalización de fechas/texto, integración legacy con mocks y comprobaciones PDF | Un flujo PDF verificado no acredita paridad de cada campo de origen y variante de diseño |
| [TaskBoard](projects/taskboard.es.md) | Componentes, reglas de negocio y comportamiento de email con mocks | El email mockeado no prueba entrega a destinatarios reales ni activación de la migración de producción |
| [Floor Planner](projects/floor-planner.es.md) | Esta ficha documenta mentoría y el flujo de editor/importación implementado | No afirma una suite automática validada de forma independiente para la implementación del becario |

## Ejecuciones históricas seleccionadas

Son resúmenes de registros internos de proyecto, no resultados ejecutados ahora ni un paquete público de reproducción. Las fechas identifican la comprobación registrada; no garantizan que el servicio actual conserve el mismo estado.

| Caso y registro | Fecha | Resultado registrado | Alcance y comprobaciones pendientes |
|---|---|---|---|
| Registro Online, verificación de fase M3 | 29 de mayo de 2026 | 881 aprobadas, 2 omitidas, 1 fallida | Criterios de fase y correcciones documentados; deuda de tipado/tests y comprobaciones de integración real registradas por separado |
| Schedule Builder, verificación de remediación | 26 de mayo de 2026 | 58 pruebas aprobadas; typecheck registrado | También consta evidencia PDF de extremo a extremo; algunas comprobaciones de paridad de campos seguían pendientes |
| Realtime Translation, verificación de perfiles de voz | 28 de abril de 2026 | 296 pruebas aprobadas en la ejecución registrada | Perfiles/API probados con mocks; acceso restringido y comprobaciones perceptuales separados |

Los resúmenes posteriores pueden citar totales distintos. No se combinan ramas, hitos o fechas. Por ejemplo, una ejecución afirmada en un resumen no se atribuye a un verificador que indica expresamente que no ejecutó la suite.

## Escenarios para explicar en una entrevista

- **Reintentos de pago:** reutilizar la identidad del intento, validar propiedad y distinguir reintento de una orden nueva para el gateway. Las restricciones de base de datos, los tests de acciones con mocks y la pasarela real ofrecen garantías de tipos distintos.
- **Sesiones de audio:** cambios concurrentes de idioma, parada y reconexión pueden dejar clientes externos vivos. Los tests de ciclo de vida abordan propiedad y limpieza; el acceso al proveedor y la escucha abordan la salida real.
- **Presencia:** RSSI ruidoso, pasos breves junto a una puerta y periodos de gracia ejercitan una máquina de estados. Alcance físico, precisión y latencia de extremo a extremo necesitan un experimento con hardware medido.
- **Impresión:** los recursos locales preparados y los cambios de estado en cola abordan la pérdida de red. Una llamada de impresión satisfactoria no es un recibo físico de la impresora.
- **Exportación legacy:** registros válidos e inválidos, fallback CSV manual e inspección de un PDF real prueban fronteras distintas.

## Convenciones del inventario

Cuando una ficha incluye un recuento de implementación, pertenece a la versión y al perímetro indicados. Archivos, casos individuales, herramientas configuradas y comprobaciones ejecutadas son unidades distintas. Los archivos generados, dependencias y copias entre ramas no deben inflar un total combinado.

Los inventarios se acotan a una versión y método de recuento, sin combinar ramas incompatibles. El foco está en la invariante, el resultado registrado y su límite.

[Metodología](METHODOLOGY.es.md) · [Stack y contribución](STACK.es.md) · [Resumen](README.es.md)
