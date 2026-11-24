For beginners : Don't just vibe code. Understand, build, and follow through.

# followthrough-dev

An open Agent Skill for structured, learning-first software development. Built to prevent "vibe coding" by pairing incremental phased execution with architecture specs, action-level telemetry logs, phase-wise learning guides, linear Git branching, and in-chat manual testing checklists.

## Install

### Global (Recommended for Personal / Portfolio Projects)

```bash
npx skills add Def119/followthrough-dev-skills --skill followthrough-dev -g
```

### Project-Local (Locks Version Inside a Repository)

```bash
npx skills add Def119/followthrough-dev-skills --skill followthrough-dev
```

### Local Development / Testing

```bash
npx skills add ./skills/followthrough-dev
```

## What It Creates in Your Project

```text
your-project/
├── AGENTS.md                        # Short persistence guardrail across long sessions
└── docs/
    ├── SPEC.md                      # Finalized idea/spec (or adopts your existing spec file)
    ├── ARCHITECTURE.md              # System-level architecture, stack, APIs, design decisions
    ├── FOLLOWTHROUGH_PLAN.md        # Phase summary table + phased [ ] / [x] checklist with testable tasks
    ├── ACTION_LOG.md                # Chronological log keyed by Action ID (P.T.S)
    └── codebase/
        ├── phase-00-setup.md        # Phase learning guide (Architectural Layman + Technical)
        └── phase-01-feasibility.md
```

## How to Start with followthrough-dev

### 1. Prepare Your Plan (Two Approaches)

- **Option 1: Pre-Planned with a High-Effort Thinking Model (Recommended)**  
  For best results, first brainstorm and draft a comprehensive technical plan (covering architecture, design choices, core features, and tech stack) using a high-effort reasoning model. Save it as `docs/PROJECT_PLAN.md` (or your preferred spec file), then instruct the agent to initialize the followthrough workflow from it. This ensures deep system-level coverage and alignment before implementation begins.

- **Option 2: In-Chat Brainstorming with followthrough-dev**  
  If starting from scratch with just a rough idea, you can prompt the agent to brainstorm requirements, assess feasibility, and generate the initial spec directly. While convenient for quick experimentation, this approach is typically less thorough than drafting a dedicated technical plan with a high-effort reasoning model beforehand.

### 2. Guide the Development Workflow

Once initialized, `followthrough-dev` scaffolds your project architecture, phase summary table, task checklists, telemetry logs, and learning guides. You can direct the agent depending on the project's complexity:

- **Task-by-Task (Recommended for high complexity or unfamiliar stacks):**  
  Instruct the agent to implement one task at a time (e.g., _"Do Task 1.1"_). The agent writes the code, ticks the checkbox in `FOLLOWTHROUGH_PLAN.md`, updates the Phase Summary table, appends an entry to `ACTION_LOG.md`, writes layman + technical mental models in `docs/codebase/`, and outputs a manual testing checklist directly in chat for you to verify.
- **Phase-at-a-Time (Recommended for straightforward setups or simpler projects):**  
  Instruct the agent to execute an entire phase sequentially (e.g., _"Run Phase 1"_). The agent works through all tasks in that phase one by one—maintaining individual per-task telemetry logs and learning guides—then pauses at the end of the phase for your review.

### 3. Handle Rework and Phase Wrap-Up

- **Fixes & Rework:** If something needs adjustment, prompt the agent (e.g., _"Fix the validation error in Task 1.2"_). It updates the code and appends an incremental revision log (`Action 1.2.2`) without erasing past history.
- **Phase Wrap-Up:** When all phase tasks are verified, ask the agent to wrap up (e.g., _"Wrap up Phase 1"_). The agent marks the phase complete in the summary table, audits architecture drift, and guides your Git branch transitions.

## Example Prompts

- _"Start a new project using followthrough-dev. Here is my rough idea: ..."_
- _"Initialize the followthrough workflow from `docs/PROJECT_PLAN.md` (a comprehensive document detailing your project's architecture, design decisions, key features and how they work, and tech stack—starting with a clear, well-defined plan is recommended for workflow initialization)."_
- _"Do Task 1.2."_
- _"Fix the validation error in Task 1.2 and update the docs."_
- _"Run Phase 2."_
- _"Wrap up Phase 1."_
