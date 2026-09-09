<p align="right"><a href="TESTING.es.md">🇪🇸 Versión en español</a></p>

# Testing & quality

The testing approach across the ecosystem, with **real data** (test-file counts per project, dependencies excluded). This is not a generic "it has tests" claim: it's the verified inventory.

## Summary

**~314 test files**, distributed as follows:

| Project | Test files | Framework(s) | Test types |
|---|---:|---|---|
| **[Online Registration](projects/online-registration.md)** | **127** | Vitest · Testing Library | Data invariants, Server Actions for both flows, FileMaker queue, OTP, security regressions (CSRF/XSS) |
| **[Realtime Translation](projects/realtime-translation.md)** | **86** | Jest · Supertest | API unit + integration, translation providers |
| **[AudioNow](projects/audionow.md)** | **38** | Vitest · Testing Library | Audio pipeline, soft-limiter, translation sessions |
| **[Beacon Presence](projects/ble-presence.md)** | **32** | Jest · Playwright · Artillery | Unit + **E2E** + **load** (up to 200 rps) |
| **[TaskBoard](projects/taskboard.md)** | **24** | Vitest · Testing Library | Components, voting, notifications |
| **[Schedule Builder](projects/schedule-builder.md)** | **7** (57 cases) | Vitest · Testing Library | Logic + FileMaker mocks |
| **[PrintFlow](projects/printflow.md)** | infra configured | Jest · Supertest | Infrastructure ready; automated coverage logged as post-rollout debt |
| **[Floor Planner](projects/floor-planner.md)** | — | — | Mentorship/learning project |

> **Honesty:** PrintFlow shipped to production against a fixed, immovable go-live date; it has the test infrastructure (Jest + Supertest) configured but prioritized delivery, leaving automated coverage as conscious debt. Floor Planner was an intern's learning vehicle. The rest of the ecosystem carries substantial coverage.

## Per-project detail

### Online Registration — 127 files · 881 tests
The suite covers the **invariants that matter** in a payment system:
- `Persona` uniqueness per association, `Pago` idempotency (the same `id_intento` never duplicates a row), `Inscripción` state machine.
- **Anti-impersonation**: no personal data is ever exposed without a successful OTP.
- Server Actions for both the individual and group flows, `fm_write_queue` handlers, OTP messaging.
- Security regressions (CSRF/XSS).

### Beacon Presence — 32 files · unit + E2E + load
The project with the most complete test pyramid:
- **Unit** (Jest): exhaustive suites — e.g. 47 cases on the zone detector (state transitions, hysteresis), 47 on the presence aggregator (points, bonuses), 18 on the Kalman filter.
- **E2E** (Playwright).
- **Load** (Artillery): scenarios up to 200 rps with warm-up → ramp-up → sustained → peak phases.
- All orchestrated in **CI/CD** (GitHub Actions: lint, typecheck, unit, E2E, load, `cdk synth`).

### Realtime Translation — 86 files
Unit + integration tests for the NestJS API (Supertest), covering the provider registry and translation-session orchestration.

### AudioNow — 38 files
Focused on the audio pipeline: soft-knee limiter, resampling, translation-session lifecycle and the LiveKit bridge. Includes the `openai-realtime` module's `*.spec.ts` (on the canary branch).

### TaskBoard — 24 · Schedule Builder — 7 (57 cases)
Component and business-logic coverage; in Schedule Builder, with FileMaker Data API mocks to test the integration without touching the real system.

## Frameworks & tools

`Vitest` · `Jest` · `ts-jest` · `Supertest` · `Playwright (E2E)` · `Artillery (load)` · `@testing-library/react` · `@testing-library/user-event` · `jsdom` · `GitHub Actions (CI/CD)`
