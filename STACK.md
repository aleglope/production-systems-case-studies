<p align="right"><a href="STACK.es.md">🇪🇸 Versión en español</a></p>

# Stack & technical skills

Skills demonstrated across the ecosystem, each with the **project that evidences it**. This is not a list of technologies "touched once": every entry is backed by a production system or a working PoC.

---

## Frontend

| Skill | Evidence |
|---|---|
| **Next.js App Router** (v14, v15, v16) | Every web project. Handling Next 16 breaking changes (`proxy.ts` replacing `middleware.ts`) documented in Online Registration and TaskBoard |
| **React 18 / 19** (Server Components + Server Actions) | Online Registration, PrintFlow, TaskBoard |
| **3D on the web** — React Three Fiber, drei, Rapier (physics), Three.js, leva | 3D kiosk with lanyard physics (PrintFlow); 3D room editor (Floor Planner); portfolio (three-js-portfolio) |
| **2D canvas** — Konva / react-konva | Interactive table floor plan (Floor Planner) |
| **PWA / offline-first** — Serwist, Service Workers, IndexedDB | PrintFlow (kiosk with no network), Beacon Presence (end-user PWA) |
| **UI** — Tailwind CSS 4, shadcn/ui, Radix, Ant Design, Chakra UI | Cross-cutting |
| **i18n** — next-intl, 6 locales with LLM multi-provider translation | Online Registration |
| **Server state** — TanStack Query (optimistic mutations) | TaskBoard |

---

## Backend

| Skill | Evidence |
|---|---|
| **NestJS** (v10, v11) — REST, WebSocket, SSE, GraphQL, guards, cron | PrintFlow (41 endpoints), AudioNow, Realtime Translation, Beacon Presence |
| **Next.js Server Actions** as the backend layer | Online Registration (56 actions), TaskBoard |
| **Server-side rendering to media** — Puppeteer (headless Chrome), PNG/PDF generation at 3× scale | PrintFlow |
| **Document generation** — jsPDF, ExcelJS | Online Registration, Schedule Builder |
| **Long-running jobs / workers** — external Docker worker, queue polling | Floor Planner (floor-plan importer), Online Registration (Vercel Cron) |

---

## Data

| Skill | Evidence |
|---|---|
| **PostgreSQL** — relational design, single-table design, partial indexes, constraints | Cross-cutting |
| **Supabase** — RLS, Realtime, Auth, Storage, `SECURITY DEFINER` RPCs, triggers | AudioNow (20 tables, 77 functions/triggers), TaskBoard, Floor Planner |
| **Drizzle ORM** | Online Registration (31 tables) |
| **Prisma ORM** (v5, v6) | PrintFlow, AudioNow, Realtime Translation |
| **DynamoDB** — single-table with GSIs, TTL | Beacon Presence |
| **Redis** — Upstash / ElastiCache: cache, rate limiting, pub/sub, single-flight token cache | Online Registration, Schedule Builder, Beacon Presence |
| **Migrations** — versioned, with destructive-change feature-flag gates | Online Registration (31 migrations), AudioNow (76) |

---

## Real-time & streaming

| Skill | Evidence |
|---|---|
| **LiveKit** (WebRTC SFU) — `@livekit/rtc-node`, server-side bots, DataChannel | AudioNow, Realtime Translation |
| **Audio processing** — PCM resampling, soft-knee limiter (tanh), chunk smoothing | AudioNow |
| **Supabase Realtime** — table-change subscriptions | TaskBoard, Floor Planner |
| **IoT pipelines** — MQTT/TLS → AWS IoT Core → Kinesis → Lambda, <500 ms latency | Beacon Presence |

---

## AI integrations

| Skill | Evidence |
|---|---|
| **Speech-to-speech translation** — Palabra.ai, Azure Live Interpreter v2, OpenAI Realtime API, Google Gemini Live, Grok | AudioNow (production), Realtime Translation (7 switchable providers) |
| **Vision + OCR** — GPT-4.1 for floor-plan import, with OpenCV / Tesseract / PaddleOCR fallback | Floor Planner |
| **LLM text translation** — multi-provider chain with fallback (OpenAI → Google → Anthropic) | Online Registration (i18n) |
| **LLM robustness patterns** — watchdog timeouts, anti-hallucination, proactive session renewal, zero-shot voice cloning | Realtime Translation |

---

## Algorithms & systems

| Skill | Evidence |
|---|---|
| **Signal filtering** — Kalman filter for RSSI smoothing (-27% noise) | Beacon Presence |
| **State machines** — presence detection with hysteresis (4 states, -70/-80 dBm thresholds) | Beacon Presence |
| **Idempotency** — payment retries via `id_intento`, find-or-create in the FileMaker queue | Online Registration |
| **Concurrency** — browser singleton with recovery, anti-zombie mutex on translation sessions | PrintFlow, AudioNow |

---

## Infrastructure & DevOps

| Skill | Evidence |
|---|---|
| **Vercel** — Next.js deployments, Cron, environment management | 8 projects deployed |
| **Railway** — NestJS backend in Docker, managed PostgreSQL | PrintFlow, AudioNow |
| **AWS CDK** (IaC) — VPC, DynamoDB, ElastiCache, SQS, Lambda, ECS Fargate, Cognito, WAF | Beacon Presence |
| **Docker** — multi-stage builds with Chromium, workers as containers | PrintFlow, Floor Planner |
| **CI/CD** — GitHub Actions (lint, typecheck, test, Playwright E2E, Artillery load, CDK synth) | Beacon Presence, others |
| **Desktop app** — Windows installer via GitHub Actions (silent printing) | PrintFlow |

---

## Payments, security & compliance

| Skill | Evidence |
|---|---|
| **Redsys payment gateway** — HMAC-SHA256 signing, server-to-server webhook, idempotency | Online Registration |
| **Authentication** — `iron-session`, passwordless OTP (Twilio Verify / Resend), bcrypt + pepper, dual session | Online Registration |
| **Authorization** — RLS, `SECURITY DEFINER` RPC + `BEFORE UPDATE` trigger, 3-tier role hierarchy | AudioNow, TaskBoard |
| **Rate limiting / anti-abuse** — Upstash, circuit breaker, magic-byte validation on uploads | Online Registration, PrintFlow, Beacon Presence |
| **Privacy** — anti-impersonation rules, data fences (never expose tax IDs), `audit_log` | Online Registration |

---

## Methodology

| Skill | Evidence |
|---|---|
| **AI-augmented development** — Claude Code with phase-based planning (GSD) | Cross-cutting (`.planning/` in every repo) |
| **Goal-backward verification** — `VERIFICATION.md` per phase | Online Registration, PrintFlow, AudioNow, Realtime Translation |
| **TDD / testing** — Vitest, Jest, Testing Library; 881 tests (Registration), 366+ files (Beacon) | Online Registration, Beacon Presence |
| **Technical writing** — specs, informal ADRs, Mermaid diagrams | Cross-cutting |
| **Mentorship** — trained an intern in AI tooling and 3D libraries | Floor Planner |
