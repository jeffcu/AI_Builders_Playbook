# [Project Name] — Engineering Guide

> **This is a living document.** Every session reads it at the start and updates it at the end.
> Replace all `[bracketed text]` with your project's specifics as you build.
> Delete instructions in `> blockquotes` once you've completed each section.

---

## What This Project Is

> 2–4 sentences. Plain language. What it does, who it's for, what makes it distinct.
> Write it as if explaining to a smart friend who just walked in.
> This is the one paragraph every AI will read first — make it precise.

[Describe your project here.]

---

## Always Read First

> List any files (specs, persona definitions, API contracts, design docs) that must be read
> before touching specific areas of the code. This prevents the AI from working blind.

1. This file — architecture, constraints, and current state
2. [filename] — [what it contains and when to read it]
3. [filename] — [what it contains and when to read it]

---

## Session Protocol — Mandatory

This document is the project's memory. Every session must follow this protocol exactly.

### Before starting any task
1. Read this entire CLAUDE.md. Do not skip sections.
2. Check **Current State** — confirms what's working, what's broken, what's next.
3. Check **Debugging History** for the area you're working in. If an approach has already failed, do not repeat it.
4. For any external API or service: fetch live documentation before writing a single line. Never rely on training data for API contracts.
5. State today's goal in one sentence. Do not begin until that goal is confirmed.

### During the session
6. Stay on the current Build Plan phase. Do not drift to other work without an explicit decision to change.
7. When an attempt fails, record it in Debugging History immediately — what was tried, what happened, root cause if known.
8. When an attempt succeeds, note it so Current State can be updated.
9. If you discover a constraint not yet documented, add it to Critical Constraints.
10. Review proposed changes before accepting. Do not accept changes to out-of-scope components.

### At the end of every session
11. Run the self-assessment: update Current State, Build Plan status, Debugging History, What's Next, and Session Log.
12. If new architectural decisions were made, add them to Locked Design Decisions with reasoning.
13. If a new API or component was successfully integrated, document its working contract here.

**The goal:** no session ever repeats a failure a previous session diagnosed.
The project moves forward along the plan — never sideways or backwards
unless the plan is explicitly updated with new learnings.

---

## Architecture Overview

> Describe the major components and how they connect. Plain English.
> Include a simple diagram if it helps. This does not need to be precise —
> it needs to be clear. Update this if the architecture changes.
> Include file paths once they exist so the AI can orient quickly.

### Components

[Component 1] — [what it does]
[Component 2] — [what it does]
[Component 3] — [what it does]

### How They Connect

[Describe the data flow: what happens when a user does the primary action,
step by step, from front to back.]

### File Structure

```
[project-root]/
├── [file or folder]    ← [one-line description]
├── [file or folder]    ← [one-line description]
└── [file or folder]    ← [one-line description]
```

> Add real paths as the project is built. Mark the entry point clearly.
> Note the "source of truth" file for any important configuration.

---

## Running the Project

> Fill this in after the first working session. Keep it accurate.
> Include every command needed to start the project from scratch.

```bash
# [How to start the backend / server]

# [How to start the frontend / UI]

# [Any environment setup required]
```

**Environment variables required** (stored in `.env`, never committed to git):
```
[VAR_NAME]=...     # [what it's for]
[VAR_NAME]=...     # [what it's for]
```

---

## Critical Constraints

> These are rules that must never be violated, simplified, or worked around.
> They protect decisions that were hard-won or that would break the system if changed.
> State them as direct prohibitions, not as background information.
> Add new ones as they're discovered. Never remove them.

- **[CONSTRAINT]:** [State the rule as a direct prohibition. Why does it matter if violated?]
- **[CONSTRAINT]:** [State the rule as a direct prohibition. Why does it matter if violated?]

> Example of a well-written constraint:
> "NEVER modify the session state schema without running a database migration first.
> Skipping this will silently corrupt existing sessions with no error message."

---

## Locked Design Decisions

> Record every significant architectural choice here — with the reasoning.
> The reasoning is as important as the decision: it prevents future sessions
> from accidentally undoing carefully considered choices.
> A locked decision can be changed, but only deliberately and with a documented reason.

| Question | Decision | Reasoning |
|---|---|---|
| [What was decided?] | [What was chosen] | [Why — including alternatives rejected] |
| [What was decided?] | [What was chosen] | [Why — including alternatives rejected] |

