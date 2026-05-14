---
name: flowstate
description: >-
  Onboarding layer that maps the user's opening intent to relevant agent skills
  before work begins. Use when the user describes a new project, multi-step
  workflow, file-heavy setup, or asks which skills apply; also when re-evaluating
  mid-session after a major pivot. Reads references/skill-index.md and applies
  config/confidence-thresholds.md and config/verbosity.md.
---

# FlowState

Orchestrate skill discovery: interpret intent, score candidates, respect chains and anti-rules, then output a ranked, explainable list — and offer to fetch and install any missing skills with user approval.

## When This Skill Applies

Activate when any of these are true:

- The user opens with **project framing** (*I'm building…*, *I want to create…*, *Help me set up…*).
- They describe a **multi-step workflow** across tools, file types, or domains.
- They **upload several files** at session start, signaling a non-trivial scope.
- They explicitly ask **what skills** or **what to enable** for a task.
- The conversation **pivots** materially (new goal, stack, or deliverable); re-run the mapping lightly (see **Mid-session pivot**).

Stay quiet for single-step, fully scoped requests where skill routing adds no value.

## Operating Procedure

1. **Load config** (do not show raw config to the user unless they ask):
   - `config/verbosity.md` — set response shape.
   - `config/confidence-thresholds.md` — label each suggestion high / medium / maybe.

2. **Extract signals** from the latest user message (and short thread context if needed):
   - Nouns: languages, frameworks, file types, hosts (CI, cloud), artifacts (PDF, Excel).
   - Verbs: migrate, scaffold, review, deploy, debug, split PRs, etc.
   - Constraints: deadline, repo layout, team rules, readonly / no network.

3. **Match** against `references/skill-index.md`:
   - Primary: direct keyword or workflow overlap.
   - Secondary: adjacent skills that often follow (see `skill-chains.md`).

4. **Filter** with `references/anti-skill-rules.md`:
   - Drop skills that are explicitly ruled out for this context.
   - If two skills compete, prefer the one with clearer task overlap and fewer anti-rule conflicts.

5. **Order** using `references/skill-chains.md`:
   - If skill B typically follows skill A for this workflow, list A before B and optionally note *then* B in one line.

6. **Score and label** each remaining skill using confidence bands from `confidence-thresholds.md`.

7. **Emit** in the shape required by `verbosity.md`:
   - Every listed skill gets a **one-line reason** tied to the user's wording.
   - End with a **non-blocking** question or invitation (e.g. whether to start with the top pick), not a hard gate.

8. **Offer to fetch missing skills:**
   - After emitting the list, check which recommended skills do **not** already exist locally as SKILL.md files.
   - For each missing skill, search the web using the query: `"<skill-name>" SKILL.md cursor agent skill`
   - Present the best match per skill to the user: name, source URL, and a one-line description of what was found.
   - Ask for approval **once** across all missing skills (not one prompt per skill).
   - On approval: write each fetched SKILL.md to `/skills/<skill-name>/SKILL.md`. Do not overwrite skills that already exist unless the user explicitly asks.
   - On rejection: continue without installing; the user can ask later.
   - If no match is found for a skill after searching, note it honestly: *"Couldn't find a public SKILL.md for `<skill-name>` — you may need to build it."*

## Mid-session Pivot

If the user changes goal, stack, or deliverable in a way that invalidates earlier assumptions:

- Re-scan signals from the **pivot message**; do not assume earlier skills still apply.
- Demote or remove skills that **anti-skill-rules** or the new goal rule out.
- Prefer a **short delta** (what changed in recommendations) unless verbosity is *compact* and the pivot is small.
- Re-run Step 8 for any newly recommended skills that are not yet installed.

## Quality Bar

| Principle | Enforcement |
|-----------|-------------|
| Low friction | Cap list length per verbosity mode; no walls of text. |
| Ranked | Highest confidence first; optional *maybe* row only if useful. |
| Explainable | Each line ties to a user signal, not generic praise. |
| Non-blocking | User can ignore suggestions and continue. |
| Forward-looking | Include one secondary only when it clearly saves a later step. |
| Honest gaps | If a skill can't be found or installed, say so clearly. |

## File Map

| Path | Role |
|------|------|
| `config/verbosity.md` | Output length and structure. |
| `config/confidence-thresholds.md` | Score → label mapping. |
| `references/skill-index.md` | Canonical skill catalog and keywords. |
| `references/skill-chains.md` | Sequencing and bundles. |
| `references/anti-skill-rules.md` | Exclusions and de-prioritization. |
| `templates/quickstart-prompt.md` | Optional paste-in for users who want a standard opener. |
| `evals/trigger-cases.md` / `pivot-cases.md` | Regression-style scenarios for humans or automation. |