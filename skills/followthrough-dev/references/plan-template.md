# Reference: `docs/FOLLOWTHROUGH_PLAN.md` Template

Use this structure when scaffolding `docs/FOLLOWTHROUGH_PLAN.md`.

## Planning Rules

- Order phases and tasks sequentially so features build incrementally and each completed task produces something concrete to inspect or test.
- Number tasks as `<Phase>.<Task>` (for example, `0.1`, `0.2`, `1.1`, `1.2`).
- **Feasibility Phase Rule:** If the project is a proof of concept, multi-platform app, or carries high technical risk, dedicate Phase 0 or Phase 1 to proving the core risky mechanics as an **extendable prototype** (plus minimal core project structure if needed) before building secondary features.
- Include **Deferred / Not Yet Built** notes on tasks where related UI or behavior comes later so neither the developer nor the agent mistakes planned work for a bug.
- **Phase Summary Table:** Always include a summary table at the top of the plan before the task breakdowns. Maintain columns for **Phase**, **Milestone**, **Status** (`Not Started` | `Ongoing` | `Complete`), and **Evidence doc(s)** (clickable markdown link to the corresponding `codebase/phase-XX-<slug>.md` file in `docs/codebase/`). Keep this table updated as phases progress and finish.
- **Phase Acceptance & Verification Task Rule:** Every phase MUST conclude with a dedicated final task (e.g., `Task 0.3 - Phase 0 Acceptance & Build/Regression Verification`). This task defines overall phase acceptance criteria, verifies the project compiles/builds without errors (if applicable to the stack), and runs regression checks to ensure recent changes haven't broken existing functionality.

## Template

```markdown
# Followthrough Plan: <Project Name>

**Status Legend:** `[ ]` Pending | `[x]` Completed | `[!]` Blocked / Needs Decision  
**Branching Strategy:** <Linear Chained `dev` branch branches from phase previous |>  
**Testing Policy:** Manual testing checklist every iteration + <Optional automated policy testing>

---

## Phase Summary

| Phase | Milestone | Status | Evidence doc(s) |
| :--- | :--- | :--- | :--- |
| Phase 0 | <Core Setup & Feasibility Prototype / Phase Title> | Ongoing | [phase-00-setup.md](codebase/phase-00-setup.md) |
| Phase 1 | <Phase 1 Title or Core Outcome> | Not Started | [phase-01-<slug>.md](codebase/phase-01-<slug>.md) |
| Phase 2 | <Phase 2 Title or Core Outcome> | Not Started | [phase-02-<slug>.md](codebase/phase-02-<slug>.md) |

---

## Phase 0: Core Setup & Feasibility Prototype _(Include when needed)_

**Goal:** Set up core project skeleton and validate <critical risky assumption> end-to-end in an extendable structure.  
**Target Branch:** `phase-00-setup`

- [ ] **Task 0.1 - <Short Task Title>**
  - **Scope:** <Concrete implement to work>
  - **Expected Result:** <What after right task this works>
  - **What to Test:** <Quick manual or script target verification>
  - **Deferred / Not Yet Built:** <Related features for intentionally later scheduled>

- [ ] **Task 0.2 - <Short Task Title>**
  - **Scope:** <Concrete implement to work>
  - **Expected Result:** <What after right task this works>
  - **What to Test:** <Quick manual or script target verification>
  - **Deferred / Not Yet Built:** <Related features for intentionally later scheduled>

- [ ] **Task 0.3 - Phase 0 Acceptance & Build/Regression Verification**
  - **Scope:** Verify the full project builds cleanly (if applicable), check for regressions in setup/prototype functionality, and validate that Phase 0 acceptance criteria are fully met.
  - **Expected Result:** Clean build with zero compile/bundling errors; existing setup works end-to-end without breaks.
  - **What to Test:** Run build script (e.g., `npm run build`), verify linters/tests, and test basic end-to-end workflow.
  - **Deferred / Not Yet Built:** <Features intentionally reserved for Phase 1+>

---

## Phase 1: <Phase Title>

**Goal:** <Clear for milestone outcome phase this>  
**Target Branch:** `phase-01-<slug>`

- [ ] **Task 1.1 - <Short Task Title>**
  - **Scope:** <Concrete implement to work>
  - **Expected Result:** <What after right task this works>
  - **What to Test:** <Quick manual or script target verification>
  - **Deferred / Not Yet Built:** <Related features for intentionally later scheduled>

- [ ] **Task 1.2 - <Short Task Title>**
  - **Scope:** <Concrete implement to work>
  - **Expected Result:** <What after right task this works>
  - **What to Test:** <Quick manual or script target verification>
  - **Deferred / Not Yet Built:** <Related features for intentionally later scheduled>

- [ ] **Task 1.3 - Phase 1 Acceptance & Build/Regression Verification**
  - **Scope:** Run full project build and verify no regressions across Phase 0 or Phase 1 features. Confirm all Phase 1 acceptance criteria are satisfied.
  - **Expected Result:** Clean build and successful integration across all implemented functionalities without breaking prior work.
  - **What to Test:** Execute build command, run test suite, and smoke test critical paths from both Phase 0 and Phase 1.
  - **Deferred / Not Yet Built:** <Features intentionally reserved for Phase 2+>
```
