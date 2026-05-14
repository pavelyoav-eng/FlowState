# Verbosity modes

FlowState responses MUST follow one of these modes. Default to **standard** unless the user asks for brevity or the session is already crowded (e.g. long pasted logs).

## Compact

Use when:

- The user asks for *short*, *quick*, *TL;DR*, or *just the list*.
- There are more than six plausible skills; compact avoids overload.

Rules:

- At most **5** skills listed (fewer if fewer match).
- One line per skill: `name — reason` (no sub-bullets).
- Omit **maybe** tier unless exactly one *maybe* prevents a obvious mistake later; if included, max one line.
- No preamble longer than **one short sentence**; no repeated restatement of the user goal.

## Standard

Use by default.

Rules:

- At most **7** skills listed.
- One line per skill with optional **confidence word** in parentheses when helpful: *(high)*, *(medium)*, *(maybe)* — only if `confidence-thresholds.md` was applied.
- **One** short intro sentence (what you inferred).
- **One** closing line: offer to start with the top skill or ask a single clarifying question if intent is ambiguous.

Do not switch modes mid-reply; pick one for the whole message.
