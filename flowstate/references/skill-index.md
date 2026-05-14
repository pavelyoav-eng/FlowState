# Skill index

Catalog of skills FlowState may recommend. Extend by appending a new `##` section using the template at the bottom.

Fields:

- **What it does** — one sentence.
- **Keywords** — comma-separated triggers (tools, file types, verbs).
- **Chains to** — optional list of skill names that often follow (see `skill-chains.md`).
- **Anti** — optional pointer to `anti-skill-rules.md` anchor if exclusions are non-obvious.

---

## xlsx

- **What it does:** Reads and transforms spreadsheet data in Excel-compatible formats.
- **Keywords:** excel, xlsx, xls, csv export, spreadsheet, workbook, pivot, sheet
- **Chains to:** docx, pdf
- **Priority hint:** primary when tabular ingestion is explicit

## docx

- **What it does:** Drafts or edits structured documents in Word-compatible formats.
- **Keywords:** docx, word, report, memo, template, styles, track changes
- **Chains to:** pdf
- **Priority hint:** primary when narrative or formatted doc output is explicit

## pdf

- **What it does:** Generates, merges, splits, or extracts from PDFs.
- **Keywords:** pdf, print, export, forms, merge, split, extract
- **Chains to:** —
- **Priority hint:** primary when final artifact must be PDF

## explore-codebase

- **What it does:** Read-only mapping of a repository before edits or refactors.
- **Keywords:** unfamiliar codebase, where is, how does X work, architecture, find usages
- **Chains to:** implement-feature, refactor
- **Priority hint:** primary at session start on existing repos

## implement-feature

- **What it does:** Implements or extends application behavior across files.
- **Keywords:** add feature, implement, build, wire up, endpoint, component
- **Chains to:** tests, ci-fix
- **Priority hint:** primary after intent and boundaries are clear

## ci-fix

- **What it does:** Diagnoses and repairs failing pipelines, lints, or build errors.
- **Keywords:** CI, GitHub Actions, failing build, lint error, test failure, red pipeline
- **Chains to:** babysit-pr
- **Priority hint:** primary when logs or CI output are pasted

## babysit-pr

- **What it does:** Keeps a PR merge-ready via review comments, conflicts, and CI loops.
- **Keywords:** PR, merge, review comments, rebase, conflict, merge-ready
- **Chains to:** —
- **Priority hint:** primary when the user is in PR maintenance mode, not greenfield

## create-rule

- **What it does:** Adds or edits Cursor project rules for persistent AI guidance.
- **Keywords:** .cursor/rules, AGENTS.md, coding standards, project conventions
- **Chains to:** —
- **Priority hint:** primary when the user wants policy encoded for the repo

## create-skill

- **What it does:** Authors Cursor Agent Skills (SKILL.md structure, discovery text).
- **Keywords:** new skill, SKILL.md, agent skill, hook discovery
- **Chains to:** create-rule
- **Priority hint:** primary when building reusable agent behavior

---

### Template for new skills

```markdown
## skill-name

- **What it does:** …
- **Keywords:** …
- **Chains to:** skill-a, skill-b
- **Priority hint:** primary | secondary
```
