# Guided Execution Mode Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Make Guided Execution Mode the default Day interaction protocol so `开始 Day N` starts a short brief and one guided step instead of dumping a complete Markdown task list.

**Architecture:** Extend the existing root-level `CONTENT_PRODUCTION_LOOP.md` with a higher-priority Guided Execution Mode section and keep the existing content-processing rules below it. Add a concise README pointer explaining that conversation is the execution entry and Markdown is maintained in the background. Do not edit the daily plan files.

**Tech Stack:** Markdown documentation, Git, PowerShell read-only validation commands.

## Global Constraints

- Guided Execution Mode takes priority over the previous one-shot Day Markdown presentation.
- Each interaction advances one real step only and waits for the user response.
- Information requests use directly answerable templates; operational requests use at most 1–3 related commands.
- Codex checks results and maintains project Markdown automatically.
- Must and Optional are distinguished for every step; capture reminders are embedded at the point of need.
- Content Processing happens after the core experiment, not during every execution step.
- Preserve `daily/day-01.md` through `daily/day-07.md` as backend plan/record templates.
- Do not start Day 1, modify Day 1–7 files, or generate Day 8–14.

---

### Task 1: Add Guided Execution Mode to the long-term operating rules

**Files:**
- Modify: `CONTENT_PRODUCTION_LOOP.md`

**Interfaces:**
- Consumes: Existing Daily Content Production Loop, capture rules, safety rules, publishing decisions, project-record rules, and trigger protocols.
- Produces: A higher-priority guided interaction protocol that governs future `开始 Day N` conversations.

- [ ] **Step 1: Add the Guided Execution Mode priority statement**

Insert a section before the existing trigger protocol stating that Guided Execution Mode supersedes one-shot full-Markdown Day output. Define the division of responsibility: conversation is the execution entry, Markdown is the backend record, and the user answers, operates, experiments, captures, and reports while Codex checks and updates.

- [ ] **Step 2: Define Phase 0 Brief and Phase 1 single-step interaction**

Specify that `开始 Day N` first gives the final goal, why it matters, and the number of stages, then immediately starts Step 1. Define the exact Step format with Step name, Purpose, What you do now, Reply with, Must/Optional, and Capture.

- [ ] **Step 3: Define direct-answer templates and bounded operations**

Require copyable response templates for facts such as budget, time, hardware, and constraints. For environment/configuration tasks, require explicit PowerShell or application actions and limit each message to 1–3 related operations until the user replies.

- [ ] **Step 4: Define Phase 2 Verify and automatic Markdown maintenance**

After each response, require checking sufficiency, identifying contradictions, deciding success, updating all relevant project Markdown, reporting what was recorded, and only then moving to the next step. State that the user should not duplicate facts across files.

- [ ] **Step 5: Define dynamic route changes and Must/Optional boundaries**

State that real execution results override the plan; incompatibility, unexpected success/failure, or new evidence can change the day’s route. Require each step to distinguish Must from Optional and prohibit long command batches that depend on unverified earlier results.

- [ ] **Step 6: Embed capture reminders and defer content production**

Require capture prompts immediately before the relevant action or milestone, with a readiness confirmation when needed. During execution, only request evidence/data capture; defer titles, covers, blog posts, and full scripts to Content Processing after core work.

- [ ] **Step 7: Define Day Acceptance, Content Processing, and Close**

After the core task, require completion/partial-completion status, missing work, reasons, and real assets before Personal Blog, Social Media, Portfolio, and SEO Opportunity decisions. Close with project progress, automatically updated files, and the next starting point, without auto-generating Day N+1.

- [ ] **Step 8: Replace the old trigger wording with the new precedence rule**

Retain the original content and publishing rules, but make the `开始 Day N` trigger explicitly say: brief first, Step 1 immediately, one step per turn, verify before advancing, and no full Day Markdown dump at startup. Keep `Day N 完成` as the post-experiment processing trigger.

- [ ] **Step 9: Validate the long-term rules**

Run:

