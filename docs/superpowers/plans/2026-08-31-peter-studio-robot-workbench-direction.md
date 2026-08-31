# Peter Studio Robot Workbench Direction Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 将已确认的 Peter Studio 工作台叙事、机械臂主线、六足角色副线和漫画式内容语言纳入现有项目文档，同时保留开放任务调研、Day 1–7、Developer Experience、Portfolio 和 Guided Execution 结构。

**Architecture:** 采用“品牌叙事层 + 技术执行层 + 内容生产层”的最小改动方案。`README.md` 负责总定位和站点职责，`ROADMAP.md` 负责 60 天能力与双机器人分工，`CONTENT_PRODUCTION_LOOP.md` 负责视觉表达和实验后内容处理，`PROGRESS.md` 负责记录当前决策与下一步。既有 Day 1–7 只做必要的叙事对齐，不创建或展开 Day 8–14。

**Tech Stack:** Markdown、Git；使用 PowerShell 进行只读检查和文本验证。

## Global Constraints

- 机械臂必须保持为桌面 AI 助手的第一能力主线。
- 六足机器人必须保持为角色、探索和传播副线，不改写成第一阶段的主要助手执行机构。
- 具体生活任务和 Flagship Task 必须保持开放，由任务调研、评分和早期实验决定。
- Peter Studio 可以借鉴漫画式个人工作台的创作感，但必须形成原创视觉语言，不复制受保护的影视 IP 资产。
- `peterstudio.online` 负责个人制造日志和机器人工作台叙事；`bimanual.org` 负责独立的具身智能资讯与 SEO 内容。
- 保留 Developer Experience、Portfolio、Guided Execution 和现有 Day 1–7 文件。
- 不生成或修改 Day 8–14。
- 不实现网站页面、不部署网站、不购买硬件。
- 只修改与本设计直接相关的文档；保留当前工作树中其他已有修改。

---

### Task 1: Update project identity and site boundaries

**Files:**
- Modify: `README.md` — 更新项目开场叙事、机器人分工、Peter Studio 与 bimanual.org 的职责边界、目录说明和当前阶段产出。

**Interfaces:**
- Consumes: `docs/superpowers/specs/2026-08-31-peter-studio-robot-workbench-direction-design.md` 中的已确认方向。
- Produces: 项目首页能够用一段话说明 Peter Studio、机械臂主线和六足副线，且不把候选任务写成最终结论。

- [ ] **Step 1: Inspect the existing README sections before editing**

  Run:

  ```powershell
  rg -n "^#|桌面 AI 助手|机械臂|网站|SEO|Portfolio|Developer Experience|Day 1|Flagship|当前" README.md
  ```

  Expected: 输出 README 的标题和相关叙事位置，确认只在现有结构中做局部修改。

- [ ] **Step 2: Update only the relevant README passages**

  Preserve the existing project purpose, task-research links, Developer Experience structure, Portfolio structure, and exclusions. Add or revise wording so it states:

  ```markdown
  Peter Studio 是这个项目的个人机器人工作台与 Physical AI Build Log。

  - 机械臂是桌面 AI 助手的能力主线；
  - 六足机器人是角色、探索和传播副线；
  - 两者共享 Camera、Voice、Screen、LLM/VLM、控制、日志和内容生产基础，但不要求同步开发；
  - 具体生活任务仍需经过调研和早期实验后决定。
  ```

  Keep `peterstudio.online` and `bimanual.org` distinct: the former records what is being built, while the latter explains the embodied-AI field and publishes SEO-oriented knowledge content.

- [ ] **Step 3: Verify README scope and contradictions**

  Run:

  ```powershell
  rg -n "机械臂.*主线|六足.*副线|peterstudio\.online|bimanual\.org|候选|最终 Flagship|Day 8|Developer Experience|Portfolio" README.md
  git diff --check -- README.md
  ```

  Expected: all required concepts appear, no final task is hard-coded, and `git diff --check` exits 0.

- [ ] **Step 4: Commit the README change**

  ```powershell
  git add -- README.md
  git commit -m "docs: clarify Peter Studio project identity"
  ```

### Task 2: Update the 60-day roadmap and capability sequence

**Files:**
- Modify: `ROADMAP.md` — 把双机器人分工嵌入现有能力成长线、里程碑、任务调研和 Flagship Projects 说明。

