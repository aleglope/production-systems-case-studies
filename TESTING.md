# Testing y calidad

Enfoque de pruebas a lo largo del ecosistema, con **datos reales** (conteo de archivos de test por proyecto, excluyendo dependencias). No es una afirmación genérica de "tiene tests": es el inventario verificado.

## Resumen

**~314 archivos de test** repartidos así:

| Proyecto | Archivos de test | Framework(s) | Tipos de prueba |
|---|---:|---|---|
| **[Inscripción Online](projects/inscripcion-online.md)** | **127** | Vitest · Testing Library | Invariantes de datos, Server Actions de ambos flujos, cola FileMaker, OTP, regresiones de seguridad (CSRF/XSS) |
| **[Congress Translation](projects/congress-translation.md)** | **86** | Jest · Supertest | Unit + integración de API, proveedores de traducción |
| **[AudioNow](projects/audionow.md)** | **38** | Vitest · Testing Library | Pipeline de audio, *soft-limiter*, sesiones de traducción |
| **[Beacon Attendance](projects/beacon-attendance.md)** | **32** | Jest · Playwright · Artillery | Unit + **E2E** + **carga** (hasta 200 rps) |
| **[LogiTasks](projects/logitasks.md)** | **24** | Vitest · Testing Library | Componentes, votación, notificaciones |
| **[Programa-Web](projects/programa-web.md)** | **7** (57 casos) | Vitest · Testing Library | Lógica + *mocks* de FileMaker |
| **[BadgeFlow](projects/badgeflow.md)** | infra configurada | Jest · Supertest | Infraestructura lista; cobertura automatizada como deuda post-evento |
| **[Sala de Cenas](projects/sala-cenas.md)** | — | — | Proyecto de mentoría/aprendizaje |

> **Honestidad:** BadgeFlow salió a producción contra la fecha fija de un congreso real; tiene la infraestructura de test (Jest + Supertest) configurada pero priorizó el evento, dejando la cobertura automatizada como deuda consciente. Sala de Cenas era el vehículo de aprendizaje de un becario. El resto del ecosistema sí tiene cobertura sustancial.

## Detalle por proyecto

### Inscripción Online — 127 archivos · 881 tests
La suite cubre los **invariantes que importan** en un sistema de pagos:
- Unicidad de `Persona` por asociación, idempotencia de `Pago` (mismo `id_intento` no duplica fila), máquina de estados de `Inscripción`.
- **Anti-suplantación**: no se exponen datos personales sin un OTP exitoso.
- *Server Actions* de los flujos individual y grupal, *handlers* de la cola `fm_write_queue`, mensajería OTP.
- Regresiones de seguridad (CSRF/XSS).

### Beacon Attendance — 32 archivos · unit + E2E + carga
El proyecto con la pirámide de test más completa:
- **Unit** (Jest): suites exhaustivas — p. ej. 47 casos en el detector de zonas (transiciones de estado, histéresis), 47 en el agregador de presencia (puntos, bonus), 18 en el filtro de Kalman.
- **E2E** (Playwright).
- **Carga** (Artillery): escenarios hasta 200 rps con fases *warm-up → ramp-up → sustained → peak*.
- Todo orquestado en **CI/CD** (GitHub Actions: lint, typecheck, unit, E2E, carga, `cdk synth`).

### Congress Translation — 86 archivos
Unit + integración de la API NestJS (Supertest), cubriendo el *registry* de proveedores y la orquestación de sesiones de traducción.

### AudioNow — 38 archivos
Foco en el *pipeline* de audio: limitador *soft-knee*, *resampling*, ciclo de vida de las sesiones de traducción y el *bridge* con LiveKit. Incluye los `*.spec.ts` del módulo `openai-realtime` (en la rama canary).

### LogiTasks — 24 · Programa-Web — 7 (57 casos)
Cobertura de componentes y lógica de negocio; en Programa-Web, con *mocks* de la FileMaker Data API para probar la integración sin tocar el sistema real.

## Frameworks y herramientas

`Vitest` · `Jest` · `ts-jest` · `Supertest` · `Playwright (E2E)` · `Artillery (carga)` · `@testing-library/react` · `@testing-library/user-event` · `jsdom` · `GitHub Actions (CI/CD)`
