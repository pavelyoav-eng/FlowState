# FlowState
 Skill Suggester — Claude Skill
A Claude skill that acts as a project onboarding assistant — when a user describes what they're about to build or work on, it analyzes their intent and recommends the most relevant skills from the available skill library before they dive in.

What It Does
When a user starts a new project or describes a task at the beginning of a conversation, this skill:

Parses their intent — understands the type of work (e.g. "I'm building a dashboard with Excel exports and a PDF report")
Maps to relevant skills — cross-references the available skill library and identifies which ones apply
Presents a prioritized list — shows the user which skills will likely be needed, in order of relevance
Explains why — briefly describes what each suggested skill does and when it will come into play during the project


When It Triggers
This skill should activate when:

A user opens with a project description ("I'm building...", "I want to create...", "Help me set up...")
A user lists a multi-step workflow that implies several tools or file types
A user asks "what skills do I need for X" explicitly
A user uploads files at the start of a session (signals a file-heavy workflow)


Example
User prompt:

"I'm starting a project where I need to read data from an Excel file, generate a report, and send it out as a PDF."

Skill response:

Here are the skills you'll likely need for this project:

📊 xlsx — for reading and processing your Excel data
📄 pdf — for generating and formatting the final PDF report
📝 docx (optional) — if you need an intermediate Word document before converting to PDF

Want me to get started with any of these?


Skill Structure
skill-suggester/
├── SKILL.md          # Core skill logic and instructions
└── references/
    └── skill-index.md  # Catalog of all available skills with trigger keywords

How to Extend It
To add a new skill to the suggestion pool, update references/skill-index.md with:

Skill name
What it does (one line)
Keywords/contexts that should trigger it as a suggestion


Design Goals

Low friction — suggestions appear naturally, not as a wall of text
Ranked, not exhaustive — only surfaces skills that are genuinely relevant
Explainable — user always knows why a skill is being suggested
Non-blocking — if no skills are relevant, it stays silent