**Interfaces:**
- Consumes: Task 1 的项目身份表述和设计文档的 60 天执行原则。
- Produces: Roadmap 明确“机械臂证明助手能力、六足建立角色传播”，同时保持任务选择开放。

- [ ] **Step 1: Inspect roadmap sections and existing Day 1–7 references**

  Run:

  ```powershell
  rg -n "^#|^##|^###|M[0-9]|能力|机械臂|六足|任务|Flagship|Screen|Speaker|Voice|Day 1|Day 7|Day 8|Portfolio" ROADMAP.md
  ```

  Expected: identify the existing milestone table, capability line, task-research section, Screen/Speaker/Voice milestone, and flagship-project boundary.

- [ ] **Step 2: Update roadmap narrative without changing its milestone scope**

  Add the following decisions in the existing roadmap locations:

  ```markdown
  ### 双机器人分工

  - 机械臂：Assistant Capability Track，优先验证桌面 AI 助手的真实操作能力；
  - 六足机器人：Character & Reach Track，优先验证角色、移动、环境探索和传播表现；
  - Camera、Microphone、Speaker、Screen、LLM/VLM、日志和内容流程可以共享，但第一阶段工程资源优先投入机械臂。
  ```

  Reframe any “robot body” language that could imply the hexapod is the primary assistant body. Keep the existing task-research gate, and explicitly state that the six-legged robot may be researched or prototyped without becoming a flagship assistant task.

- [ ] **Step 3: Verify roadmap preserves required milestones and open task selection**

  Run:

  ```powershell
  rg -n "机械臂.*(主线|Assistant)|六足.*(副线|Character)|Camera|Microphone|Speaker|Screen|LLM|VLM|任务.*(调研|候选)|最终 Flagship|Day 8" ROADMAP.md
  git diff --check -- ROADMAP.md
  ```

  Expected: both tracks, multimodal milestones, open task selection, and the absence of Day 8–14 content are visible.

- [ ] **Step 4: Commit the roadmap change**

  ```powershell
  git add -- ROADMAP.md
  git commit -m "docs: align roadmap with dual robot tracks"
  ```

### Task 3: Update content-production and comic storyboard rules

**Files:**
- Modify: `CONTENT_PRODUCTION_LOOP.md` — 增加 Peter Studio 原创工作台视觉语言、漫画式分镜和双机器人内容分工。

**Interfaces:**
- Consumes: README 与 ROADMAP 的统一定位。
- Produces: 每次真实实验完成后，能够将机械臂能力内容和六足角色内容转化为不同叙事，同时保留证据优先原则。

- [ ] **Step 1: Inspect existing capture and publishing rules**

  Run:

  ```powershell
  rg -n "^#|^##|^###|Capture|Publishing|Personal Blog|Social Media|Portfolio|真实|失败|漫画|视觉|机械臂|桌面 AI" CONTENT_PRODUCTION_LOOP.md
  ```

  Expected: locate capture, reality-check, publishing-pack, personal build log, and guided-execution sections.

- [ ] **Step 2: Add the Peter Studio visual language section**

  Add a focused section near the existing personal-build-log or visual-content rules:

  ```markdown
  ## Peter Studio Visual Language

  Peter Studio 可以采用“个人机器人工作台”的原创视觉语言：临时拼装、桌面实验室、手写笔记、零件、工具、失败记录、机器人草稿、测试痕迹、状态标签和漫画式分镜。

  漫画式分镜用于解释真实实验过程：问题出现 → 尝试方案 → 机器人反应 → 失败 → 修改 → 新结果。它不能替代真实视频、命令、数据和边界说明。
  ```

- [ ] **Step 3: Add the two-track content framing**

  State that arm content asks “AI 获得了什么助手能力”，while hexapod content asks “这个机器人角色看见、移动、探索或回应了什么”。 Both must use real evidence and may share footage, logs, and technical infrastructure.

- [ ] **Step 4: Verify the new rules do not move content creation before experiments**

  Run:

  ```powershell
  rg -n "Peter Studio|漫画式分镜|机械臂|六足|真实|证据|实验之后|实验结果之后|不.*替代" CONTENT_PRODUCTION_LOOP.md
  git diff --check -- CONTENT_PRODUCTION_LOOP.md
  ```

  Expected: the visual language and two-track framing are present, and the existing “experiment first, content processing later” rule remains intact.

