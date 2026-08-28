# Desktop AI Assistant Narrative Upgrade Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Upgrade the existing 60-day Embodied AI FieldLab documentation around the single confirmed direction of a physical Desktop AI Assistant, while keeping final life tasks open for research and early experiments.

**Architecture:** Preserve the existing README, M0–M9 roadmap, Day 1–7 daily-plan structure, Developer Experience structure, and five Portfolio Case Studies. Add a task-research layer before task selection, then connect the capability-growth narrative, content rules, candidate-task language, and local/remote compute boundary across the existing documents.

**Tech Stack:** Markdown documentation, Git, PowerShell read-only inspection and validation commands.

## Global Constraints

- The only fixed product direction is “打造一个真正存在于物理世界中的桌面 AI 助手”。
- Desktop整理、递取物品、内容创作辅助、桌面办公辅助、人机互动、AI + 机械臂 and newly discovered tasks are candidates, not final Flagship Tasks.
- Final task selection is deferred until research and early experiments in Weeks 1–2; select 2–4 tasks only after comparison.
- Preserve the existing robot practice, Developer Experience, Portfolio, M0–M9, and real-robot-first structures.
- Use RTX 3060 Laptop for local robot/control/data/lightweight inference work and Remote GPU for policy training, larger-model experiments, and necessary VLA fine-tuning.
- Do not generate or plan Day 8–14.
- Do not perform external research or purchase Screen/Speaker hardware in this implementation.
- Do not add SEO work or modify the Developer Experience and Portfolio core designs.

---

### Task 1: Upgrade the project-level narrative in README

**Files:**
- Modify: `README.md`

**Interfaces:**
- Consumes: Existing project positioning, scope boundary, directory navigation, daily rules, and Day 7 definition of done.
- Produces: A project-level narrative that makes Desktop AI Assistant the fixed direction while keeping task choice open for research.

- [ ] **Step 1: Replace the abstract positioning with the Desktop AI Assistant positioning**

Add the exact exploration question about AI moving beyond a chat box and gaining eyes, ears, voice, and a robotic hand. Explain the component mapping: arm/hand, Camera/eyes, Microphone/ears, LLM/VLM/VLA/brain, Speaker/mouth, Screen/face, and Policy/action capability.

- [ ] **Step 2: Add the public content rule**

Explain that public content should lead with what new capability or failure the assistant gained, while ROS2, Teleoperation, VLA, and other technical terms remain supporting explanations or long-form Developer Education assets. State that JARVIS is only a communication reference and not the project name.

- [ ] **Step 3: Add the open task-discovery rule**

State that the assistant’s concrete life tasks are not predetermined. Link to `robot-arm/tasks/task-research.md` and `robot-arm/tasks/task-selection.md`, and list the candidate directions without calling them Flagship Tasks.

- [ ] **Step 4: Preserve existing boundaries and deliverables**

Keep the existing distinction from SEO/site-growth work, the evidence-first rules, real-versus-substitute verification boundary, and the five portfolio outcomes. Update only wording needed to connect them to task research and capability growth.

- [ ] **Step 5: Validate README terminology**

Run:

```powershell
rg -n "桌面 AI 助手|JARVIS|task-research|task-selection|Flagship|SEO|Developer Experience|Portfolio" README.md
```

Expected: The fixed overall direction, candidate-task distinction, task-research links, and preserved boundaries are all present; no candidate is labeled as a final task.

---

### Task 2: Add capability growth, task research, personality layer, and compute architecture to ROADMAP

**Files:**
- Modify: `ROADMAP.md`

**Interfaces:**
- Consumes: Existing M0–M9 stages, milestone table, five flagship project descriptions, Case Study acceptance criteria, and weekly rhythm.
- Produces: A roadmap that sequences capability growth and defers final task selection until evidence exists.

- [ ] **Step 1: Add the capability-growth spine**

Insert a section that sequences: give AI a hand; give AI eyes; let AI understand speech; let AI speak; give AI a face; let AI learn skills. Map each stage to concrete components and to the user-facing assistant capability it enables.

- [ ] **Step 2: Insert Desktop AI Assistant Task Research into the early roadmap**

Add an early research-and-screening milestone before final flagship-task commitment. Require research into personal/open-source robot capability, LeRobot/SO-101 examples, platform content interest, overused demos, immediate understandability, assistant feeling, visual impact, failure value, upgrade paths, multimodal integration, desktop fit, safety, cost, and space.

- [ ] **Step 3: Define the candidate scoring model and output classes**

Document all 12 five-point dimensions: Technical Feasibility, Beginner Feasibility, Visual Impact, Immediate Understandability, Life Relevance, AI Assistant Feeling, Failure Entertainment, Upgrade Potential, Repeatability, Safety, Cost, and Content Potential. Require a 15–30-item candidate pool classified into A Flagship candidate, B single-episode content, C technical validation, and D temporarily unsuitable with a reason.

- [ ] **Step 4: Convert the three previously fixed tasks into candidate directions**

