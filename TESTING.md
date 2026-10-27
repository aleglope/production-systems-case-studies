<p align="right"><a href="TESTING.es.md">Versión en español</a></p>

# Testing and validation

This appendix separates **test assets**, **dated execution records** and **operational validation**. A test-file count describes suite size, not coverage or a passing run. The records below concern historical versions; the applications were not re-run to prepare this documentation update.

## Behaviors and boundaries

| Case | What the tests or checks address | Boundary of that evidence |
|---|---|---|
| [Online Registration](projects/online-registration.md) | Identity and tenant boundaries, payment attempts, retry actions, OTP and queue-handler contracts | Mocked services do not validate the payment gateway, SMS or FileMaker activation in production |
| [AudioNow](projects/audionow.md) | Audio processing, resampling, provider clients and session lifecycle | Main and OpenAI validation branches differ; unit tests do not establish perceptual quality or canary traffic |
| [PrintFlow](projects/printflow.md) | Delivery checks for generation, reconciliation, kiosk and printing; test infrastructure configured | Automated coverage remained a development item; the offline-video extension had a separate human checkpoint |
| [Beacon Presence](projects/ble-presence.md) | Filter/state transitions, aggregation, a local harness and configured E2E/load scenarios | Scenario configuration is not an executed load result or a hardware-accuracy measurement |
| [Realtime Translation](projects/realtime-translation.md) | Provider registry, session orchestration, API boundaries and voice-profile behavior with mocks | Real-provider/perceptual checks and restricted-access features have separate gates |
| [Schedule Builder](projects/schedule-builder.md) | Mapping, dates/text normalization, mocked legacy integration and PDF checks | A verified PDF flow does not establish parity for every source field and layout variant |
| [TaskBoard](projects/taskboard.md) | Components, business rules and email behavior with mocks | Mock email checks do not prove delivery to real recipients or activation of the production migration |
| [Floor Planner](projects/floor-planner.md) | This case documents mentorship and the implemented editor/import workflow | It does not claim an independently validated automated test suite for the intern's implementation |

## Selected historical execution records

These are summaries of internal project records, not newly executed results or a public reproduction package. Dates identify the reported check, not a guarantee that the current service has the same state.

| Case and record | Date | Reported result | Scope and remaining checks |
|---|---|---|---|
| Online Registration, M3 phase verification | 29 May 2026 | 881 passed, 2 skipped, 1 failed | Phase criteria and fixes documented; typing/test debt and live integration checks were recorded separately |
| Schedule Builder, remediation verification | 26 May 2026 | 58 tests passed; typecheck reported | End-to-end PDF evidence also recorded; some source-field parity checks remained |
| Realtime Translation, voice-profile verification | 28 April 2026 | 296 tests passed in the recorded run | Profiles/API tested with mocks; restricted-access and perceptual checks remained separate |

Later summaries may mention different totals. They are not combined across branches, milestones or dates. For example, a summary's claimed run is not treated as an execution by a verifier that explicitly did not run the suite.

## Scenarios worth discussing in an interview

- **Payment retries:** reuse the payment-attempt identity, validate ownership and distinguish retries from a new gateway order. Database constraints, mocked action tests and a live gateway check provide different kinds of assurance.
- **Audio sessions:** concurrent language changes, shutdown and reconnection can leave external clients alive. Lifecycle tests address ownership and cleanup; provider access and listening checks address real output.
- **Presence:** noisy RSSI, short doorway crossings and grace periods exercise a state machine. Physical range, precision and end-to-end latency need a measured hardware experiment.
- **Printing:** prepared local assets and queued state changes address network loss. A successful print call is not a physical receipt from the printer.
- **Legacy export:** valid and invalid source records, manual CSV fallback and a real PDF inspection test different boundaries.

## Inventory conventions

Where a case includes an implementation count, it belongs to the stated version and perimeter. Test files, individual cases, configured tools and executed checks are different units. Generated files, dependencies and copies of the same code across branches must not inflate a combined total.

Inventories are scoped to one version and counting method instead of combining incompatible branches. The emphasis is the invariant, the recorded result and its boundary.

[Methodology](METHODOLOGY.md) · [Stack and contribution](STACK.md) · [Overview](README.md)
