<p align="right"><a href="STACK.es.md">Versión en español</a></p>

# Stack and contribution

Technologies and practices linked to the case and contribution that support them. Delivery and validation scope belongs to each case; the mentorship project is not attributed as individual implementation. Historical versions are retained where they explain a decision.

## Web applications

| Technology or practice | Case and contribution |
|---|---|
| **Next.js App Router · React** | [Online Registration](projects/online-registration.md) — Individual/group flows, server actions and tenant-specific web journeys |
| **React Three Fiber · Rapier** | [PrintFlow](projects/printflow.md) — Implementation of a configurable 3D kiosk alongside the printing workflow |
| **Three.js · 2D views** | [Floor Planner](projects/floor-planner.md) — Mentorship of the editor project; the intern implemented the application |
| **Serwist · IndexedDB** | [PrintFlow](projects/printflow.md) — Prepared local assets and replay of queued print-state changes |
| **next-intl · translation pipeline** | [Online Registration](projects/online-registration.md) — Six locale catalogs and structured fallbacks; linguistic review distinguished from key parity |
| **TanStack Query · Supabase Realtime** | [TaskBoard](projects/taskboard.md) — Client state and request/vote updates in an internal tool |

## Backend and integration

| Technology or practice | Case and contribution |
|---|---|
| **NestJS · LiveKit** | [AudioNow](projects/audionow.md) — Server-side translation clients, shared audio tracks and session ownership |
| **Next.js Server Actions · Drizzle** | [Online Registration](projects/online-registration.md) — Purchasing identities, payment actions and relational ownership checks |
| **Puppeteer · HTML to PNG/PDF** | [PrintFlow](projects/printflow.md) — Resolution-configurable generation, bounded concurrency and browser recovery |
| **FileMaker Data API** | [Schedule Builder](projects/schedule-builder.md) — Read-only application wrapper, record mapping and manual CSV fallback |
| **Controlled queue handlers** | [Online Registration](projects/online-registration.md) — Deferred legacy writes with permitted operations and parameter boundaries |
| **Tesseract.js · Jimp · PDF text** | [Floor Planner](projects/floor-planner.md) — Technical guidance on the located import workflow; OCR executes in the Next.js route/process |

## Data and access control

| Technology or practice | Case and contribution |
|---|---|
| **PostgreSQL · Drizzle** | [Online Registration](projects/online-registration.md) — Relational model, constraints, indexes and versioned SQL migrations |
| **Supabase RLS · RPCs · triggers** | [AudioNow](projects/audionow.md) — Three-tier streaming permissions and controlled state-change paths |
| **Prisma · PostgreSQL** | [PrintFlow](projects/printflow.md) — Credential/design persistence and reconciliation between data sources |
| **DynamoDB · GSIs · TTL** | [Beacon Presence](projects/ble-presence.md) — State model for the software presence pipeline |
| **Redis · single-flight token cache** | [Schedule Builder](projects/schedule-builder.md) — Shared FileMaker session token and lock; distinguished from agenda-data caching |
| **Supabase Realtime** | [TaskBoard](projects/taskboard.md) — Subscriptions around persisted requests and in-app notifications |

## Real-time media and AI

| Technology or practice | Case and contribution |
|---|---|
| **WebRTC SFU · server-side bots** | [AudioNow](projects/audionow.md) — One translated track distributed to listeners; translation sessions organized per room/language |
| **PCM · limiter · resampling** | [AudioNow](projects/audionow.md) — Peak compression, chunk smoothing and sample-rate adaptation with branch-specific scope |
| **Speech-provider registry** | [Realtime Translation](projects/realtime-translation.md) — Seven registered adapters behind one contract; live validation differs by adapter |
| **Watchdogs · adaptive playout** | [Realtime Translation](projects/realtime-translation.md) — Session robustness and queue-depth control; bounded observability in the PoC evolution |

## Algorithms and infrastructure

| Technology or practice | Case and contribution |
|---|---|
| **Kalman filter · hysteresis** | [Beacon Presence](projects/ble-presence.md) — RSSI filtering and presence transitions; physical calibration remained a separate milestone |
| **AWS IoT · Lambda · SQS** | [Beacon Presence](projects/ble-presence.md) — Four processing stages with queue boundaries; Kinesis/S3 as parallel ingestion branches |
| **AWS CDK** | [Beacon Presence](projects/ble-presence.md) — Infrastructure as code for the MVP; not a claim of currently running cloud infrastructure |
| **Docker · Chromium · Railway** | [PrintFlow](projects/printflow.md) — Backend deployment with headless rendering and constrained memory |
| **Vercel · Railway · Supabase** | [AudioNow](projects/audionow.md) — Separate web, API and data services; single API replica in the described version |
| **Electron · Windows packaging** | [PrintFlow](projects/printflow.md) — Desktop bridge, silent print requests and portable/NSIS distribution |

## Payments, privacy and collaboration

| Technology or practice | Case and contribution |
|---|---|
| **Redsys · attempt identity** | [Online Registration](projects/online-registration.md) — Gateway signing, webhook handling, retry ownership and payment-attempt reuse |
| **OTP · iron-session · bcrypt** | [Online Registration](projects/online-registration.md) — Distinct identities for individual attendees and authenticated group buyers |
| **Data boundaries · audit records** | [Online Registration](projects/online-registration.md) — Role/tenant restrictions and explicit privacy requirements; not a legal-compliance certification |
| **Notifications · Resend** | [TaskBoard](projects/taskboard.md) — In-app persistence followed by an email attempt with isolated errors; activation scope dated in the case |
| **Mentorship · technical review** | [Floor Planner](projects/floor-planner.md) — Initial architecture, implementation guidance and review; code authored by the intern |

## Engineering practice

The cases connect these tools to constraints and alternatives. [Methodology](METHODOLOGY.md) explains discovery, planning, review and AI assistance; [testing and validation](TESTING.md) separates inventory, historical execution and operational checks.

[Back to overview](README.md)
