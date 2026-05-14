# Skill chains

Sequencing rules: when multiple skills apply, **order** recommendations so the first item unblocks the rest. Chains are hints, not strict dependencies.

## Default ordering principles

1. **Migrate before authoring** — convert old rules and commands to skills before building new ones from scratch.
2. **Author before enforce** — write the skill or subagent before adding the rule or hook that governs it.
3. **Split before maintaining** — break a large changeset into PRs before entering the merge-maintenance loop.

## Documented chains

| After / during | Often next | Notes |
|----------------|------------|--------|
| `migrate-to-skills` | `create-skill` | Converted rules often need a proper SKILL.md pass to add frontmatter and trigger logic. |
| `create-skill` | `create-hook` | Skills frequently need a hook to fire automatically on agent events. |
| `create-skill` | `create-rule` | When the skill's behavior should also be enforced as a repo-wide coding rule. |
| `create-subagent` | `create-skill` | A subagent persona is most useful when paired with a skill that invokes it. |
| `split-to-prs` | `babysit` | Once branches are opened, each needs triaging until merged. |
| `update-cursor-settings` | `update-cli-config` | IDE settings and CLI config are often adjusted together when onboarding or reconfiguring Cursor. |
| `statusline` | `update-cli-config` | Statusline is configured inside cli-config.json; the two skills share the same file. |

## Bundles (same message)

When the user describes a Cursor setup or onboarding session, present related skills as a natural sequence rather than isolated items:

- **Cursor meta-setup:** `update-cursor-settings` → `update-cli-config` → `statusline`
- **Skills authoring flow:** `migrate-to-skills` → `create-skill` → `create-hook`
- **PR lifecycle:** `split-to-prs` → `babysit`

Do not chain skills that **anti-skill-rules** forbids for the stated context.
