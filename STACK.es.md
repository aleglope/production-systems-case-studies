<p align="right"><a href="STACK.md">English version</a></p>

# Stack y contribución

Tecnologías y prácticas enlazadas con el caso y la aportación que las respaldan. El estado de entrega y validación pertenece a cada ficha; las tecnologías del proyecto de mentoría no se atribuyen como implementación individual. Se mantienen las versiones históricas cuando explican una decisión.

## Aplicaciones web

| Tecnología o práctica | Caso y contribución |
|---|---|
| **Next.js App Router · React** | [Registro Online](projects/online-registration.es.md) — Flujos individual/grupal, acciones de servidor y recorridos web por tenant |
| **React Three Fiber · Rapier** | [PrintFlow](projects/printflow.es.md) — Implementación de un kiosco 3D configurable junto al flujo de impresión |
| **Three.js · vistas 2D** | [Floor Planner](projects/floor-planner.es.md) — Mentoría del proyecto de editor; la implementación corresponde al becario |
| **Serwist · IndexedDB** | [PrintFlow](projects/printflow.es.md) — Recursos locales preparados y replay de cambios de estado de impresión en cola |
| **next-intl · pipeline de traducción** | [Registro Online](projects/online-registration.es.md) — Seis catálogos de idioma y fallbacks estructurados; revisión lingüística diferenciada de paridad de claves |
| **TanStack Query · Supabase Realtime** | [TaskBoard](projects/taskboard.es.md) — Estado cliente y actualizaciones de peticiones/votos en una herramienta interna |

## Backend e integración

| Tecnología o práctica | Caso y contribución |
|---|---|
| **NestJS · LiveKit** | [AudioNow](projects/audionow.es.md) — Clientes de traducción en servidor, pistas compartidas y propiedad de sesiones |
| **Next.js Server Actions · Drizzle** | [Registro Online](projects/online-registration.es.md) — Identidades de compra, acciones de pago y comprobaciones relacionales de propiedad |
| **Puppeteer · HTML a PNG/PDF** | [PrintFlow](projects/printflow.es.md) — Generación con resolución configurable, concurrencia acotada y recuperación del navegador |
| **FileMaker Data API** | [Schedule Builder](projects/schedule-builder.es.md) — Wrapper de aplicación de lectura, mapeo de registros y fallback CSV manual |
| **Handlers de cola controlados** | [Registro Online](projects/online-registration.es.md) — Escrituras legacy diferidas con operaciones permitidas y fronteras de parámetros |
| **Tesseract.js · Jimp · texto PDF** | [Floor Planner](projects/floor-planner.es.md) — Orientación técnica del flujo de importación localizado; OCR en ruta/proceso Next.js |

## Datos y control de acceso

| Tecnología o práctica | Caso y contribución |
|---|---|
| **PostgreSQL · Drizzle** | [Registro Online](projects/online-registration.es.md) — Modelo relacional, restricciones, índices y migraciones SQL versionadas |
| **Supabase RLS · RPCs · triggers** | [AudioNow](projects/audionow.es.md) — Permisos de streaming en tres niveles y rutas controladas de cambio de estado |
| **Prisma · PostgreSQL** | [PrintFlow](projects/printflow.es.md) — Persistencia de credenciales/diseños y conciliación entre fuentes |
| **DynamoDB · GSIs · TTL** | [Beacon Presence](projects/ble-presence.es.md) — Modelo de estado del pipeline de presencia de software |
| **Redis · caché de token single-flight** | [Schedule Builder](projects/schedule-builder.es.md) — Token de sesión FileMaker y lock compartidos; diferenciados de la caché de datos del programa |
| **Supabase Realtime** | [TaskBoard](projects/taskboard.es.md) — Suscripciones sobre peticiones y notificaciones in-app persistidas |

## Medios en tiempo real e IA

| Tecnología o práctica | Caso y contribución |
|---|---|
| **WebRTC SFU · bots en servidor** | [AudioNow](projects/audionow.es.md) — Una pista traducida distribuida a oyentes; sesiones organizadas por sala/idioma |
| **PCM · limitador · resampling** | [AudioNow](projects/audionow.es.md) — Compresión de picos, suavizado de chunks y adaptación de sample rate según rama |
| **Registry de proveedores de voz** | [Realtime Translation](projects/realtime-translation.es.md) — Siete adaptadores registrados tras un contrato; validación real distinta por adaptador |
| **Watchdogs · playout adaptativo** | [Realtime Translation](projects/realtime-translation.es.md) — Robustez de sesiones y control de profundidad de cola; observabilidad acotada en la evolución de la PoC |

## Algoritmos e infraestructura

| Tecnología o práctica | Caso y contribución |
|---|---|
| **Filtro Kalman · histéresis** | [Beacon Presence](projects/ble-presence.es.md) — Filtrado RSSI y transiciones de presencia; calibración física como hito separado |
| **AWS IoT · Lambda · SQS** | [Beacon Presence](projects/ble-presence.es.md) — Cuatro etapas con fronteras de cola; Kinesis/S3 como ramas paralelas de ingestión |
| **AWS CDK** | [Beacon Presence](projects/ble-presence.es.md) — Infraestructura como código del MVP; no implica infraestructura cloud activa actualmente |
| **Docker · Chromium · Railway** | [PrintFlow](projects/printflow.es.md) — Despliegue backend con renderizado headless y memoria limitada |
| **Vercel · Railway · Supabase** | [AudioNow](projects/audionow.es.md) — Servicios separados de web, API y datos; una réplica de API en la versión descrita |
| **Electron · empaquetado Windows** | [PrintFlow](projects/printflow.es.md) — Puente de escritorio, solicitudes de impresión silenciosa y distribución portable/NSIS |

## Pagos, privacidad y colaboración

| Tecnología o práctica | Caso y contribución |
|---|---|
| **Redsys · identidad de intento** | [Registro Online](projects/online-registration.es.md) — Firma de pasarela, webhook, propiedad del reintento y reutilización del intento de pago |
| **OTP · iron-session · bcrypt** | [Registro Online](projects/online-registration.es.md) — Identidades distintas para asistentes individuales y compradores grupales autenticados |
| **Fronteras de datos · auditoría** | [Registro Online](projects/online-registration.es.md) — Restricciones por rol/tenant y requisitos de privacidad explícitos; no certificación de cumplimiento legal |
| **Notificaciones · Resend** | [TaskBoard](projects/taskboard.es.md) — Persistencia in-app seguida de intento de email con errores aislados; alcance de activación fechado en la ficha |
| **Mentoría · revisión técnica** | [Floor Planner](projects/floor-planner.es.md) — Arquitectura inicial, orientación y revisión; código implementado por el becario |

## Práctica de ingeniería

Las fichas conectan estas herramientas con restricciones y alternativas. La [metodología](METHODOLOGY.es.md) explica descubrimiento, planificación, revisión y asistencia de IA; [pruebas y validación](TESTING.es.md) separa inventario, ejecuciones históricas y comprobaciones operativas.

[Volver al resumen](README.es.md)
