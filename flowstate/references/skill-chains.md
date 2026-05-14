# Skill chains

Sequencing rules: when multiple skills apply, **order** recommendations so the first item unblocks the rest. Chains are hints, not strict dependencies. Every skill id below must match a `##` heading in `references/skill-index.md`.

## Default ordering principles

1. **Schema before persistence** — `database-design` before `orm-setup` and `database-migration` when the data model is still moving.
2. **Test pyramid** — favor `unit-testing` before `integration-testing` before `e2e-testing` when the user is standing up coverage.
3. **Images before orchestration** — `docker` before `kubernetes` when both apply.
4. **API contract before consumers** — `api-design` before `api-integration` when building a new surface.

## Documented chains

Pairs align with `Chains to` fields in the index and common follow-ons:

| After / during | Often next | Notes |
|----------------|------------|--------|
| `xlsx` | `docx` | Tabular data into narrative docs. |
| `docx` | `pdf` | Final formatted artifact. |
| `xlsx` | `pdf` | When PDF is the only stated output (skip docx). |
| `file-reading` | `xlsx`, `docx`, `pdf-reading` | Uploaded files routed by type. |
| `reporting` | `pdf`, `xlsx` | Report output formats from the index. |
| `database-design` | `database-migration` | Schema stable enough to migrate. |
| `orm-setup` | `database-queries` | ORM in place, then query work. |
| `server-setup` | `api-design` | Server scaffold then API surface. |
| `unit-testing` | `integration-testing` | Pyramid ordering. |
| `integration-testing` | `e2e-testing` | Broader coverage after layers hold. |
| `docker` | `kubernetes` | Container images before cluster rollout. |
| `ci-cd` | `deployment` | Green pipeline then promote. |
| `create-skill` | `create-rule` | Packaged workflow plus repo standards when both matter. |

## Bundles (same message)

Use when the user describes an end-to-end flow in one breath:

- **Office / documents:** `xlsx` → `docx` → `pdf`
- **Test and ship:** `unit-testing` → `integration-testing` → `e2e-testing` → `ci-cd`
- **Data to report:** `data-cleaning` → `reporting` → `pdf` (or `xlsx` when spreadsheet is the deliverable)
- **DB lifecycle:** `database-design` → `orm-setup` → `database-queries` → `database-migration` → `deployment`
- **Cloud path:** `docker` → `kubernetes` → `monitoring`
- **Security hardening:** `security-audit` → `dependency-management` → `secrets-management`
- **Frontend stack:** `react-component` → `frontend-design` → `accessibility` (when UI and a11y are both in scope)

Do not chain skills that **anti-skill-rules** forbids for the stated context.
