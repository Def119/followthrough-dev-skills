---
name: followthrough-dev
description: Enforces a structured, learning-first software development workflow with architecture specs, optional feasibility prototyping, phased followthrough checklists, Action-ID (P.T.S) telemetry logs, phase-wise codebase learning docs, linear Git phase branching, and in-chat manual testing checklists. Use when starting or structuring a software project, turning a rough idea or spec MD into a phased plan, executing project tasks or phases incrementally, logging revisions or rework, or wrapping up a development phase.
---

# followthrough-dev

Guide individual software projects from requirement analysis through incremental implementation, verification, and deployment so the developer builds genuine architectural and codebase mastery instead of black-box vibe coding.

## When to Use

Use this skill when the user wants to:

- Brainstorm a project idea into a technical spec and architecture document
- Initialize `docs/` planning, logging, and learning files from an existing spec MD
- Implement a project incrementally (task-by-task or phase-at-a-time) with full traceability
- Rework or fix a previously completed task while keeping logs and learning docs accurate
- Wrap up a completed phase, audit architecture drift, and transition Git branches

## Core Operating Rules

1. **Progressive Template Loading:** Read the matching file in `references/` before creating or updating any `docs/` artifact so formats stay consistent.
2. **Adopt Existing Specs:** If the user already has an initial project plan or idea file (for example, `docs/PROJECT_PLAN.md`), adopt and reference it instead of creating a duplicate `docs/SPEC.md`.
3. **Anti-Vibe-Coding Transparency:** Never treat code generation alone as done. Every completed task or rework must update the plan, action log, and phase learning doc, and output a plain-English manual testing checklist directly in chat.
4. **Global Skip Escape Hatch:** At any interactive gate (missing preferences, testing, branch warnings, architecture audit), if the user says "skip", "use defaults", or "skip for now", do not block or re-ask. Proceed immediately with sensible defaults and record `SKIPPED (user override)` in `docs/ACTION_LOG.md`.

## Workflow Modes

Determine which mode fits the current user request and repository state, then jump straight into it.

---

### Mode 1: Ideation, Architecture Lock, and Feasibility Gate

Use when the user has a rough idea, partial notes, or wants to design the project before scaffolding.

1. Discuss and lock down core requirements at a high level:
   - Problem statement, core functionalities, and non-goals
   - Tech stack, tools, methodologies, external APIs, and data models
   - System-level architectural decisions and deployment scope (if included)
2. **Run the Feasibility Gate:** Assess whether the project involves unproven technical risk (proof-of-concept mechanics, multi-platform support, unfamiliar APIs/SDKs, or hardware integration).
   - If high uncertainty exists, propose putting core project setup and critical risky features into an early **Feasibility / Prototype Phase** (Phase 0 or Phase 1).
   - Design that prototype to be extendable into the final codebase rather than throwaway code, proving end-to-end viability before investing in polish.
