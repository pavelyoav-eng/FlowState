# Trigger cases

Sample **opening** prompts and **expected** FlowState behavior for manual or automated checks. Expected outputs describe shape, not exact wording.

---

## Case T1 — Project description (standard)

**Prompt:**  
I'm building an internal tool that reads roster data from Excel, merges it with a SQLite DB, and emails managers a PDF summary each Monday.

**Expected:**

- Activates FlowState.
- Suggests **xlsx** (high), **pdf** (high); **SQLite** / data skills if present in index (medium); email delivery skill if indexed (medium).
- Short intro + ranked list with one-line reasons + non-blocking closer.
- Respects **standard** verbosity caps.

---

## Case T2 — Explicit skill question

**Prompt:**  
What skills should I use to split this huge refactor into reviewable PRs?

**Expected:**

- Activates even if short (explicit ask).
- Surfaces **pr-management** and/or **git-workflow** (high); optional **monorepo** if the refactor spans packages.
- Compact or standard per user preference if stated.

---

## Case T3 — Should stay quiet

**Prompt:**  
What is the difference between `let` and `const` in JavaScript?

**Expected:**

- FlowState **does not** run a skill survey; answer directly.
- No skill list unless user asks for tooling around learning.

---

## Case T4 — CI logs pasted

**Prompt:**  
My GitHub Action fails on `npm test` with this log: [paste].

**Expected:**

- **ci-cd** (high); **pr-management** if an open PR or merge thread is in scope (medium or omit).
- Optional **unit-testing** when the failure is test-related; no unrelated heavy skills unless logs imply them.

---

## Case T5 — File upload signal

**Prompt:**  
[User attaches 4+ unrelated project files] Help me clean up this React folder structure.

**Expected:**

- Activates (multi-file + structural task).
- **react-component**, **frontend-design**, or **monorepo** ranked appropriately; reasons cite structure/folder cleanup.
