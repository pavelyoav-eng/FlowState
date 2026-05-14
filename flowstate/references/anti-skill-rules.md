# Anti-skill rules

Explicit **do not suggest** and **deprioritize** rules. If a rule matches, drop the skill or move it below *maybe* unless the user directly asked for that skill by name.

## Hard exclusions (do not suggest)

| Context signal | Do not suggest |
|----------------|----------------|
| User wants a **single one-line answer** (definition, trivia, math snippet) | explore-codebase, implement-feature, babysit-pr |
| **No repository** in scope (pure chat / theory) | ci-fix, babysit-pr, explore-codebase |
| User explicitly said **do not change files** / **advice only** | implement-feature, ci-fix (unless diagnosing read-only) |
| Trivial **rename one variable** in one file with path given | explore-codebase |
| User is **not** using Cursor / no editor integration mentioned | create-rule, create-skill (unless they are authoring skills for others) |

## Soft exclusions (deprioritize or one-line only)

| Context signal | Behavior |
|----------------|----------|
| Greenfield **hello world** with no CI mentioned | ci-fix, babysit-pr — omit unless they paste errors |
| Skill overlaps **100%** with a higher-ranked skill | Keep the sharper match only |
| Pivot **reduced** scope (e.g. from “whole app” to “fix typo”) | Remove forward-looking secondaries |

## Confusion pairs

- **babysit-pr** vs **ci-fix**: Prefer **ci-fix** when the problem is build or test logs without PR context; prefer **babysit-pr** when merge blockers and review threads dominate.
- **create-rule** vs **create-skill**: Prefer **create-rule** for repo standards; **create-skill** for packaged workflows and SKILL.md authoring.

When in doubt, prefer **fewer** suggestions with **higher** average confidence.