```powershell
rg -n "Guided Execution Mode|Phase 0|Phase 1|Phase 2|Phase 3|Phase 4|Phase 5|一次只推进一个|1–3|Must|Optional|自动更新|Content Processing|不要自动生成 Day N\+1|不在开场一次性输出" CONTENT_PRODUCTION_LOOP.md
```

Expected: Priority, phases, single-step behavior, bounded operations, automatic updates, capture timing, deferred content processing, and close behavior are all present.

---

### Task 2: Add the guided-mode entry to README

**Files:**
- Modify: `README.md`

**Interfaces:**
- Consumes: Existing project navigation, Daily Content Production Loop link, Desktop AI Assistant positioning, and backend-record boundary.
- Produces: A short discoverable statement that the conversation, not manual Markdown editing, is the execution entry.

- [ ] **Step 1: Add Guided Execution Mode to the navigation or long-term rules entry**

Update the existing content-loop README entry to mention Guided Execution Mode and its one-step-at-a-time behavior.

- [ ] **Step 2: Add the conversation/backend distinction**

State that the user’s role is to answer, operate, experiment, capture evidence, and report results, while Codex maintains project Markdown in the background. Preserve the existing Personal Build Log and SEO Website distinction.

- [ ] **Step 3: Validate the README entry**

Run:

```powershell
rg -n "Guided Execution Mode|CONTENT_PRODUCTION_LOOP|对话|后台|Markdown|Personal Build Log|SEO Website|Developer Experience|Portfolio" README.md
```

Expected: README points to the guided protocol and preserves all existing project boundaries.

---

### Task 3: Verify preservation and deliver the requested summary

**Files:**
- Verify: `CONTENT_PRODUCTION_LOOP.md`
- Verify: `README.md`
- Verify unchanged: `daily/day-01.md`
- Verify unchanged: `daily/day-02.md`
- Verify unchanged: `daily/day-03.md`
- Verify unchanged: `daily/day-04.md`
- Verify unchanged: `daily/day-05.md`
- Verify unchanged: `daily/day-06.md`
- Verify unchanged: `daily/day-07.md`
- Verify unchanged: `ROADMAP.md`
- Verify unchanged: `developer-experience/`
- Verify unchanged: `portfolio/`

**Interfaces:**
- Consumes: The guided rules and README entry.
- Produces: Evidence that only the intended long-term documentation changed and the user-facing delivery requirements are satisfied.

- [ ] **Step 1: Check whitespace and current working-tree scope**

Run:

```powershell
git diff --check
git status --short
```

Expected: No whitespace errors. Account for any pre-existing uncommitted work from the earlier Desktop AI Assistant narrative upgrade; do not overwrite or revert it.

- [ ] **Step 2: Check that daily files remain exactly Day 1–7**

Run:

```powershell
Get-ChildItem daily -Filter 'day-*.md' | Sort-Object Name | Select-Object -ExpandProperty Name
```

Expected: Only `day-01.md` through `day-07.md` are present.

- [ ] **Step 3: Check that existing daily Content Ideas remain**

Run:

```powershell
$rows = 1..7 | ForEach-Object { $p = ('daily/day-{0:00}.md' -f $_); [pscustomobject]@{File=$p; ContentIdea=[bool](Select-String -Path $p -Pattern '^## Content Idea of the Day$')} }; $rows | Format-Table; if (($rows | Where-Object { -not $_.ContentIdea }).Count -eq 0) { 'Day 1–7 Content Idea preservation check: PASS' }
```

Expected: All seven files still contain `Content Idea of the Day`.

- [ ] **Step 4: Confirm no execution was started**

Run:

```powershell
rg -n "^### Step 1：|开始 Day 1|Today's Capture List" daily/day-01.md
```

Expected: This implementation adds no live execution results or new execution log to Day 1; the file remains a plan/template.

- [ ] **Step 5: Report and stop**

Report: the file containing Guided Execution Mode, the new `开始 Day N` flow, Markdown automatically maintained by Codex, preservation of Day 1–7, and that Day 1 and Day 8–14 were not started/generated. Do not start Day 1 in the same turn.