Retain desktop organizing, object retrieval, and content-creation assistance as examples in the candidate pool. Add desktop office assistance, human–robot interaction, AI + arm, and new research discoveries. State clearly that the final set will be 2–4 tasks selected after Weeks 1–2 research and experiments.

- [ ] **Step 5: Add Multimodal Personality Layer**

Add a later milestone for Speaker, Microphone, ASR, TTS, Screen, Status UI, Simple Expressions, and Assistant Personality. Explain its role in Human-Robot Interaction and content expression, rather than presenting it as decorative hardware.

- [ ] **Step 6: Add the Local Robot + Remote GPU architecture**

Document the responsibilities of the RTX 3060 Laptop and Remote GPU, plus the end-to-end chain:

```text
Robot + Camera → Local Laptop → Teleoperation / Dataset → Remote GPU → Training → Checkpoint → Local Inference → Real Robot Task
```

- [ ] **Step 7: Update milestone wording without generating Day 8–14**

Keep M0–M9 and all later milestone intent. Update only the task-selection dependency and capability language. Do not add a day-by-day plan for Days 8–14.

- [ ] **Step 8: Validate roadmap scope and candidate language**

Run:

```powershell
rg -n "Desktop AI Assistant Task Research|Multimodal Personality Layer|Remote GPU|RTX 3060|Candidate|候选|2–4|15–30|Day 8|Day 14" ROADMAP.md
```

Expected: Research, scoring, personality, compute, and open-task language are present; there is no newly generated Day 8–14 schedule and no candidate is presented as final.

---

### Task 3: Create task research and task selection working documents

**Files:**
- Create: `robot-arm/tasks/task-research.md`
- Create: `robot-arm/tasks/task-selection.md`

**Interfaces:**
- Consumes: Candidate directions, 12-dimension scoring model, early research requirements, and final selection criteria from the upgraded README and ROADMAP.
- Produces: A repeatable research record and a separate decision record that can later hold 2–4 selected Flagship Tasks.

- [ ] **Step 1: Create the task-research document structure**

Include these sections: research goal, research questions, source log with source/date/platform/task/observation fields, candidate pool table for 15–30 tasks, 12 scoring columns using 1–5 values, A/B/C/D classification, reasons for D classification, early experiment evidence, and next comparison actions. Include the user-suggested directions as candidate examples, then actively add new candidates from robot demos, platform research, and early experiments rather than letting the pool consist only of the examples.

- [ ] **Step 2: Add the film/AI-assistant analysis framework**

Include a table for JARVIS and other film/TV AI assistants that records why audiences perceive intelligence: proactive response, context memory, environmental perception, language understanding, feedback, prediction, physical-world action, personality, voice, visual feedback, correction, and collaboration. Add a translation column for what can be explored with arm + Camera + LLM/VLM + Microphone + Speaker + Screen on a personal desktop.

- [ ] **Step 3: Create the task-selection document structure**

State that selection happens only after Weeks 1–2 research and early experiments. Provide fields for selected 2–4 tasks, selection rationale, rejected alternatives and reasons, technical difficulty, content value, hardware requirements, AI capabilities, safety/cost/space constraints, 60-day target, success criteria, and evidence links.

- [ ] **Step 4: Validate that the new documents defer conclusions**

Run:

```powershell
rg -n "候选|Candidate|15–30|1–5|JARVIS|选择|放弃|2–4|调研|早期实验" robot-arm/tasks/task-research.md robot-arm/tasks/task-selection.md
```

Expected: The research file supports an open comparison, and the selection file does not claim any task has already been selected.

---

### Task 4: Update Day 1–4 plans and public content ideas

**Files:**
- Modify: `daily/day-01.md`
- Modify: `daily/day-02.md`
- Modify: `daily/day-03.md`
- Modify: `daily/day-04.md`

**Interfaces:**
- Consumes: Existing Day 1–4 technical, DX, evidence, and Portfolio requirements.
- Produces: Early plans that gather task-selection evidence and use ordinary-viewer assistant-oriented hooks.

- [ ] **Step 1: Update Day 1 facts and task scope**

Add the project content line about building a physical Desktop AI Assistant. Record the known compute plan as `RTX 3060 Laptop + Remote GPU`, with local control/data collection, remote GPU training, and local inference. Replace any implication of a chosen life task with a safe early experiment candidate and a reminder that it is not a final Flagship Task. Link the new task-research document.

- [ ] **Step 2: Replace the Day 1 content card**

Use a hook about trying to build a real Desktop AI Assistant and discovering that the first step is defining what useful task it should eventually do. Show the workspace, constraints, candidate directions, and the gap between a software assistant and a physical assistant.

- [ ] **Step 3: Update Day 2 research and content card**

Keep hardware-path comparison and DX audit. Add task-research input from robot capability and existing examples. Frame the content around finding the first suitable hand/body for an assistant and the hidden constraints ordinary people face, not merely buying hardware.

- [ ] **Step 4: Update Day 3 environment and content card**

Keep smoke tests, reproducibility, and substitution boundaries. Make the content hook about checking whether the RTX 3060 Laptop can serve as the assistant’s local brain while heavier training moves to Remote GPU.

- [ ] **Step 5: Update Day 4 control-chain and content card**

