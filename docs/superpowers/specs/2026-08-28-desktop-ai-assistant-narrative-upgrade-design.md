# Desktop AI Assistant 项目叙事与执行原则升级设计

> 历史规格：2026-09-04 已将项目总目标修正为“60 天内运行开源具身机器人并探索其能力”。本文件保留原始设计背景，不作为当前总目标的权威来源；当前状态请查看 `docs/project-state/current-state.md`。

## 目标

在不推倒重来、不删除现有机器人实践、Developer Experience 和 Portfolio 结构的前提下，将项目统一升级为“打造一个真正存在于物理世界中的桌面 AI 助手”，并让具体生活任务通过前期调研和早期实验产生，而不是预先写死。

## 已确认的范围

- 修改现有 `README.md`、`ROADMAP.md` 和 `daily/day-01.md` 至 `daily/day-07.md`。
- 保留现有 M0–M9 阶段、Developer Experience 结构、Portfolio 五个 Case Study 和真实机器人优先原则。
- 新增 `robot-arm/tasks/task-research.md` 与 `robot-arm/tasks/task-selection.md`，作为任务调研和选择的工作文档/模板。
- 不生成或预先规划 Day 8–14。
- 不把桌面整理、递取物品或内容创作辅助写成最终 Flagship Task；它们只能作为候选方向参与竞争。

## 核心叙事

项目唯一确定的总体方向是：

> 我正在尝试打造一个真正存在于物理世界中的桌面 AI 助手。

README 必须明确提出探索问题：

> 当 AI 不再只存在于聊天框，而真正拥有眼睛、耳朵、声音和一只机械手之后，它能不能成为一个真正参与日常生活的桌面 AI 助手？

能力映射为：机械臂是手，Camera 是眼睛，Microphone 是耳朵，LLM/VLM/VLA 是大脑，Speaker 是嘴，Screen 是脸/表情/UI，Robot Policy 是动作能力。JARVIS、现实版贾维斯和影视 AI 助手只能作为传播 Hook，不作为项目正式名称。

## 能力成长线

Roadmap 保留原有 60 天里程碑，同时增加一条贯穿主线：

1. 给 AI 一只手：安装、标定、遥操作和安全的基础桌面动作。
2. 给 AI 一双眼睛：Camera、图像/视频、物体观察和 VLM 基础。
3. 让 AI 听懂我：Microphone、ASR、自然语言命令和 LLM。
4. 让 AI 开口说话：Speaker、TTS 和执行前后反馈。
5. 给 AI 一张脸：Screen、状态 UI、简单表情和视觉人格。
6. 让 AI 学会技能：Demonstration、Dataset、Imitation Learning、Policy、VLA、Training 和 Inference。

后期增加 `Multimodal Personality Layer` 里程碑，包含 Speaker、Microphone、TTS、ASR、Screen、Status UI、Simple Expressions 和 Assistant Personality。它服务于 Human-Robot Interaction 与内容表达，不是装饰性附件。

## 任务研究与选择

`桌面 AI 助手` 是确定方向，但最终 Flagship Task 延后到前 1–2 周的调研和早期实验之后决定。候选方向包括桌面整理、递取物品、内容创作辅助、桌面办公辅助、人机互动、AI + 机械臂，以及调研发现的其他任务。

Roadmap 要增加 `Desktop AI Assistant Task Research` 阶段，研究以下问题：个人级/开源机械臂能稳定做到什么、LeRobot/SO-101 生态中的常见任务、各平台对普通观众有吸引力的机器人任务、已经同质化的 Demo、价值是否一眼可懂、AI 助手感、视觉表现、失败可能、渐进升级路径、Camera/Voice/LLM/VLM/VLA/Screen/Speaker 接入、桌面适配性，以及安全/成本/空间约束。

候选任务按以下 12 个维度以 1–5 分评价：Technical Feasibility、Beginner Feasibility、Visual Impact、Immediate Understandability、Life Relevance、AI Assistant Feeling、Failure Entertainment、Upgrade Potential、Repeatability、Safety、Cost、Content Potential。

候选池至少研究 15–30 个任务，并分为：

- A：很适合作为 Flagship Task
- B：很适合做单期内容
- C：很适合技术验证
- D：暂时不适合，并记录技术难度、危险、特殊硬件、视觉效果、观众理解、同质化或定位弱关联等原因

最终任务必须同时具备可实现性、可理解性、生活意义、视觉表现、可重复实验、失败内容价值和 AI 能力升级空间。

`task-research.md` 记录候选池、评分、研究来源、影视 AI 助手体验拆解和分类结果；`task-selection.md` 只在正式选择后记录 2–4 个任务、选择/放弃理由、技术难度、内容价值、硬件需求、AI 能力和 60 天目标。

## Day 1–7 执行原则

- 早期任务是安全的实验载体，不等于最终 Flagship Task。
- Day 1–7 保留原有环境、DX、任务定义、证据和作品集要求，但将它们解释为任务筛选与能力成长的证据。
- Day 1–4 的内容包装生活化、具象化、角色化：从“学习某个技术”改成“助手能否拥有/获得什么能力”。
- Day 5–7 保留真实任务、First Motion 和 Week 1 复盘，但不提前指定最终生活任务。
- 每个内容选题先回答：完全不了解 ROS2、VLA、LeRobot 的普通观众为什么会点开？
- 内容优先级为普通观众可理解、真实机器人画面、明确目标、失败可能、最终结果、幽默/反差/人格，最后再添加技术解释。
- 失败按助手体验解释：没看见、理解错、抓歪、掉落、没听懂、选错、动作太慢或不知道下一步，而不只记录错误码。
- Day 7 从真实素材中选择两个最值得制作的视频，不预设来源于任何固定任务。

## 算力与系统架构

采用 `Local Robot + Remote GPU`：RTX 3060 Laptop 负责 Robot Control、SDK、Camera、Teleoperation、Data Collection、Dataset Inspection、Lightweight Inference 和 Debugging；Remote GPU 负责 Policy Training、较大模型实验和必要的 VLA Fine-tuning。目标链路为：

`Robot + Camera → Local Laptop → Teleoperation / Dataset → Remote GPU → Training → Checkpoint → Local Inference → Real Robot Task`

本地显卡有限不构成转为纯仿真的理由；真实机器人实践优先，硬件未到时必须清楚区分替代验证和真实硬件证据。

## 预期交付

- README：新的一句话定位、探索问题、能力部件、内容原则和边界。
- ROADMAP：能力成长线、任务调研阶段、候选任务规则、Multimodal Personality Layer 和 Local Robot + Remote GPU。
- Day 1–7：保留原计划结构，更新任务表述、内容 Hook、助手能力/失败叙事和任务候选状态。
- `robot-arm/tasks/task-research.md`：可执行的任务调研与评分模板。
- `robot-arm/tasks/task-selection.md`：延后填写的最终任务选择记录模板。
- 最终回复：修改文件清单、一句话定位、两个最值得制作的视频、普通观众价值、Day 1 待办，并明确未生成 Day 8–14。

## 不在本次范围内

- 不现在开展 15–30 个候选任务的外部调研。
- 不现在确定 2–4 个最终 Flagship Task。
- 不购买屏幕、音箱或其他后期硬件。
- 不改变现有 Developer Experience 和 Portfolio 的核心设计。
- 不开展网站 SEO、关键词计划或独立网站增长工作。
