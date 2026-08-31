# Daily Content Production Loop Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add a durable daily content-production and evidence loop to the existing Embodied AI FieldLab without changing its Roadmap, Day 2–7 plans, Developer Experience structure, or Portfolio structure.

**Architecture:** Store the complete operating rules in a new root-level `CONTENT_PRODUCTION_LOOP.md`. Add only a short entry point and the two-site boundary to `README.md`, and add only the required pre-experiment capture/real-results handoff to `daily/day-01.md`. Existing `Content Idea of the Day` sections remain as pre-experiment plans and can be replaced by evidence after execution.

**Tech Stack:** Markdown documentation, Git, PowerShell read-only validation commands.

## Global Constraints

- The full rules live in `CONTENT_PRODUCTION_LOOP.md`.
- Personal Build Log belongs to the Desktop AI Assistant project; Embodied AI SEO Website belongs to a separate project.
- Every Day begins with tasks plus a Today's Capture List and ends with a reality-based publishing decision.
- `Content Idea of the Day` remains and is explicitly a pre-experiment plan, never a fixed final story.
- Safety and truthfulness override content capture and publishing.
- Do not rewrite Roadmap, Day 2–7, Developer Experience, or Portfolio core structure.
- Do not generate Day 8–14.
- Do not execute SEO strategy; only mark qualified SEO Website Content Opportunities.

---

### Task 1: Add the complete Daily Content Production Loop rules

**Files:**
- Create: `CONTENT_PRODUCTION_LOOP.md`

**Interfaces:**
- Consumes: Existing Desktop AI Assistant narrative, candidate-task research boundary, Day 1–7 content cards, Developer Experience workflow, Portfolio Case Studies, and SEO boundary.
- Produces: The long-term operating contract for starting a Day, capturing evidence, reporting reality, deciding publication, and updating project records.

- [ ] **Step 1: Add the end-to-end daily workflow**

Document this sequence: `开始 Day N → Codex 输出当天任务 → Codex 输出 Today's Capture List → 用户执行真实实验 → 用户汇报真实结果 → Codex 更新项目记录 → Personal Blog 判断 → Social Media 判断 → Publishing Pack → Portfolio Evidence → SEO Website Content Opportunity 标记`.

- [ ] **Step 2: Define the pre-experiment output and Capture List**

Specify that `开始 Day N` returns Today's Goal, core Tasks, Robot/AI Assistant Practice, Knowledge, Today's Capture List, Safety Reminder, and Definition of Done. Require the four capture groups: Must Capture, Nice to Have, Technical Evidence, and Human / Story Moments. State that the existing Content Idea is only a pre-experiment plan.

- [ ] **Step 3: Define safety, truthfulness, and missing-asset rules**

Ban dangerous re-enactments, unsafe proximity, intentionally dangerous failures, knives, glass, hot objects, liquids, and unvalidated actions near people. Ban fake firsts, simulation-as-real claims, fake purchase status, untested tutorials, hidden material failures, exaggerated outcomes, and fabricated data, success rates, feedback, or emotions. Allow only safe supplementary footage; never recreate a first event.

- [ ] **Step 4: Define post-experiment Reality Check and Project Record updates**

Require actual completed work, incomplete work, success, failure, errors, experiment result, data, time cost, unexpected events, media, feelings, Developer Pain Points, and evidence before choosing a story angle. Require updates to Daily Log, Experiment Result, Developer Experience, Progress, Assets, and Portfolio Evidence regardless of publication.

- [ ] **Step 5: Define Personal Blog and Social Media decisions**

Document Social Media S/A/B/C/Skip, including the required statement and future placement for B/C/Skip. Make Personal Blog independent from Social Media so a technical failure can be a blog post even when it is not a short video. Do not force daily publishing.

- [ ] **Step 6: Define both Publishing Packs**

