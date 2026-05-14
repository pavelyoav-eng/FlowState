# Anti-skill rules

Explicit **do not suggest** and **deprioritize** rules. Every skill named below must exist as a `##` heading in `references/skill-index.md`. If a rule matches, drop the skill or move it below unless the user asked for it by name.

## Hard exclusions (do not suggest)

| Context signal | Do not suggest |
|----------------|----------------|
| User wants a **single one-line answer** (definition, trivia, math) | kubernetes, microservices, infrastructure-as-code, system-design, compliance, data-pipeline |
| **No software project** (pure chat, creative writing, non-code life advice) | ci-cd, docker, kubernetes, deployment, database-migration, api-design |
| **No repository / codebase** in scope (theory only) | git-workflow, pr-management, monorepo, ci-cd, deployment, database-migration |
| User said **do not change files** / **advice only** | database-migration, deployment, linting-formatting, code-generation |
| **Homework-style** “explain this concept” with no build | e2e-testing, load-testing, kubernetes, infrastructure-as-code |

## Soft exclusions (deprioritize or one line only)

| Context signal | Behavior |
|----------------|----------|
| **Toy / hello-world** scope | kubernetes, microservices, load-testing, compliance, tracing |
| **Single small bugfix** in one file | system-design, monorepo, data-pipeline, edge-computing |
| Pivot to **narrower** scope | Strip secondaries (e.g. monitoring, load-testing) unless still relevant |
| User only needs **static copy** (no app) | server-setup, api-integration, deployment, kubernetes |

## Confusion pairs

When two skills score close, prefer the tighter match:

- **docker** vs **kubernetes**: `docker` for container images and compose; `kubernetes` when orchestration, clusters, or helm are explicit.
- **api-design** vs **api-integration**: `api-design` for contracts and new surface area; `api-integration` for consuming or wiring existing HTTP APIs.
- **unit-testing** vs **integration-testing** vs **e2e-testing**: unit for isolated modules; integration for cross-layer or service boundaries; e2e for full browser or user flows.
- **monitoring** vs **logging** vs **error-tracking**: `monitoring` for metrics/dashboards; `logging` for log pipelines; `error-tracking` when Sentry-like tools or crash triage dominate.
- **database-design** vs **orm-setup**: `database-design` for schema and modeling; `orm-setup` when the ORM layer itself is the task.
- **pr-management** vs **code-review**: `pr-management` for merge health, CI on the branch, conflicts; `code-review` for review process and feedback quality.
- **reporting** vs **data-visualization**: `reporting` for document-style outputs (often pdf/xlsx); `data-visualization` for charts and dashboards in-app.
- **security-audit** vs **dependency-management**: `security-audit` for vuln review and config; `dependency-management` for npm audit, lockfiles, CVE bumps.
- **create-skill** vs **create-rule**: `create-skill` for packaged SKILL-style workflows; `create-rule` for repo-wide persistent rules and standards.

When in doubt, prefer **fewer** suggestions with **higher** average confidence.
