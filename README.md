# 🌊 FlowState
 
> A Claude skill that reads what you're building and lines up the right skills before you start.
 
---
 
## What It Does
 
FlowState acts as a **project onboarding layer** for Claude. When you describe what you're about to work on, it scans your intent and surfaces the skills most relevant to your project — so you're not discovering mid-task that a skill exists that would have saved you time.
 
It analyzes your prompt, maps it to the available skill library, and returns a ranked list of what you'll likely need — with a one-line explanation of when each skill will come into play.
 
---
 
## When It Triggers
 
FlowState activates when:
 
- You open with a **project description** — *"I'm building...", "I want to create...", "Help me set up..."*
- You describe a **multi-step workflow** that spans multiple file types or tools
- You explicitly ask — *"what skills do I need for X?"*
- You upload files at the start of a session, signaling a file-heavy workflow
It stays silent when your request is simple or single-step — it's not meant to interrupt, only to help you plan.
 
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
flowstate/
├── README.md               # This file
├── SKILL.md                # Core skill logic and trigger instructions
└── references/
    └── skill-index.md      # Catalog of available skills with keywords and descriptions
```
 
---
 
## How It Works
 
1. **Parses intent** — reads the user's opening prompt for signals: file types mentioned, tools implied, workflow steps described
2. **Cross-references the skill index** — matches signals against `references/skill-index.md`
3. **Ranks by relevance** — skills that map directly to the task come first; adjacent/optional ones are flagged as secondary
4. **Explains briefly** — each suggestion includes a one-line reason so the user understands *why* it's being recommended
5. **Moves on** — doesn't block the conversation; the user can accept, ignore, or ask for more detail
---
 
## Extending FlowState
 
To add a new skill to the suggestion pool, add an entry to `references/skill-index.md`:
 
```md
## skill-name
- **What it does:** One sentence description
- **Suggests when:** Keywords or contexts that should trigger this as a recommendation
- **Priority:** primary | secondary
```
 
---
 
## Design Principles
 
| Principle | What it means in practice |
|---|---|
| **Low friction** | Suggestions appear in a few lines, never a wall of text |
| **Ranked, not exhaustive** | Only surfaces skills that are genuinely relevant to the task |
| **Explainable** | Every suggestion includes a reason |
| **Non-blocking** | If nothing is relevant, FlowState stays quiet |
| **Forward-looking** | Thinks about what you'll need 3 steps ahead, not just right now |
 
---
 
## Status
 
- [ ] `SKILL.md` — core skill logic
- [ ] `references/skill-index.md` — skill catalog
- [ ] Trigger optimization
- [ ] Eval set
---
 
*Built as a Claude skill. Part of the skills ecosystem.*