For S/A social content, require Best Story Angle, a plain-language Hook, at least five title types, 3–5 cover-text options, a 30–90 second script with the specified time blocks and visual/audio/subtitle instructions, and an existing/missing Shot List. For a worthwhile Personal Blog, require titles, summary, full first-person post, media insertion points, and Verified/Observation/Hypothesis/Unverified sections.

- [ ] **Step 7: Define platform adaptation, timeline metadata, Portfolio Evidence, and SEO opportunity handling**

Explain that platform recommendations are selective, Personal Build Log is not SEO work, the separate SEO Website owns SEO strategy, and this project only records topic/value/evidence gaps for opportunities. Include Build Log metadata and Case Study 01–05 evidence examples.

- [ ] **Step 8: Define the two trigger protocols**

Specify the exact output order for `开始 Day N` and `Day N 完成，结果如下……`, including Next-Step Insight and the rule not to auto-generate Day N+1 unless explicitly requested.

- [ ] **Step 9: Validate the new rules document**

Run:

```powershell
rg -n "Daily Content Production Loop|Today's Capture List|Must Capture|Nice to Have|Technical Evidence|Human / Story Moments|Reality Check|Personal Blog|Social Media|S/A/B/C/Skip|Publishing Pack|SEO Website Content Opportunity|Portfolio Evidence|不要自动生成 Day N\+1|安全|真实性" CONTENT_PRODUCTION_LOOP.md
```

Expected: All required rule families and trigger protocols are present in the new root document.

---

### Task 2: Add a concise README entry and website boundary

**Files:**
- Modify: `README.md`

**Interfaces:**
- Consumes: Existing project positioning, content rules, directory navigation, and SEO scope boundary.
- Produces: A discoverable link to the long-term loop without duplicating the full rule set.

- [ ] **Step 1: Add the document to directory navigation**

Add `CONTENT_PRODUCTION_LOOP.md` to the README navigation with a sentence explaining that it governs daily capture, reality review, publishing decisions, and evidence updates.

- [ ] **Step 2: Clarify the Personal Build Log boundary**

State that Personal Build Log is part of the current Desktop AI Assistant project and supports Build in Public, timeline, portfolio, job evidence, technical practice, and DX records; it is not the separate SEO website and is not an SEO traffic project.

- [ ] **Step 3: Preserve existing content and SEO boundaries**

Do not remove the existing Content Idea rules, candidate-task research links, SEO exclusion, Developer Experience structure, or Portfolio structure. Point readers to the new document for the complete operational loop.

- [ ] **Step 4: Validate the README entry**

Run:

```powershell
rg -n "CONTENT_PRODUCTION_LOOP|Personal Build Log|SEO Website|SEO Strategy|Developer Experience|Portfolio" README.md
```

Expected: The new entry and two-site distinction are visible, with no duplicated full workflow or removed existing boundaries.

---

### Task 3: Make Day 1 compatible with the new capture-and-report loop

**Files:**
- Modify: `daily/day-01.md`

**Interfaces:**
- Consumes: Existing Day 1 project baseline, Desktop AI Assistant content line, compute plan, candidate-task research, and Content Idea.
- Produces: A Day 1 plan that distinguishes pre-experiment content planning from post-experiment evidence.

- [ ] **Step 1: Add the loop reference and pre-plan rule**

Link to `CONTENT_PRODUCTION_LOOP.md`. State that the existing Content Idea is an execution-before-experiment hypothesis, and that actual results can replace it after the user reports back.

- [ ] **Step 2: Add a Day 1 Today's Capture List**

Include Day 1-specific Must Capture items: workspace before changes, computer/RTX 3060 state, constraint sheet, candidate-task cards, early experiment object, and the initial observation. Include Nice to Have items such as desk closeups and user/desk framing. Include Technical Evidence such as OS/GPU/disk/camera facts, decision memo, environment baseline, and task-research file. Include Human / Story Moments such as budget shock, uncertainty, discarded idea, and the gap between software and physical assistants.

- [ ] **Step 3: Add the Day 1 Safety Reminder**

State that no robot movement is required on Day 1; do not introduce unsafe objects or film near a moving arm. Any future motion footage must follow the global safety rules.

