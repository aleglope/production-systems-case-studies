<p align="right"><a href="TESTING.md">🇬🇧 English version</a></p>

# Testing y calidad

Enfoque de pruebas a lo largo del ecosistema, con **datos reales** (conteo de archivos de test por proyecto, excluyendo dependencias). No es una afirmación genérica de "tiene tests": es el inventario verificado.

## Resumen

**~314 archivos de test** repartidos así:

| Proyecto | Archivos de test | Framework(s) | Tipos de prueba |
|---|---:|---|---|
| **[Registro Online](projects/online-registration.es.md)** | **127** | Vitest · Testing Library | Invariantes de datos, Server Actions de ambos flujos, cola FileMaker, OTP, regresiones de seguridad (CSRF/XSS) |
| **[Realtime Translation](projects/realtime-translation.es.md)** | **86** | Jest · Supertest | Unit + integración de API, proveedores de traducción |
| **[AudioNow](projects/audionow.es.md)** | **38** | Vitest · Testing Library | Pipeline de audio, *soft-limiter*, sesiones de traducción |
| **[Beacon Presence](projects/ble-presence.es.md)** | **32** | Jest · Playwright · Artillery | Unit + **E2E** + **carga** (hasta 200 rps) |
| **[TaskBoard](projects/taskboard.es.md)** | **24** | Vitest · Testing Library | Componentes, votación, notificaciones |
| **[Schedule Builder](projects/schedule-builder.es.md)** | **7** (57 casos) | Vitest · Testing Library | Lógica + *mocks* de FileMaker |
| **[PrintFlow](projects/printflow.es.md)** | infra configurada | Jest · Supertest | Infraestructura lista; cobertura automatizada como deuda posterior al despliegue |
| **[Floor Planner](projects/floor-planner.es.md)** | — | — | Proyecto de mentoría/aprendizaje |

> **Honestidad:** PrintFlow salió a producción contra una fecha de salida fija e inamovible; tiene la infraestructura de test (Jest + Supertest) configurada pero priorizó la entrega, dejando la cobertura automatizada como deuda consciente. Floor Planner era el vehículo de aprendizaje de un becario. El resto del ecosistema sí tiene cobertura sustancial.

## Detalle por proyecto

### Registro Online — 127 archivos · 881 tests
La suite cubre los **invariantes que importan** en un sistema de pagos:
- Unicidad de `Persona` por asociación, idempotencia de `Pago` (mismo `id_intento` no duplica fila), máquina de estados de `Inscripción`.
- **Anti-suplantación**: no se exponen datos personales sin un OTP exitoso.
- *Server Actions* de los flujos individual y grupal, *handlers* de la cola `fm_write_queue`, mensajería OTP.
- Regresiones de seguridad (CSRF/XSS).

### Beacon Presence — 32 archivos · unit + E2E + carga
El proyecto con la pirámide de test más completa:
- **Unit** (Jest): suites exhaustivas — p. ej. 47 casos en el detector de zonas (transiciones de estado, histéresis), 47 en el agregador de presencia (puntos, bonus), 18 en el filtro de Kalman.
- **E2E** (Playwright).
- **Carga** (Artillery): escenarios hasta 200 rps con fases *warm-up → ramp-up → sustained → peak*.
- Todo orquestado en **CI/CD** (GitHub Actions: lint, typecheck, unit, E2E, carga, `cdk synth`).

### Realtime Translation — 86 archivos
Unit + integración de la API NestJS (Supertest), cubriendo el *registry* de proveedores y la orquestación de sesiones de traducción.

### AudioNow — 38 archivos
Foco en el *pipeline* de audio: limitador *soft-knee*, *resampling*, ciclo de vida de las sesiones de traducción y el *bridge* con LiveKit. Incluye los `*.spec.ts` del módulo `openai-realtime` (en la rama canary).

### TaskBoard — 24 · Schedule Builder — 7 (57 casos)
Cobertura de componentes y lógica de negocio; en Schedule Builder, con *mocks* de la FileMaker Data API para probar la integración sin tocar el sistema real.

## Frameworks y herramientas

`Vitest` · `Jest` · `ts-jest` · `Supertest` · `Playwright (E2E)` · `Artillery (carga)` · `@testing-library/react` · `@testing-library/user-event` · `jsdom` · `GitHub Actions (CI/CD)`