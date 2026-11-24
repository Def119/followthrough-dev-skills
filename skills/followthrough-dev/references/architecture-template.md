# Reference: `docs/ARCHITECTURE.md` Template

Use this structure when creating `docs/ARCHITECTURE.md` from the user's initial project plan or spec. Update this file **only** when system-level architecture, tech stack, external APIs, data models, or major design decisions change (never for minor task-level refactors).

````markdown
# System Architecture: <Project Name>

**Last Updated:** YYYY-MM-DD  
**Source Spec:** `<path-to-initial-spec-md>`  
**Current Phase:** Phase <X>

---

## 1. System Overview & Scope

- **Core Problem:** <max 5 sentences explaining the problem this project solves>
- **Core Functionalities & Functional Requirements:**
  - **FR-1 - <Functionality Name>:** <Clear description of what the system does / expected behavior>
  - **FR-2 - <Functionality Name>:** <Clear description of what the system does / expected behavior>
  - **FR-3 - <Functionality Name>:** <Clear description of what the system does / expected behavior>
- **Out of Scope (Current Version):**
  - <Explicit exclusions or deferred functionality>

## 2. Tech Stack, Tools & Methodologies

- **Frontend / Client:** <Frameworks, UI libraries, state management>
- **Backend / Services:** <Runtime, framework, architecture style>
- **Database & Storage:** <DB engine, ORM, file/blob storage>
- **Dev & Quality Tooling:** <Package manager, linter, testing tools, CI/CD>
- **Development Methodology:** Phased incremental delivery with linear phase branching

## 3. High-Level Component Architecture

Describe major system modules, their boundaries, and how data flows between them.

```text
[Client / UI Layer] ---> [API / Controller Layer] ---> [Service / Domain Layer] ---> [Database / External APIs]
```

- **Module A (`src/...`):** Responsibility and boundary.
- **Module B (`src/...`):** Responsibility and boundary.

## 4. External APIs, Integrations & Core Data Models

- **Integrations:** <Third-party APIs, SDKs, auth providers, and how secrets/keys are isolated>
- **Core Entities / Schemas:** <High-level entities and key relationships>

## 5. System-Level Design Decisions

Track key architectural trade-offs concisely so the developer remembers _why_ the system is shaped this way.

| Decision              | Choice Made              | Why / Trade-off                                     |
| --------------------- | ------------------------ | --------------------------------------------------- |
| <e.g., Auth strategy> | <e.g., HttpOnly cookies> | <e.g., Reduces XSS token exposure vs. localStorage> |

## 6. Deployment & Environment Overview _(If In Scope)_

- **Target Environment:** <Hosting, containerization, cloud provider>
- **Key Environment Variables:** <Names only, never secrets>
````
