# FlowState

> An agent skill that reads what you're building and lines up the right skills before you start.

---

## What It Does

FlowState is a project onboarding layer for your agent. Describe what you're building and it maps your intent to the skills you'll actually need, before you're three steps in and realizing something useful existed the whole time.

It reads your opening prompt, matches it against a skill catalog, ranks what fits, and tells you why each one is relevant. If a skill isn't installed locally, it offers to find and fetch it.

---

## When It Triggers

FlowState activates when:

- You open with a project description: *"I'm building...", "I want to create...", "Help me set up..."*
- You describe a workflow that touches multiple tools or file types
- You explicitly ask what skills you need for something
- You upload files at session start, signaling a non-trivial scope
- You pivot mid-session to a different goal or stack

It stays quiet for simple, single-step requests. It's not meant to interrupt, only to help you plan.

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

  xlsx       (high)   -- read and process your Excel data
  docx       (high)   -- draft and format the report content
  pdf        (high)   -- generate and export the final PDF

None of these are installed yet. Want me to find them?
```

---

## Project Structure

```
FlowState/
├── README.md
├── LICENSE
└── flowstate/
    ├── SKILL.md                      # Core trigger logic and orchestration
    ├── config/
    │   ├── verbosity.md              # Compact vs standard response rules
    │   └── confidence-thresholds.md  # Score to label mapping
    ├── references/
    │   ├── skill-index.md            # 100-skill catalog with keywords and chains
    │   ├── skill-chains.md           # Sequencing rules and bundles
    │   └── anti-skill-rules.md       # When to exclude or deprioritize a skill
    ├── templates/
    │   └── quickstart-prompt.md      # Ready-to-paste session opener
    └── evals/
        ├── trigger-cases.md          # Opening prompt test scenarios
        └── pivot-cases.md            # Mid-session pivot test scenarios
```

---

## How It Works

1. Reads your opening prompt for signals: file types, tools, verbs, constraints
2. Matches signals against the skill index
3. Applies exclusion rules and sequences the results
4. Scores each skill and labels it high, medium, or maybe
5. Outputs a short ranked list, one line per skill, with a reason tied to what you said
6. Checks which skills are missing locally and offers to fetch them with your approval

---

## Getting Started

**1. Install** -- drop the `flowstate/` folder into your project.

**2. Load it.** Add to `.cursor/rules` so it loads every session automatically:
```
Always read flowstate/SKILL.md at the start of every session.
```
Or paste this manually at the start of any session:
```
Read flowstate/SKILL.md before we start.
```

**3. Describe your project.** Talk normally. FlowState activates on its own.

**4. Review the list.** Ranked skills with confidence labels and a one-line reason each.

**5. Approve the fetch.** For missing skills it finds online, it asks once. Yes installs them, no skips them.

**6. Test it occasionally.** Grab a prompt from `evals/trigger-cases.md`, paste it into a fresh session, check the output matches the expected skills. That's your smoke test.

---

## Extending FlowState

To add a skill to the pool, add a section to `flowstate/references/skill-index.md`:

```markdown
## skill-name
- **What it does:** One sentence.
- **Keywords:** comma, separated, triggers
- **Chains to:** other-skill-id
- **Priority hint:** primary | secondary
```

Keep chain references and anti-rule references in sync with whatever ids you use in the index.

---

## Design Principles

| Principle | What it means |
|---|---|
| Low friction | A few lines, never a wall of text |
| Ranked | Only surfaces skills that are genuinely relevant |
| Explainable | Every suggestion ties back to something you said |
| Non-blocking | Ignore the suggestions and keep going if you want |
| Forward-looking | Thinks about step 3, not just step 1 |
| Honest gaps | If a skill can't be found, it says so |

---

## Status

- [x] `flowstate/SKILL.md`
- [x] `flowstate/references/skill-index.md`
- [x] `flowstate/references/skill-chains.md`
- [x] `flowstate/references/anti-skill-rules.md`
- [x] `flowstate/config/`
- [x] `flowstate/evals/`
- [ ] Trigger tuning against real sessions

---

*Built as an agent skill. Works with Claude Code, Cursor, and any setup that loads SKILL.md files.*