3. Write or finalize `docs/SPEC.md` (or the user's chosen spec filename).
4. Read `references/architecture-template.md` and create or update `docs/ARCHITECTURE.md` with system-level details.
5. Proceed to Mode 2 once the user confirms the spec.

---

### Mode 2: Project Workflow Scaffold

Use when a finalized spec MD exists (either from Mode 1 or provided directly by the user).

1. **Batched Missing-Info Gate:** If any of the following preferences are not already specified, ask them together in **one compact message** before generating files:
   - Whether a **Feasibility / PoC phase** is needed first (Phase 0 or Phase 1)
   - Preferred **testing level** (manual checklist only, automated scripts plus manual checklist, or decide per phase)
   - Preferred **Git branching base** (branch each phase from an aggregating `dev` branch, or chain linearly from the previous phase branch)
2. Read the reference templates:
   - `references/architecture-template.md`
   - `references/plan-template.md`
   - `references/action-log-template.md`
   - `references/learning-doc-template.md`
3. Create or update the target repository files:
   - `docs/ARCHITECTURE.md` (synced from the initial spec)
   - `docs/FOLLOWTHROUGH_PLAN.md` (sequential phases `0`, `1`, `2`... and incremental testable tasks `0.1`, `0.2`, `1.1`...)
   - `docs/ACTION_LOG.md` (initialized with Action ID `P.T.S` format rules)
   - `docs/codebase/phase-XX-<slug>.md` (stubbed for the first active phase)
4. **Write the `AGENTS.md` Persistence Guardrail:** Create `AGENTS.md` (or append to it without overwriting existing rules; also append to `CLAUDE.md` only if it already exists in the repo) with this exact block so long sessions do not forget the workflow:

```markdown
## Followthrough Dev Workflow Guardrail

This repository uses the `followthrough-dev` incremental workflow.
Never mark a task or rework complete until ALL steps below are done:

1. Update the task status (`[x]`) in `docs/FOLLOWTHROUGH_PLAN.md`.
2. Append a new sequential `Action P.T.S` entry (with `Task ID` inside metadata) to `docs/ACTION_LOG.md`.
3. Update `docs/codebase/phase-XX-<title>.md` with both an Architecturally Grounded Plain-English Mental Model and a Technical Walkthrough.
4. Update `docs/ARCHITECTURE.md` only if system-level architecture changed.
5. Output a plain-English summary of changes and a step-by-step Manual Testing Checklist directly in chat.
   At the start of a new phase, warn if a new phase branch was not created; proceed on the same branch only if the user consents.
```

5. Remind the user to verify or create the initial phase branch before starting Mode 3.

---

### Mode 3: Execution Loop (Task, Phase, and Rework)

Use when implementing a task, running a full phase, or applying user-requested fixes/rework.

#### Pre-Execution: Git Branch Gate (Start of a New Phase Only)

Before executing the first task of a new phase:

1. Check the active Git branch (run `git branch --show-current` if terminal access exists, or ask the user).
2. If the user is still on the previous phase's branch (or on `main`/`dev` without creating a dedicated phase branch):
   - Issue a clear **Warning** stating the current branch and recommending a dedicated branch for clean phase inspection and rollback.
   - Provide the exact copy-paste command (for example, `git checkout -b phase-02-<slug>`).
   - Ask whether to switch branches first or proceed on the current branch.
3. **Consent Override:** If the user consents to stay on the current branch, proceed immediately without further blocking and note `Branch Warning Acknowledged - proceeded on <branch> by user consent` in `docs/ACTION_LOG.md`.

#### Execution Granularity

- **Task-by-Task Mode (Default):** Execute one task (`P.T`), finish the Definition of Done below, and pause for user testing and feedback.
- **Phase-at-a-Time Mode (On Request):** Execute remaining tasks in the requested phase sequentially (`P.1` -> `P.2` -> `P.3`). Write **individual per-task** entries in `docs/ACTION_LOG.md` and `docs/codebase/phase-XX-<slug>.md` as each task completes rather than collapsing the phase into one summary. Pause at phase end for review.
- **Rework / Change-Request Mode:** When the user asks to modify or fix a previously completed task `P.T`:
  - Implement the fix cleanly.
  - Append a **new** entry to `docs/ACTION_LOG.md` incrementing the 3rd digit of the Action ID (`Action P.T.2`, `Action P.T.3`, ...) while referencing the same `Task ID: P.T`.
  - Update the corresponding task section in `docs/codebase/phase-XX-<slug>.md` so the guide reflects current reality, and add a brief revision note referencing the new Action ID.

#### Mandatory Definition of Done (Every Iteration)

Do not finish a response until all five steps are completed:

1. **Implement** the code or configuration changes cleanly.
2. **Update Plan:** Mark `[x]` in `docs/FOLLOWTHROUGH_PLAN.md` (or leave `[ ]` / `[!]` if partially blocked).
3. **Log Action:** Append a lean `Action P.T.S` entry to `docs/ACTION_LOG.md` following `references/action-log-template.md`.
4. **Update Learning Docs:** Update `docs/codebase/phase-XX-<slug>.md` following `references/learning-doc-template.md`. Update `docs/ARCHITECTURE.md` **only** if system-level architecture, APIs, stack, or major design decisions changed.
5. **Output In-Chat Manual Testing Checklist:** Always print the block below directly in chat so the user can test immediately without opening `docs/`:

```markdown
### Completed: Action <P.T.S> (Task <P.T> - <Title>)

**What Changed (Plain English):**

- <2 to 4 concise points on what changed and how it affects the app>

**Manual Testing Checklist:**

1. [ ] <Concrete /route action, and dev e.g., run server visit> -> **Expect:** <observable result>
2. [ ] <Edge case interaction or to verify> -> **Expect:** <observable result>

**Not Built Yet (Intentional):**

- <1 to 2 reminders of related features deferred to upcoming tasks or phases>

**Docs Updated:** `FOLLOWTHROUGH_PLAN.md`, `ACTION_LOG.md` (`Action <P.T.S>`), `docs/codebase/phase-XX-<slug>.md`
```

---

### Mode 4: Phase Wrap-Up and Branch Transition

Use when all tasks in the active phase are marked `[x]` and verified by the user.

1. Run configured phase-level automated tests (if enabled for the project) and output a brief phase-level manual smoke test checklist in chat.
2. Audit `docs/ARCHITECTURE.md` against what was actually built in this phase and reconcile any drift.
3. Prompt the user for Git transition:
   - Commit final phase changes.
   - Merge into `dev` (if using an aggregating branch) or prepare to branch linearly from the current phase branch.
   - Create the next dedicated phase branch (provide exact copy-paste `git` commands).
4. Initialize the next phase's file inside `docs/codebase/phase-XX-<slug>.md`.

## Gotchas

- **Why Action ID (`P.T.S`) is the heading in `ACTION_LOG.md`:** Using Task ID as the heading breaks chronological clarity whenever the user requests rework on an earlier task. Keeping `Action P.T.S` as the title and `Task ID` inside metadata preserves an accurate, append-only audit trail.
- **Avoid dumbing down the Layman section:** The plain-English explanation in `docs/codebase/phase-XX-<slug>.md` is for a developing engineer, not a non-technical stakeholder. Keep high-level architectural concepts (layers, boundaries, data flow, roles) clear and approachable rather than stripping away all technical meaning.
- **Avoid doc bloat:** Document module responsibilities, entry points, runtime execution flow, and why key decisions were made. Do not narrate trivial syntax line by line.
