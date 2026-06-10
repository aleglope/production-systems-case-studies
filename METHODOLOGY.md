<p align="right"><a href="METHODOLOGY.es.md">🇪🇸 Versión en español</a></p>

# Methodology: AI-augmented development with engineering discipline

Building **8 production systems in a matter of months, solo**, was not vibe coding. It was a deliberate methodology combining AI tooling (Claude Code) with a phase-based planning and verification process that leaves an **auditable trail in every repository**.

This document collects the **real evidence** of that process — what a recruiter or lead can actually verify.

---

## 1. Phase-based planning before code (GSD)

Every milestone is broken down into phases, and every phase produces `PLAN`, `RESEARCH`, `CONTEXT` and `REQUIREMENTS` documents **before** any code is written. Every phase closes with a `VERIFICATION.md` that checks — goal-backward — that the objective was achieved, not just that tasks "got done".

**Aggregate evidence:** **37 phases** planned and **30 verification documents** across the ecosystem.

---

## 2. Custom reusable agents

Beyond *using* AI, I built **specialized agents for my domain**, versioned in the repo (`.claude/agents/`):

| Agent | Project | What it automates |
|---|---|---|
| **`livekit-translation-reviewer`** | AudioNow | Audits the LiveKit ↔ Palabra/OpenAI bridge for session leaks, race conditions and audio regressions |
| **`prisma-supabase-migration-checker`** | AudioNow | Reviews Prisma/Supabase migrations against the schema and RLS policies before they are applied |

That's the difference between *consuming* a tool and *building your own tooling* on top of it.

---

## 3. Subagent-driven development and skills

The work leaned on **subagents** (parallel task decomposition) and reusable skills. Several specs declare it explicitly (e.g. *"brainstormed with Claude"*, *"REQUIRED SUB-SKILL: subagent-driven-development"*).

**Evidence:** **~56 documents** of design specs and plans (AudioNow concentrates ~49), each with its decision log and execution checklists.

---

## 4. Conventions codified for the AI

`CLAUDE.md` / `AGENTS.md` files codify each project's rules so that any AI session respects them — for example, *"this Next.js 16 version has breaking changes: read the docs before touching code"*, or the **read-only FileMaker** policy.

**Evidence:** `CLAUDE.md` in **6 of 8** projects · `AGENTS.md` in **3 of 8**.

---

## 5. Decision traceability

Decisions are referenced in the code itself: decision IDs (`D-XX`), numbered pitfalls and plan references (`Phase 33 Plan 33-08`) embedded in comments. Anyone can reconstruct *why* something was done a certain way.

---

## Evidence per project

| Project | GSD phases | Verif. docs | Specs+Plans | Custom agents | `CLAUDE`/`AGENTS` |
|---|---:|---:|---:|---:|:--|
| Online Registration | 16 | 11 | 1 | — | ✓ / ✓ |
| Congress Translation | 10 | 10 | — | — | ✓ / — |
| BadgeFlow | 5 | 5 | 2 | — | ✓ / — |
| Programa-Web | 4 | 4 | 2 | — | ✓ / — |
| AudioNow | — | — | **49** | **2** | — / — |
| Beacon Attendance | 1 | — | — | — | ✓ / — |
| LogiTasks | 1 | — | 2 | — | ✓ / ✓ |
| Dinner Room | — | — | — | — | ✓ / ✓ |

---

## The result

**One person's speed, a team's process rigor.** AI accelerates execution; architecture, decisions and verification remain the developer's responsibility. That same discipline was transferred to an **intern** I trained in AI tooling and 3D libraries (see [Dinner Room](projects/sala-cenas.md)).

> For each system's test suite, see **[TESTING.md](TESTING.md)**.
