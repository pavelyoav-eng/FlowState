# Skill index

Catalog of skills FlowState may recommend. Extend by appending a new `##` section using the template at the bottom.

Fields:

- **What it does** — one sentence.
- **Keywords** — comma-separated triggers (tools, file types, verbs, phrases).
- **Chains to** — optional list of skill names that often follow (see `skill-chains.md`).
- **Priority hint** — when this skill should be ranked primary vs secondary.

---

## babysit

- **What it does:** Keeps an open PR merge-ready by triaging review comments, resolving clear conflicts, and fixing CI in a loop.
- **Keywords:** PR, pull request, merge-ready, review comments, CI failing on branch, rebase conflict, Bugbot, green CI, unresolved threads
- **Chains to:** —
- **Priority hint:** primary when an open PR is the main subject and it is failing or has unresolved feedback

## create-hook

- **What it does:** Creates Cursor hooks — scripts or prompt-based checks that run before or after agent events.
- **Keywords:** hook, hooks.json, before agent, after agent, block action, observe, audit, automate behavior, stdin stdout, agent event
- **Chains to:** create-rule
- **Priority hint:** primary when the user wants to automate reactions to agent actions

## create-rule

- **What it does:** Adds or edits Cursor project rules for persistent AI guidance.
- **Keywords:** .cursor/rules, AGENTS.md, coding standards, project conventions, rule, always apply, file-specific pattern, mdc
- **Chains to:** —
- **Priority hint:** primary when the user wants policy or standards encoded for the repo

## create-skill

- **What it does:** Authors Cursor Agent Skills (SKILL.md structure, frontmatter, discovery text, trigger scenarios).
- **Keywords:** new skill, SKILL.md, agent skill, skill authoring, reusable workflow, skill directory
- **Chains to:** create-hook, create-rule
- **Priority hint:** primary when building packaged, reusable agent behavior

## create-subagent

- **What it does:** Configures custom subagents — specialized AI assistants with isolated context and custom system prompts.
- **Keywords:** subagent, custom agent, specialized AI, isolated context, code reviewer agent, debugger agent, domain-specific assistant
- **Chains to:** create-skill
- **Priority hint:** primary when the user needs a persistent specialized AI persona rather than a one-off skill

## migrate-to-skills

- **What it does:** Converts "Applied intelligently" Cursor rules (.mdc) and slash commands (.md) to Agent Skills format (.cursor/skills/).
- **Keywords:** migrate, convert rules, .mdc, slash commands, commands to skills, consolidate, SKILL.md format
- **Chains to:** create-skill
- **Priority hint:** primary when the user has existing rules or commands they want to promote to skills

## sdk

- **What it does:** Guides building apps, scripts, CI pipelines, or automations against the Cursor TypeScript SDK (`@cursor/sdk`).
- **Keywords:** @cursor/sdk, Cursor SDK, Agent.create, Agent.prompt, Agent.resume, agent.send, run.stream, CursorAgentError, programmatic agent, CI pipeline agent, cloud runtime, local runtime, v1/agents
- **Chains to:** —
- **Priority hint:** primary when the user is writing code that calls the Cursor SDK outside the IDE

## split-to-prs

- **What it does:** Splits accumulated work into small, reviewable pull requests.
- **Keywords:** split PR, split changes, too many changes, big diff, reviewable, stacked PRs, branch per feature, split branch
- **Chains to:** babysit
- **Priority hint:** primary when the user has a large or mixed-intent changeset and wants to ship it incrementally

## statusline

- **What it does:** Configures a custom status line rendered above the CLI prompt, fed by a user-supplied command.
- **Keywords:** status line, statusline, statusLine, CLI status bar, prompt footer, session context, cli-config statusLine
- **Chains to:** update-cli-config
- **Priority hint:** primary when the user mentions customizing the CLI prompt area or session display

## update-cli-config

- **What it does:** Views and modifies Cursor CLI settings in `~/.cursor/cli-config.json`.
- **Keywords:** CLI config, cli-config.json, approval mode, vim mode, sandbox, permissions, display options, CLI preferences
- **Chains to:** —
- **Priority hint:** primary when the user wants to change CLI-level behavior or preferences

## update-cursor-settings

- **What it does:** Modifies Cursor/VSCode user settings in `settings.json`.
- **Keywords:** settings.json, editor settings, theme, font size, tab size, format on save, auto save, keybindings, VSCode settings, Cursor preferences
- **Chains to:** update-cli-config
- **Priority hint:** primary when the user wants to change IDE-level editor behavior

---

### Template for new skills

```markdown
## skill-name

- **What it does:** …
- **Keywords:** …
- **Chains to:** skill-a, skill-b
- **Priority hint:** primary | secondary
```