- [ ] **Step 5: Commit the content-rule change**

  ```powershell
  git add -- CONTENT_PRODUCTION_LOOP.md
  git commit -m "docs: add Peter Studio comic content language"
  ```

### Task 4: Record the current strategic decision and execution entry point

**Files:**
- Modify: `PROGRESS.md` — 记录当前路线决策、未决事项和下一步从 Guided Execution 的 Day 1 入口开始。

**Interfaces:**
- Consumes: Tasks 1–3 的最终叙事。
- Produces: 项目进度页反映真实决策，而不是只保留抽象计划。

- [ ] **Step 1: Inspect the current progress format**

  Run:

  ```powershell
  Get-Content -Raw PROGRESS.md
  ```

  Expected: identify the existing status, decision, and next-step sections before inserting a compact entry.

- [ ] **Step 2: Add one dated strategic decision entry**

  Record:

  - Peter Studio will be rebuilt as a personal robot workbench and Physical AI Build Log;
  - arm-first for assistant capability;
  - hexapod as character and reach/传播 track;
  - task and flagship selection remain open;
  - next execution entry is Guided Execution Mode for Day 1, with no automatic Day 2 or Day 8–14 generation.

- [ ] **Step 3: Verify progress reflects the actual state**

  Run:

  ```powershell
  rg -n "Peter Studio|机械臂|六足|主线|副线|候选|Flagship|Guided Execution|Day 1|Day 8" PROGRESS.md
  git diff --check -- PROGRESS.md
  ```

  Expected: one coherent current-direction entry is visible and no completed experiment is falsely claimed.

- [ ] **Step 4: Commit the progress change**

  ```powershell
  git add -- PROGRESS.md
  git commit -m "docs: record Peter Studio direction decision"
  ```

### Task 5: Cross-document acceptance verification

**Files:**
- Test: `README.md`, `ROADMAP.md`, `CONTENT_PRODUCTION_LOOP.md`, `PROGRESS.md`, `daily/day-01.md` through `daily/day-07.md`, `robot-arm/tasks/task-research.md`, `robot-arm/tasks/task-selection.md`

**Interfaces:**
- Consumes: Tasks 1–4 committed documentation updates.
- Produces: 可复现的文档一致性检查结果。

- [ ] **Step 1: Run repository-wide wording checks**

  ```powershell
  $required = @(
    'README.md',
    'ROADMAP.md',
    'CONTENT_PRODUCTION_LOOP.md',
    'PROGRESS.md'
  )
  foreach ($file in $required) {
    if (-not (Test-Path $file)) { throw "Missing required file: $file" }
  }
  rg -n "Peter Studio|peterstudio\.online|bimanual\.org|机械臂.*主线|六足.*副线|漫画式分镜" README.md ROADMAP.md CONTENT_PRODUCTION_LOOP.md PROGRESS.md
  rg -n "候选|最终 Flagship Task|任务.*调研|不.*锁定" README.md ROADMAP.md robot-arm/tasks/task-research.md robot-arm/tasks/task-selection.md
  git diff --check
  ```

  Expected: required concepts are represented in the intended documents and no whitespace errors are reported.

- [ ] **Step 2: Confirm Day 1–7 are retained exactly as the existing set and Day 8–14 are absent**

  ```powershell
  $dayFiles = Get-ChildItem daily -Filter 'day-*.md' | Select-Object -ExpandProperty Name
  $expected = 1..7 | ForEach-Object { "day-{0:D2}.md" -f $_ }
  if ((Compare-Object $dayFiles $expected)) { throw "Day 1-7 file set changed" }
  if ($dayFiles -match 'day-(0[89]|1[0-4])\.md') { throw "Day 8-14 must not exist" }
  'Day 1-7 retained; Day 8-14 absent'
  ```

  Expected: `Day 1-7 retained; Day 8-14 absent`.

- [ ] **Step 3: Inspect final diff and status without touching unrelated changes**

  ```powershell
  git diff --stat HEAD~4..HEAD
  git status --short
  ```

  Expected: only the four intended project documents were changed by this plan’s commits; pre-existing user modifications and untracked assets remain preserved and are not reset or deleted.

- [ ] **Step 4: Report the verified result**

  Report the four modified files, the arm/hexapod division, the unchanged task-research gate, the retained Day 1–7 files, and the exact next execution entry point: Guided Execution Mode → Day 1.
