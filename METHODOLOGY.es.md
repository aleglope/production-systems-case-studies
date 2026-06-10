<p align="right"><a href="METHODOLOGY.md">🇬🇧 English version</a></p>

# Metodología: desarrollo *AI-augmented* con disciplina de ingeniería

Construir **8 sistemas en producción en cuestión de meses, en solitario**, no fue *vibe coding*. Fue una metodología deliberada que combina herramientas de IA (Claude Code) con un proceso de planificación y verificación por fases que deja **rastro auditable en cada repositorio**.

Este documento recoge la **evidencia real** de ese proceso — lo que un reclutador o *lead* puede comprobar.

---

## 1. Planificación por fases antes del código (GSD)

Cada *milestone* se descompone en fases, y cada fase produce documentos `PLAN`, `RESEARCH`, `CONTEXT` y `REQUIREMENTS` **antes** de escribir código. Cada fase cierra con un `VERIFICATION.md` que comprueba —*goal-backward*— que el objetivo se cumplió, no solo que las tareas "se hicieron".

**Evidencia agregada:** **37 fases** planificadas y **30 documentos de verificación** a lo largo del ecosistema.

---

## 2. Agentes reutilizables propios

Más allá de *usar* IA, construí **agentes especializados para mi dominio**, versionados en el repo (`.claude/agents/`):

| Agente | Proyecto | Qué automatiza |
|---|---|---|
| **`livekit-translation-reviewer`** | AudioNow | Audita el *bridge* LiveKit ↔ Palabra/OpenAI buscando fugas de sesión, *race conditions* y regresiones de audio |
| **`prisma-supabase-migration-checker`** | AudioNow | Revisa migraciones Prisma/Supabase contra el esquema y las políticas RLS antes de aplicarlas |

Es la diferencia entre *consumir* una herramienta y *construir* tu propio tooling sobre ella.

---

## 3. Desarrollo dirigido por subagentes y *skills*

El trabajo se apoyó en **subagentes** (descomposición de tareas en paralelo) y en *skills* reutilizables. Varias specs lo declaran explícitamente (p. ej. *"brainstormed with Claude"*, *"REQUIRED SUB-SKILL: subagent-driven-development"*).

**Evidencia:** **~56 documentos** de specs y planes de diseño (AudioNow concentra ~49), cada uno con su *decision log* y *checklists* de ejecución.

---

## 4. Convenciones codificadas para la IA

Ficheros `CLAUDE.md` / `AGENTS.md` codifican las reglas del proyecto para que cualquier sesión de IA las respete — por ejemplo, *"esta versión de Next.js 16 tiene breaking changes: consulta los docs antes de tocar código"*, o la política de **FileMaker de solo lectura**.

**Evidencia:** `CLAUDE.md` en **6 de 8** proyectos · `AGENTS.md` en **3 de 8**.

---

## 5. Trazabilidad de decisiones

Las decisiones quedan referenciadas en el propio código: IDs de decisión (`D-XX`), *pitfalls* numerados y referencias a planes (`Phase 33 Plan 33-08`) embebidos en comentarios. Cualquiera puede reconstruir *por qué* algo se hizo de una forma.

---

## Evidencia por proyecto

| Proyecto | Fases GSD | Verif. docs | Specs+Plans | Agentes propios | `CLAUDE`/`AGENTS` |
|---|---:|---:|---:|---:|:--|
| Inscripción Online | 16 | 11 | 1 | — | ✓ / ✓ |
| Congress Translation | 10 | 10 | — | — | ✓ / — |
| BadgeFlow | 5 | 5 | 2 | — | ✓ / — |
| Programa-Web | 4 | 4 | 2 | — | ✓ / — |
| AudioNow | — | — | **49** | **2** | — / — |
| Beacon Attendance | 1 | — | — | — | ✓ / — |
| LogiTasks | 1 | — | 2 | — | ✓ / ✓ |
| Sala de Cenas | — | — | — | — | ✓ / ✓ |

---

## El resultado

**Velocidad de una persona, rigor de proceso de un equipo.** La IA acelera la ejecución; la arquitectura, las decisiones y la verificación siguen siendo responsabilidad del desarrollador. Esa misma disciplina se transfirió a un **becario** al que formé en el uso de IA y librerías 3D (ver [Sala de Cenas](projects/sala-cenas.es.md)).

> Para la batería de pruebas de cada sistema, ver **[TESTING.md](TESTING.es.md)**.