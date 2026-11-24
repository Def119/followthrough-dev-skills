# Reference: `docs/ACTION_LOG.md` Template

Use this structure when initializing and appending to `docs/ACTION_LOG.md`.

## Action ID Rules (`P.T.S`)

- Every entry is titled with its **Action ID**: `Action <Phase>.<Task>.<Sequence>`.
- Keep the parent **Task ID** (`<Phase>.<Task>`) inside the metadata block.
- `<Sequence>` starts at `1` for initial implementation of a task and increments (`2`, `3`, ...) for any follow-up rework, change request, bug fix, or rollback belonging to the same Task ID.
  - Example: Initial work on Phase 0, Task 1 -> `Action 0.1.1` (`Task ID: 0.1`).
  - Example: Revision requested on Phase 0, Task 1 -> `Action 0.1.2` (`Task ID: 0.1`).
- Keep entries append-only and lean. Do not invent extra telemetry fields beyond those listed below.
- If the user skips a gate or consents to remain on a previous branch, record it explicitly in **Verification** or **Issues / Decisions**.

## File Header (When Initializing `docs/ACTION_LOG.md`)

```markdown
# Action Log: <Project Name>

Chronological, append-only record of all implementation work, revisions, verifications, and decisions.  
**ID Format:** `Action <Phase>.<Task>.<Sequence>` (e.g., `Action 0.1.1`, `Action 0.1.2` for rework on Task `0.1`).

---
```

## Entry Template (Append Per Action)

```markdown
## Action <P.T.S> - <Concise Action Title>

- **Task ID:** `<P.T>` | **Phase:** Phase <P> | **Branch:** `<git-branch-name>`
- **Timestamp:** YYYY-MM-DD HH:MM | **Status:** Completed / Rework / Partial / Reverted
- **Verification:** <e.g., Manual checklist provided; unit tests passed | SKIPPED (user override)>
- **Files Touched:** `<path/to/file>` (added), `<path/to/other>` (modified)
- **Summary:** <1-3 concise sentences summarizing what was actually implemented or changed>
- **Issues / Decisions:** <Bugs "None" branch-override consent, design hit, or trade-offs, workarounds,>
```
