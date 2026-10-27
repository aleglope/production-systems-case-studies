<p align="right"><a href="METHODOLOGY.es.md">Versión en español</a></p>

# Engineering methodology

I used AI-assisted development alongside discovery, design notes, scoped implementation and review. The projects used different combinations of phase plans, specifications and verification records; they did not all follow one uniform process.

This page explains the working practices behind the cases. The original planning artifacts remain private, so the public archive summarizes selected decisions rather than offering a reproducible audit of every internal record.

## Start with the operational problem

In [Online Registration](projects/online-registration.md), I studied the existing workflow before changing the web platform: working sessions with the internal team, legacy behavior, data ownership and the difference between individual and group purchasers. These observations became requirements and delivery boundaries.

The constraint was coexistence: new web flows had to evolve while the operational legacy system remained in use. That led to separate identities, controlled write paths and a staged rollout rather than a single replacement.

## Break implementation into bounded deliveries

I used phase plans and design notes to identify dependencies, alternatives and acceptance criteria. Verification records distinguished code checks, automated tests and human or operational checkpoints.

Examples of that distinction:

| Case | Planning or verification decision |
|---|---|
| [Online Registration](projects/online-registration.md) | Separate M1–M3 delivery from later milestones and provider-activation checks |
| [PrintFlow](projects/printflow.md) | Record field feedback after the first delivery and validate extensions such as offline video separately |
| [Beacon Presence](projects/ble-presence.md) | Move from a software MVP to a local harness before claiming real-hardware accuracy |
| [Realtime Translation](projects/realtime-translation.md) | Distinguish a registered adapter, automated checks and a live/provider-access test |
| [Schedule Builder](projects/schedule-builder.md) | Combine mocked integration tests with a documented end-to-end PDF check |

A closed plan is not itself proof of deployment. A later fix can also supersede an earlier gap: the case should reflect the dated implementation and its verification, not an isolated progress percentage.

## Use AI for scoped engineering work

I used coding assistants, reusable skills and parallel tasks for research, implementation and review. Project instructions captured conventions and constraints so that a new session could work from the same context.

Two specialized review agents in the AudioNow work addressed:

- **Translation-session review:** session leaks, concurrent start/stop operations and audio regressions around the LiveKit/provider bridge.
- **Migration review:** consistency between Prisma/Supabase changes, schema and access policies.

These tools supported review; they did not guarantee correctness or replace acceptance checks. Architecture, scope decisions and verification remained my responsibility.

## Keep decisions connected to their consequences

The useful record is the reason for a choice and the behavior it permits:

- [AudioNow](projects/audionow.md): a single API replica keeps session ownership simple, with horizontal scaling outside that version's scope.
- [PrintFlow](projects/printflow.md): a desktop host provides silent printing, at the cost of packaging and device configuration.
- [Online Registration](projects/online-registration.md): restricted queue handlers limit the legacy write surface, while activation still requires operational checks.

The case studies retain those trade-offs. Aggregate counts of plans, phases or agent instructions are omitted because different projects used different units and version snapshots.

## Transfer the approach through mentorship

In [Floor Planner](projects/floor-planner.md), my contribution was guidance, initial architecture and technical review. The intern implemented the application. The case explains that role separately from implementation ownership.

[Testing and validation](TESTING.md) · [Stack and contribution](STACK.md) · [Overview](README.md)
