# Confidence thresholds

Assign each suggested skill an internal **score** from **0.0–1.0**, then map to a user-facing label. Scores are relative to the current user message and immediate context, not global truth.

## Labels

| Label | Score range | Meaning |
|-------|-------------|---------|
| **high** | 0.75–1.00 | Clear keyword or workflow match; likely needed soon. |
| **medium** | 0.50–0.74 | Plausible adjacent or second-phase need; worth mentioning. |
| **maybe** | 0.30–0.49 | Weak signal; include only if standard verbosity allows and anti-rules do not block. |
| *(omit)* | below 0.30 | Do not surface unless the user explicitly asked for an exhaustive sweep. |

## Tie-breakers

When two skills score within **0.05** of each other:

1. Prefer the skill whose **primary** triggers (per skill-index) matched explicit user terms.
2. Prefer the skill not blocked by **anti-skill-rules**.
3. Prefer the skill earlier in a documented **chain** when both are on the same path.

## Calibration

- **High** should be rare enough that the top **1–2** are obviously right, not everything ranked high.
- If everything scores medium, re-check signals: you may be over-broad; narrow to the stated deliverable.