Keep the DX journey and control-chain diagram. Frame the content around giving the assistant a hand/learning how it can see and act, while reserving the final everyday task for research.

- [ ] **Step 6: Validate Day 1–4 content cards**

Run:

```powershell
rg -n "Content Idea|桌面 AI 助手|Candidate|候选|Remote GPU|RTX 3060|为什么会点开|Flagship" daily/day-01.md daily/day-02.md daily/day-03.md daily/day-04.md
```

Expected: Every day has a concrete, ordinary-viewer-facing hook; the compute plan appears where relevant; no day locks a final Flagship Task.

---

### Task 5: Update Day 5–7 plans, failure framing, and weekly selection language

**Files:**
- Modify: `daily/day-05.md`
- Modify: `daily/day-06.md`
- Modify: `daily/day-07.md`

**Interfaces:**
- Consumes: Existing task-definition, First Motion, failure-review, evidence-index, and Week 1 retrospective requirements.
- Produces: Early experiments and content choices that inform task selection without pretending to have finalized it.

- [ ] **Step 1: Reframe Day 5 task definition as an early experiment**

Keep safe/light/soft-object constraints, success criteria, attempt tracking, and pre-hardware substitution. State that the experiment tests feasibility and content value for the candidate pool; it does not decide the final Flagship Task.

- [ ] **Step 2: Replace the Day 5 content card**

Use a hook about testing what a Desktop AI Assistant could reliably do in real life, emphasizing why a simple task can be more valuable than a flashy one. Include failure categories and upgrade potential without claiming the candidate is final.

- [ ] **Step 3: Reframe Day 6 First Motion and failure card**

Keep real-hardware-first and substitute-validation branches. Explain failures as assistant capability failures—did not see, understand, grasp, hear, choose, or know the next step—alongside technical classifications. Use a first visible capability/failure hook.

- [ ] **Step 4: Reframe Day 7 review and selection**

Keep evidence indexing, Week 1 review, Dashboard update, deletion of low-value learning, and selection of two content pieces. Add task-research evidence and state that the two videos are chosen from actual material, not from fixed task assumptions. Do not create Day 8–14.

- [ ] **Step 5: Replace the Day 7 content card**

Frame the weekly review as the assistant’s first week of gaining a body/hand and the process of discovering what it might actually be useful for. Preserve the honest-progress and failure emphasis.

- [ ] **Step 6: Validate Day 5–7 scope**

Run:

```powershell
rg -n "Content Idea|桌面 AI 助手|候选|Candidate|失败|没看见|理解错|Flagship|Day 8|Day 14|task-research" daily/day-05.md daily/day-06.md daily/day-07.md
```

Expected: The files retain their original weekly evidence goals, classify failures in assistant terms, and avoid creating a Day 8–14 plan or prematurely selecting a final task.

---

### Task 6: Cross-document consistency review and delivery verification

**Files:**
- Verify: `README.md`
- Verify: `ROADMAP.md`
- Verify: `daily/day-01.md`
- Verify: `daily/day-02.md`
- Verify: `daily/day-03.md`
- Verify: `daily/day-04.md`
- Verify: `daily/day-05.md`
- Verify: `daily/day-06.md`
- Verify: `daily/day-07.md`
- Verify: `robot-arm/tasks/task-research.md`
- Verify: `robot-arm/tasks/task-selection.md`

**Interfaces:**
- Consumes: All upgraded project documents.
- Produces: A verified, internally consistent narrative and a concise delivery summary.

- [ ] **Step 1: Check repository diff and whitespace**

Run:

```powershell
git diff --check
git status --short
```

Expected: No whitespace errors; only the intended documentation files and task templates are modified, plus the already committed design and plan records.

- [ ] **Step 2: Check prohibited premature conclusions**

Run:

```powershell
rg -n "Flagship Task 1：桌面整理|Flagship Task 2：桌面递物|Flagship Task 3：AI 内容创作|最终任务已|已选任务" README.md ROADMAP.md daily robot-arm/tasks
```

Expected: No result that presents those three examples as selected final tasks. Any mention must clearly say candidate direction or example.

- [ ] **Step 3: Check required architecture and research terms**

Run:

```powershell
rg -n "桌面 AI 助手|Desktop AI Assistant Task Research|Multimodal Personality Layer|RTX 3060 Laptop|Remote GPU|Technical Feasibility|AI Assistant Feeling|Failure Entertainment|Content Potential" README.md ROADMAP.md daily robot-arm/tasks
```

Expected: All required concepts appear in the relevant project documents.

- [ ] **Step 4: Check that Day 8–14 was not generated**

Run:

```powershell
Get-ChildItem daily -Filter 'day-*.md' | Sort-Object Name | Select-Object -ExpandProperty Name
```

Expected: Existing Day 1–7 files remain present, and no new Day 8–14 daily files are created.

- [ ] **Step 5: Review final answer against requested outputs**

Report the modified files, the new one-sentence positioning, the two recommended videos selected from Day 1–7, why each works for ordinary viewers, the Day 1 actions the user must complete, and the explicit statement that Day 8–14 was not generated.