- [ ] **Step 4: Add the Day 1 Definition of Done handoff**

Require the user to report what was actually completed, what remains blank, evidence paths, real time cost, unexpected findings, and initial Developer Pain Points. State that Codex will then update the project record and make independent Personal Blog/Social Media decisions.

- [ ] **Step 5: Preserve the original Day 1 structure**

Keep the existing goal, tasks, compute plan, Robot Practice, Knowledge, Developer Experience, Content Idea, Website Content Opportunity, Assets Created, Portfolio Value, Reflection, and Tomorrow sections. Do not add any Day 8–14 plan.

- [ ] **Step 6: Validate Day 1 structure**

Run:

```powershell
rg -n "CONTENT_PRODUCTION_LOOP|Today's Capture List|Must Capture|Nice to Have|Technical Evidence|Human / Story Moments|Safety Reminder|Definition of Done|Content Idea|Website Content Opportunity|Portfolio Value" daily/day-01.md
```

Expected: Day 1 contains the new handoff sections and all original core sections.

---

### Task 4: Cross-document verification and delivery report

**Files:**
- Verify: `CONTENT_PRODUCTION_LOOP.md`
- Verify: `README.md`
- Verify: `daily/day-01.md`
- Verify unchanged structure: `ROADMAP.md`
- Verify unchanged structure: `daily/day-02.md`
- Verify unchanged structure: `daily/day-03.md`
- Verify unchanged structure: `daily/day-04.md`
- Verify unchanged structure: `daily/day-05.md`
- Verify unchanged structure: `daily/day-06.md`
- Verify unchanged structure: `daily/day-07.md`
- Verify unchanged structure: `developer-experience/`
- Verify unchanged structure: `portfolio/`

**Interfaces:**
- Consumes: The new rule document and the two targeted integration edits.
- Produces: Evidence that the loop is complete, the existing project structure is preserved, and no future daily plan was generated.

- [ ] **Step 1: Check whitespace and changed-file scope**

Run:

```powershell
git diff --check
git status --short
```

Expected: No whitespace errors. The implementation changes are limited to `CONTENT_PRODUCTION_LOOP.md`, `README.md`, and `daily/day-01.md`; no Roadmap, Day 2–7, Developer Experience, or Portfolio file is modified.

- [ ] **Step 2: Check Day 1–7 file scope**

Run:

```powershell
Get-ChildItem daily -Filter 'day-*.md' | Sort-Object Name | Select-Object -ExpandProperty Name
```

Expected: Only the existing `day-01.md` through `day-07.md` files are present; no Day 8–14 file is created.

- [ ] **Step 3: Check required rule families**

Run:

```powershell
rg -n "开始 Day N|Day N 完成|Today's Capture List|Reality Check|Personal Blog Decision|Social Media Decision|Portfolio Evidence|SEO Website Content Opportunity|Personal Build Log|Embodied AI SEO Website" CONTENT_PRODUCTION_LOOP.md README.md daily/day-01.md
```

Expected: Both trigger protocols, capture workflow, independent publication decisions, evidence handling, and website boundary are present.

- [ ] **Step 4: Check that all seven existing Content Ideas remain**

Run:

```powershell
$rows = 1..7 | ForEach-Object { $p = ('daily/day-{0:00}.md' -f $_); [pscustomobject]@{File=$p; ContentIdea=[bool](Select-String -Path $p -Pattern '^## Content Idea of the Day$')} }; $rows | Format-Table; if (($rows | Where-Object { -not $_.ContentIdea }).Count -eq 0) { 'Content Idea preservation check: PASS' }
```

Expected: All seven daily plans retain `Content Idea of the Day`.

- [ ] **Step 5: Report the requested outputs and stop**

Report the modified files, the location of the full loop, the Personal Blog/SEO Website distinction, the outputs for both trigger phrases, the exact Day 1 changes, and that Day 8–14 was not generated. Do not propose or write the next daily plan.

