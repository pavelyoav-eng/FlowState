#  FlowState
 
> An agent skill that reads what you're building and lines up the right skills before you start (works with Claude Code, Cursor, and similar setups that load `SKILL.md`).
 
---
 
## What It Does
 
FlowState acts as a **project onboarding layer** for the agent. When you describe what you're about to work on, it scans your intent and surfaces the skills most relevant to your project — so you're not discovering mid-task that a capability you care about was never surfaced.
 
It analyzes your prompt, maps it to the available skill library, and returns a ranked list of what you'll likely need - with a one-line explanation of when each skill will come into play.
 
---
 
## When It Triggers
 
FlowState activates when:
 
- You open with a **project description** - *"I'm building...", "I want to create...", "Help me set up..."*
- You describe a **multi-step workflow** that spans multiple file types or tools
- You explicitly ask - *"what skills do I need for X?"*
- You upload files at the start of a session, signaling a file-heavy workflow
It stays silent when your request is simple or single-step - it's not meant to interrupt, only to help you plan.
 
---
 
## Example
 
**You say:**
```
I'm starting a project where I need to pull data from an Excel file,
write it up into a report, and send it out as a PDF.
```
 
**FlowState responds:**
```
Here are the skills you'll likely need for this project:
 
  📊 xlsx       — read and process your Excel data
  📝 docx       — draft and format the report content
  📄 pdf        — generate and export the final PDF
 
Want me to start with any of these?
```
 
---
 
## Project Structure
 
```
FlowState/                    # repository root (README + LICENSE live here)
├── README.md                 # This file
├── LICENSE
└── flowstate/
    ├── SKILL.md              # Core trigger logic + orchestration
    ├── config/
    │   ├── verbosity.md      # Compact vs standard response rules
    │   └── confidence-thresholds.md
    ├── references/
    │   ├── skill-index.md    # Domain-organized catalog (keywords + chains per skill)
    │   ├── skill-chains.md   # Cross-cutting sequences and bundles (ids match the index)
    │   └── anti-skill-rules.md  # When to omit or deprioritize skills (ids match the index)
    ├── templates/
    │   └── quickstart-prompt.md
    └── evals/
        ├── trigger-cases.md
        └── pivot-cases.md
```
 
---
 
## How It Works
 
1. **Parses intent** — reads the opening prompt (and pivots) for signals: file types, tools, workflow steps, constraints.
2. **Cross-references the skill index** — matches signals against `flowstate/references/skill-index.md` (only recommend skill ids that appear there as `##` headings).
3. **Applies anti-rules and chains** — filters with `anti-skill-rules.md`, orders with `skill-chains.md`, and uses per-skill `Chains to` from the index where helpful.
4. **Uses config** — response shape from `config/verbosity.md`; confidence labels from `config/confidence-thresholds.md`.
5. **Ranks by relevance** — direct matches first; secondaries when a follow-on step is likely.
6. **Explains briefly** — each line ties the skill to something the user said.
7. **Moves on** — non-blocking; user can ignore or go deeper. See `flowstate/SKILL.md` for optional steps (e.g. surfacing missing skills) if your runtime supports them.
 
---
 
## Extending FlowState
 
To add a skill to the suggestion pool, append a section to `flowstate/references/skill-index.md` under the right domain heading. Use the same shape as existing entries — and **only** use other skill ids in `Chains to` that already exist as `##` headings in that file (keeps the index, chains, and anti-rules consistent).
 
```md
## skill-name
- **What it does:** One sentence.
- **Keywords:** comma, separated, triggers
- **Chains to:** other-skill-id, another-skill-id
- **Priority hint:** primary | secondary (when to rank it first vs as a follow-on)
```
 
If you add exclusion or ordering logic, update `anti-skill-rules.md` and `skill-chains.md` so they reference the same ids.
 
---
 
## Design Principles
 
| Principle | What it means in practice |
|---|---|
| **Low friction** | Suggestions appear in a few lines, never a wall of text |
| **Ranked, not exhaustive** | Only surfaces skills that are genuinely relevant to the task |
| **Explainable** | Every suggestion includes a reason |
| **Non-blocking** | If nothing is relevant, FlowState stays quiet |
| **Forward-looking** | Thinks about what you'll need a few steps ahead, not only the first action |
| **Same vocabulary** | Index, chains, and anti-rules use the same skill ids — no orphan names |
 
---
 
## Status
 
- [x] `flowstate/SKILL.md` — core skill logic and orchestration
- [x] `flowstate/references/skill-index.md` — domain skill catalog + per-skill chains
- [x] `flowstate/references/skill-chains.md` — shared sequences and bundles
- [x] `flowstate/references/anti-skill-rules.md` — exclusions aligned to the catalog
- [x] `flowstate/config/` — verbosity and confidence bands
- [x] `flowstate/evals/` — trigger and pivot case sets
- [ ] Trigger tuning against real sessions
---
 
*Built as an agent skill. Extend the catalog in-repo; wire installed skills in your own skills directory.*
