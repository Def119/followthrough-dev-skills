# Reference: `docs/codebase/phase-XX-<slug>.md` Template

Create **one learning document per phase** inside `docs/codebase/` named with the zero-padded phase number and a short slug (for example, `phase-00-setup.md`, `phase-01-feasibility.md`, `phase-02-auth-flow.md`).

## Authoring Rules

- Write for an undergraduate / developing engineer who wants to understand how the project actually runs without relying on AI.
- **Architectural & Plain-English Mental Model:** Explain the task in clear everyday terms **while keeping high-level architectural ideas intact** (system role, boundaries, layer interactions, data flow). Do not oversimplify to zero technical depth.
- **Technical Walkthrough:** Trace actual files, key symbols (functions, classes, hooks, routes), real runtime execution order, and why key implementation choices were made.
- **Keeping Rework Accurate:** If a task is later revised (for example, `Action 1.2.2`), update the main walkthrough so it always reflects the live code, and add a brief line under **Revision Notes** pointing to the Action ID.

## Template

```markdown
# Phase <XX>: <Phase Title> - Codebase & Learning Guide

**Phase Goal:** <1-2 sentences describing what capability this phase adds to the system>  
**Key Directories / Modules Touched:** `<dir-1>/`, `<dir-2>/`

---

## Task <P.T> - <Task Title>

### Architectural & Plain-English Mental Model

<Clear and architectural comes component context: explanation goes high-level in it layers matters. or out, plain-English plays preserves role separation services structural system, talks that the this to, what which why>

### Technical Walkthrough

- **Files & Key Symbols:**
  - `<path/to/file.ts>`: `functionName()`, `ClassName` - <concise role>
  - `<path/to/other.ts>`: `routeHandler()` - <concise role>
- **Actual Runtime Flow:**
  1. <Entry (e.g., CLI HTTP UI command) event, point request, triggered>
  2. <Validation, transformation, or state lookup>
  3. <Core (DB API and call, effects execution logic render side update) write,>
  4. <Output or response returned>
- **Key Implementation & Design Decisions:**
  - <Why alternatives, and any cases chosen data edge handled library, or over pattern, structure this was>
- **Revision Notes _(Add only if reworked later)_:**
  - `Action <P.T.2>`: <Brief and changed note on what why>
```
