# Anti-skill rules

Explicit **do not suggest** and **deprioritize** rules. If a rule matches, drop the skill or move it below *maybe* unless the user directly asked for that skill by name.

## Hard exclusions (do not suggest)

| Context signal | Do not suggest |
|----------------|----------------|
| User wants a **single one-line answer** (definition, trivia, math snippet) | babysit, split-to-prs, create-subagent |
| **No repository** in scope (pure chat / theory) | babysit, split-to-prs |
| User explicitly said **do not change files** / **advice only** | create-rule, create-hook, create-skill (unless they are authoring for others) |
| User is **not** using Cursor / no Cursor context mentioned | update-cursor-settings, update-cli-config, statusline, create-rule, create-skill, create-hook, create-subagent |
| User wants to **run a single terminal command** | all skills except shell (which is not routed by FlowState anyway) |

## Soft exclusions (deprioritize or one-line only)

| Context signal | Behavior |
|----------------|----------|
| Greenfield first commit, no open PRs | babysit, split-to-prs — omit unless work is already large |
| Skill overlaps **100%** with a higher-ranked skill | Keep the sharper match only |
| Pivot **reduced** scope (e.g. from "whole system" to "fix one typo") | Remove forward-looking secondaries |
| User asked for **sdk** help in a non-TypeScript context | Deprioritize sdk; note the language limitation |

## Confusion pairs

When two skills score close, use these tie-breakers:

- **babysit** vs **split-to-prs**: Prefer `babysit` when an open PR is already failing or has comments. Prefer `split-to-prs` when work is not yet branched or the changeset is too broad to review as-is.
- **create-rule** vs **create-skill**: Prefer `create-rule` for repo-wide coding standards and persistent context. Prefer `create-skill` for packaged, reusable agent workflows with trigger logic.
- **create-skill** vs **create-subagent**: Prefer `create-skill` for domain logic and reusable workflows. Prefer `create-subagent` when the user needs a persistent specialized AI persona with its own isolated context.
- **update-cursor-settings** vs **update-cli-config**: Prefer `update-cursor-settings` for IDE editor behavior (themes, fonts, format-on-save). Prefer `update-cli-config` for CLI runtime behavior (approval mode, sandbox, vim mode). Suggest both only when the user is doing broad Cursor configuration.

When in doubt, prefer **fewer** suggestions with **higher** average confidence.
