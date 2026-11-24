For beginners : Don't just vibe code. Understand, build, and follow through.

# followthrough-dev

An open Agent Skill for structured, learning-first software development. Built to prevent "vibe coding" by pairing incremental phased execution with architecture specs, action-level telemetry logs, phase-wise learning guides, linear Git branching, and in-chat manual testing checklists.

## Install

### Global (Recommended for Personal / Portfolio Projects)

```bash
npx skills add <your-github-username>/followthrough-dev-skill -g
```

### Project-Local (Locks Version Inside a Repository)

```bash
npx skills add <your-github-username>/followthrough-dev-skill
```

### Local Development / Testing

```bash
npx skills add ./path/to/followthrough-dev-skill
```

## What It Creates in Your Project

```text
your-project/
├── AGENTS.md                        # Short persistence guardrail across long sessions
└── docs/
    ├── SPEC.md                      # Finalized idea/spec (or adopts your existing spec file)
    ├── ARCHITECTURE.md              # System-level architecture, stack, APIs, design decisions
    ├── FOLLOWTHROUGH_PLAN.md        # Phased [ ] / [x] checklist with incremental testable tasks
    ├── ACTION_LOG.md                # Chronological log keyed by Action ID (P.T.S)
    └── codebase/
        ├── phase-00-setup.md        # Phase learning guide (Architectural Layman + Technical)
        └── phase-01-feasibility.md
```

## Example Prompts

- _"Start a new project using followthrough-dev. Here is my rough idea: ..."_
- _"Initialize the followthrough workflow from `docs/PROJECT_PLAN.md` (a comprehensive document detailing your project's architecture, design decisions, key features and how they work, and tech stack—starting with a clear, well-defined plan is recommended for workflow initialization)."_
- _"Do Task 1.2."_
- _"Fix the validation error in Task 1.2 and update the docs."_
- _"Run Phase 2."_
- _"Wrap up Phase 1."_