---

## Component / Service Status

> Use this section once the project has multiple services, routes, or modules.
> It prevents the AI from treating legacy or dead code as active.

| Component | File | Status | Notes |
|---|---|---|---|
| [Name] | [path/to/file] | **Active** | [what it does] |
| [Name] | [path/to/file] | **Legacy** — do not use | [why it exists, what replaced it] |
| [Name] | [path/to/file] | **In progress** | [current state] |

---

## Build Plan

> The phased construction sequence. Each phase produces something demonstrably working.
> Done criteria must be specific things you can observe or test — not vague descriptions.
> Mark phases as they complete. Do not begin a phase until the previous phase's
> done criteria are fully met.

### Phase 1 — [Name: e.g., "Working Skeleton"]
**Goal:** [Single sentence — what this phase achieves]
**Builds:** [The specific components constructed in this phase]
**Done when:** [Concrete, observable test — e.g., "User can log in and see an empty dashboard"]
**Prerequisite:** [What must be true before this phase begins]
**Status:** `[ ] Not started`

### Phase 2 — [Name]
**Goal:**
**Builds:**
**Done when:**
**Prerequisite:** Phase 1 complete
**Status:** `[ ] Not started`

### Phase 3 — [Name]
**Goal:**
**Builds:**
**Done when:**
**Prerequisite:** Phase 2 complete
**Status:** `[ ] Not started`

> Add phases as needed. Keep the sequence honest —
> if a phase reveals that the plan needs to change, update it here
> and add a note explaining why.

---

## MVP Scope

> What the first working version includes and — equally important — what it deliberately excludes.
> This is the agreement made before building started. Refer back to it when scope starts to drift.

### In scope
- [Feature or capability — one line]
- [Feature or capability — one line]

### Out of scope (intentionally deferred)
- [Feature — one line reason why it's deferred]
- [Feature — one line reason why it's deferred]

**MVP in one sentence:** [What this version does, for whom, in plain language.]

---

## Current State

> This section is updated at the end of every session.
> It is the first thing checked at the start of every session.
> Be honest. "Unknown" is a valid and important status.

### Confirmed Working
- [Thing that is verified working]

### Known Issues
- [Thing that is broken or behaving incorrectly]

### Unknown / Needs Investigation
- [Thing whose status is unclear]

### Current Build Plan Phase
**Active phase:** [Phase name]
**Remaining in this phase:** [What's left to complete the done criteria]

---

## What's Next

> The top 1–5 priorities for the next session.
> One sentence each. Update at the end of every session.

1. [Highest priority — specific enough that the next session can start immediately]
2. [Second priority]
3. [Third priority]

---

## External Services and APIs

> Document every external service this project connects to.
> Include the authoritative documentation URL so it can be fetched before any integration work.
> Document the working contract once it's been confirmed — endpoint, auth, request/response shape.

### [Service Name]
**Documentation:** [URL]
**Used for:** [What this project uses it for]
**Auth method:** [How authentication works]
**Key endpoints:**
```
[METHOD] [endpoint]
Request: [key parameters]
Response: [key fields]
```
**Known constraints:** [Rate limits, version requirements, gotchas]

---

## Debugging History

> Add a row every time something fails.
> Complete the row when the root cause is known.
> Never delete rows. This table prevents the same failure from happening twice.

| Date | What Was Tried | What Happened | Root Cause |
|---|---|---|---|
| [date] | [what was attempted] | [error or symptom] | [root cause once known] |

---

## Session Log

> One entry per session. Written by the AI during the end-of-session self-assessment.
> Do not edit or summarize past entries.

### [YYYY-MM-DD]
**Phase:** [Build Plan phase]
**Attempted:** [What we tried to do]
**Succeeded:** [What worked]
**Failed:** [What didn't work, and why if known]
**New constraints discovered:** [Anything that must now be documented]
**Plan changes:** [Any changes to Build Plan or Locked Decisions]

---

## Authoritative Sources

> List the official documentation URLs for every external dependency.
> These must be fetched — not assumed — before implementing any integration.
> Training data has a cutoff date. APIs do not.

| Service / Library | Documentation URL | Last verified |
|---|---|---|
| [Name] | [URL] | [date] |

---

*CLAUDE.md is a living document. It reflects the current true state of the project.
If something in this file is wrong, update it immediately — a wrong document is
worse than no document.*
