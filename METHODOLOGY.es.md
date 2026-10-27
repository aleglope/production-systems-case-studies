<p align="right"><a href="METHODOLOGY.md">English version</a></p>

# Metodología de ingeniería

Utilicé desarrollo asistido por IA junto con descubrimiento, notas de diseño, implementación acotada y revisión. Los proyectos combinaron planes por fases, especificaciones y registros de verificación de formas distintas; no todos siguieron un proceso uniforme.

Esta página explica las prácticas de trabajo que hay detrás de los casos. Los artefactos de planificación originales siguen siendo privados, por lo que el archivo público resume decisiones concretas en lugar de ofrecer una auditoría reproducible de cada registro interno.

## Empezar por el problema operativo

En [Registro Online](projects/online-registration.es.md) estudié el flujo existente antes de cambiar la plataforma web: sesiones de trabajo con el equipo interno, comportamiento legacy, propiedad de los datos y diferencia entre compradores individuales y grupales. Esas observaciones se convirtieron en requisitos y límites de entrega.

La restricción era la convivencia: los flujos web nuevos debían evolucionar mientras el sistema operativo heredado seguía en uso. De ahí surgieron identidades separadas, rutas de escritura controladas y una salida por etapas en lugar de una sustitución de golpe.

## Dividir la implementación en entregas acotadas

Utilicé planes de fase y notas de diseño para identificar dependencias, alternativas y criterios de aceptación. Los registros de verificación distinguían comprobaciones de código, pruebas automatizadas y checkpoints humanos u operativos.

Ejemplos de esa distinción:

| Caso | Decisión de planificación o verificación |
|---|---|
| [Registro Online](projects/online-registration.es.md) | Separar M1–M3 de los hitos posteriores y de las comprobaciones de activación de proveedores |
| [PrintFlow](projects/printflow.es.md) | Registrar feedback de campo tras la primera entrega y validar por separado extensiones como el vídeo offline |
| [Beacon Presence](projects/ble-presence.es.md) | Pasar de un MVP de software a un harness local antes de afirmar precisión con hardware real |
| [Realtime Translation](projects/realtime-translation.es.md) | Distinguir adaptador registrado, comprobaciones automáticas y prueba real con acceso al proveedor |
| [Schedule Builder](projects/schedule-builder.es.md) | Combinar pruebas de integración con mocks y una comprobación PDF de extremo a extremo documentada |

Un plan cerrado no prueba por sí solo un despliegue. Una corrección posterior también puede superar un gap inicial: la ficha debe reflejar la implementación fechada y su verificación, no un porcentaje de progreso aislado.

## Utilizar IA para trabajo de ingeniería acotado

Usé asistentes de programación, skills reutilizables y tareas paralelas para investigación, implementación y revisión. Las instrucciones de proyecto recogían convenciones y restricciones para que una sesión nueva pudiera trabajar con el mismo contexto.

Dos agentes de revisión especializados del trabajo de AudioNow abordaban:

- **Revisión de sesiones de traducción:** fugas de sesiones, operaciones concurrentes de arranque/parada y regresiones de audio en el puente LiveKit/proveedor.
- **Revisión de migraciones:** coherencia entre cambios Prisma/Supabase, esquema y políticas de acceso.

Estas herramientas apoyaban la revisión; no garantizaban corrección ni sustituían las comprobaciones de aceptación. La arquitectura, las decisiones de alcance y la verificación seguían bajo mi responsabilidad.

## Conectar las decisiones con sus consecuencias

El registro útil es el motivo de una elección y el comportamiento que permite:

- [AudioNow](projects/audionow.es.md): una réplica de API simplifica la propiedad de las sesiones, dejando el escalado horizontal fuera del alcance de esa versión.
- [PrintFlow](projects/printflow.es.md): un host de escritorio aporta impresión silenciosa, a cambio de empaquetado y configuración de dispositivos.
- [Registro Online](projects/online-registration.es.md): los handlers restringidos de la cola limitan la superficie de escritura legacy, mientras la activación sigue requiriendo comprobaciones operativas.

Los casos conservan esos compromisos. Se omiten totales agregados de planes, fases o instrucciones de agentes porque cada proyecto utilizó unidades y versiones distintas.

## Transferir el enfoque mediante mentoría

En [Floor Planner](projects/floor-planner.es.md) mi aportación fue orientación, arquitectura inicial y revisión técnica. El becario implementó la aplicación. La ficha explica ese papel por separado de la autoría de la implementación.

[Pruebas y validación](TESTING.es.md) · [Stack y contribución](STACK.es.md) · [Resumen](README.es.md)
