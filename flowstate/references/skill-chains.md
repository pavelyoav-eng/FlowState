# Skill chains

Sequencing rules: when multiple skills apply, **order** recommendations so the first item unblocks the rest. Chains are hints, not strict dependencies.

## Default ordering principles

1. **Understand before change** — exploration and indexing skills before large edits.
2. **Policy before volume** — rules and skills authoring before wide refactors, when the user asked for standards.
3. **Fix the path** — CI or build health before optional polish, when delivery is blocked.

## Documented chains

| After / during | Often next | Notes |
|----------------|------------|--------|
| explore-codebase | implement-feature | Narrow scope after map. |
| implement-feature | ci-fix | When they intend to ship and tests/CI exist. |
| xlsx | docx | Data → narrative report. |
| docx | pdf | Final distribution artifact. |
| xlsx | pdf | When PDF is the only stated output (skip docx). |
| ci-fix | babysit-pr | When the failure is on a branch with an open PR. |
| create-skill | create-rule | When the skill should enforce repo-wide behavior. |

## Bundles (same message)

When the user describes an end-to-end pipeline, you may present a **bundle** in one line:

- **Office pipeline:** xlsx → docx → pdf (respect actual steps they omitted).

Do not chain skills that **anti-skill-rules** forbids for the stated context.
