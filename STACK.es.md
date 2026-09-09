<p align="right"><a href="STACK.md">🇬🇧 English version</a></p>

# Stack y competencias técnicas

Competencias demostradas a lo largo del ecosistema, con el **proyecto que las evidencia**. No es una lista de tecnologías "vistas una vez": cada entrada está respaldada por un sistema en producción o un PoC funcional.

---

## Frontend

| Competencia | Evidencia |
|---|---|
| **Next.js App Router** (v14, v15, v16) | Todos los proyectos web. Manejo de *breaking changes* de Next 16 (`proxy.ts` en lugar de `middleware.ts`) documentado en Registro Online y TaskBoard |
| **React 18 / 19** (Server Components + Server Actions) | Registro Online, PrintFlow, TaskBoard |
| **3D en web** — React Three Fiber, drei, Rapier (física), Three.js, leva | Kiosco 3D con física de *lanyard* (PrintFlow); editor de salas 3D (Floor Planner); portfolio (three-js-portfolio) |
| **Canvas 2D** — Konva / react-konva | Plano interactivo de mesas (Floor Planner) |
| **PWA / offline-first** — Serwist, Service Workers, IndexedDB | PrintFlow (kiosco sin red), Beacon Presence (PWA de usuario) |
| **UI** — Tailwind CSS 4, shadcn/ui, Radix, Ant Design, Chakra UI | Transversal |
| **i18n** — next-intl, 6 locales con traducción LLM multi-proveedor | Registro Online |
| **Estado de servidor** — TanStack Query (mutaciones optimistas) | TaskBoard |

---

## Backend

| Competencia | Evidencia |
|---|---|
| **NestJS** (v10, v11) — REST, WebSocket, SSE, GraphQL, guards, cron | PrintFlow (41 *endpoints*), AudioNow, Realtime Translation, Beacon Presence |
| **Next.js Server Actions** como capa de backend | Registro Online (56 *actions*), TaskBoard |
| **Renderizado servidor** — Puppeteer (Chrome headless), generación PNG/PDF a escala 3× | PrintFlow |
| **Generación de documentos** — jsPDF, ExcelJS | Registro Online, Schedule Builder |
| **Procesos largos / workers** — worker externo en Docker, polling de cola | Floor Planner (importador de planos), Registro Online (Vercel Cron) |

---

## Datos

| Competencia | Evidencia |
|---|---|
| **PostgreSQL** — diseño relacional, *single-table design*, índices parciales, *constraints* | Transversal |
| **Supabase** — RLS, Realtime, Auth, Storage, RPC `SECURITY DEFINER`, triggers | AudioNow (20 tablas, 77 funciones/triggers), TaskBoard, Floor Planner |
| **Drizzle ORM** | Registro Online (31 tablas) |
| **Prisma ORM** (v5, v6) | PrintFlow, AudioNow, Realtime Translation |
| **DynamoDB** — *single-table* con GSIs, TTL | Beacon Presence |
| **Redis** — Upstash / ElastiCache: cache, rate limit, pub/sub, *single-flight token cache* | Registro Online, Schedule Builder, Beacon Presence |
| **Migraciones** — versionadas, con *gates* destructivos por flag | Registro Online (31 migraciones), AudioNow (76) |

---

## Tiempo real y streaming

| Competencia | Evidencia |
|---|---|
| **LiveKit** (WebRTC SFU) — `@livekit/rtc-node`, *bot* server-side, DataChannel | AudioNow, Realtime Translation |
| **Procesamiento de audio** — *resampling* PCM, soft-knee limiter (tanh), chunk smoothing | AudioNow |
| **Supabase Realtime** — suscripciones a cambios de tabla | TaskBoard, Floor Planner |
| **Pipelines IoT** — MQTT/TLS → AWS IoT Core → Kinesis → Lambda, latencia <500 ms | Beacon Presence |

---

## Integraciones de IA

| Competencia | Evidencia |
|---|---|
| **Traducción *speech-to-speech*** — Palabra.ai, Azure Live Interpreter v2, OpenAI Realtime API, Google Gemini Live, Grok | AudioNow (producción), Realtime Translation (7 proveedores conmutables) |
| **Visión + OCR** — GPT-4.1 para importación de planos, con OpenCV / Tesseract / PaddleOCR de respaldo | Floor Planner |
| **Traducción de texto LLM** — cadena multi-proveedor con *fallback* (OpenAI → Google → Anthropic) | Registro Online (i18n) |
| **Patrones de robustez LLM** — *watchdog timeouts*, anti-alucinación, renovación proactiva de sesión, *voice cloning* zero-shot | Realtime Translation |

---

## Algoritmos y sistemas

| Competencia | Evidencia |
|---|---|
| **Filtrado de señal** — filtro de Kalman para suavizar RSSI (-27 % ruido) | Beacon Presence |
| **Máquinas de estados** — detección de presencia con histéresis (4 estados, umbrales -70/-80 dBm) | Beacon Presence |
| **Idempotencia** — reintentos de pago con `id_intento`, *find-or-create* en cola FileMaker | Registro Online |
| **Concurrencia** — *singleton* de navegador con recuperación, mutex anti-zombie en sesiones de traducción | PrintFlow, AudioNow |

---

## Infraestructura y DevOps

| Competencia | Evidencia |
|---|---|
| **Vercel** — despliegue de Next.js, Cron, *environment variables* | 8 proyectos desplegados |
| **Railway** — backend NestJS en Docker, PostgreSQL gestionado | PrintFlow, AudioNow |
| **AWS CDK** (IaC) — VPC, DynamoDB, ElastiCache, SQS, Lambda, ECS Fargate, Cognito, WAF | Beacon Presence |
| **Docker** — *builds* multi-stage con Chromium, workers como contenedor | PrintFlow, Floor Planner |
| **CI/CD** — GitHub Actions (lint, typecheck, test, E2E Playwright, carga Artillery, CDK synth) | Beacon Presence, varios |
| **App de escritorio** — instalador Windows con GitHub Actions (impresión silenciosa) | PrintFlow |

---

## Pagos, seguridad y cumplimiento

| Competencia | Evidencia |
|---|---|
| **TPV Redsys** — firma HMAC-SHA256, webhook server-to-server, idempotencia | Registro Online |
| **Autenticación** — `iron-session`, OTP passwordless (Twilio Verify / Resend), bcrypt + pepper, sesión dual | Registro Online |
| **Autorización** — RLS, RPC `SECURITY DEFINER` + trigger `BEFORE UPDATE`, jerarquía de roles 3-tier | AudioNow, TaskBoard |
| **Rate limiting / anti-abuso** — Upstash, *circuit breaker*, validación de *magic bytes* en uploads | Registro Online, PrintFlow, Beacon Presence |
| **Privacidad** — reglas anti-suplantación, fences de datos (no exponer NIF), `audit_log` | Registro Online |

---

## Metodología

| Competencia | Evidencia |
|---|---|
| **Desarrollo *AI-augmented*** — Claude Code con planificación por fases (GSD) | Transversal (`.planning/` en todos los repos) |
| **Verificación goal-backward** — `VERIFICATION.md` por fase | Registro Online, PrintFlow, AudioNow, Realtime Translation |
| **TDD / tests** — Vitest, Jest, Testing Library; 881 tests (Inscripción), 366+ archivos (Beacon) | Registro Online, Beacon Presence |
| **Documentación técnica** — specs, ADRs informales, diagramas Mermaid | Transversal |
| **Mentoría** — formación de un becario en IA y librerías 3D | Floor Planner |