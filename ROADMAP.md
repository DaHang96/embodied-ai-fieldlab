# 60 天 Roadmap

## 北极星结果

60 天结束时，作品集首页能够清晰呈现：

> 我不是只“了解”具身智能，而是在尝试打造一个真正存在于物理世界中的桌面 AI 助手：实际部署过开源机器人，研究过它能为日常生活完成什么任务，做过真实实验，体验过开发者上手阻力，并能把技术转化为内容、教育材料和生态策略。

## 60 天阶段与里程碑

| 阶段 | 天数 | 重点 | 退出证据 |
|---|---:|---|---|
| M0 项目启动 | Day 1 | 明确定位、约束、设备决策标准和证据格式 | 基线记录、候选路径评分、Day 1 资产 |
| M1 任务调研、选型与准备 | Day 2–7 | 调研桌面 AI 助手候选任务、确认机械臂路径、同步研究六足机器人角色方向、准备环境、拆解文档和第一次内容叙事 | 候选任务研究记录、决策备忘录、环境清单、控制链路计划、2 个高潜内容进入制作 |
| M2 真实部署 | Day 8–14 | 到货验收、安装、环境配置、第一次运动；记录全部摩擦 | First Motion 证据、安装日志、首个 DX Pain Point |
| M3 遥操作与感知 | Day 15–21 | 理解关节/末端/坐标、相机、标定、遥操作和安全边界 | Teleoperation Demo、相机/标定记录、故障复盘 |
| M4 数据闭环 | Day 22–30 | 设计一个现实任务，采集 demonstration，形成最小数据集 | Dataset、任务定义、评估标准、Day 30 复盘 |
| M5 Policy 基线 | Day 31–37 | 使用现成教程或基线完成训练/推理，不为数学细节失控 | Training/Inference 记录、成功率或失败率、Expectation vs Reality 内容 |
| M6 AI 接入 | Day 38–44 | 尝试语言、视觉或 VLA 组件接入，明确决策与动作的边界 | Voice/Language → Decision → Action Demo 或诚实的失败实验 |
| M7 Robot in Real Life | Day 45–51 | 用 7 天 Challenge 测试机器人对真实生活任务的帮助程度 | 连续实验素材、任务评分、观众/用户反馈、内容实验数据 |
| M8 生态与教育资产 | Day 52–56 | 完成生态研究、Developer Experience Case Study 和教程 | 生态比较、教程 + 视频/图文、改进策略 |
| M9 作品集与求职包装 | Day 57–60 | 打磨 5 个 Case Study、职业叙事、Demo 索引和下一步计划 | Portfolio 首页、简历素材、公开链接清单、最终复盘 |

## Desktop AI Assistant 能力成长线

60 天不是 60 个相互独立的小实验，而是一条逐渐形成助手能力的成长线：

1. **给 AI 一只手**：机械臂安装、Calibration、Teleoperation、Pick & Place 和安全的桌面动作，让它第一次能够改变真实世界。
2. **给 AI 一双眼睛**：Camera、Image/Video、Object Observation 和 VLM 基础，让它能够看见桌面上发生了什么。
3. **让 AI 听懂我**：Microphone、Speech Recognition、Natural Language Command 和 LLM，让用户可以用语言提出请求。
4. **让 AI 开口说话**：Speaker、TTS 和 Feedback，让它说明自己理解了什么、准备做什么以及遇到了什么问题。
5. **给 AI 一张脸**：Screen、Status UI、Simple Expressions 和视觉人格，让它从机械臂逐渐成为可被理解的角色。
6. **让 AI 学会技能**：Demonstration、Dataset、Imitation Learning、Policy、VLA、Training 和 Inference，回答它能否通过示范学会新的真实任务。

这条能力线服务于一个仍然开放的问题：桌面 AI 助手最终最值得学会什么，不能凭感觉预设，要由任务调研和早期实验决定。

### 双机器人并行分工与落地顺序

本项目采用两条并行研究轨道。机械臂和六足机器人都可以成为 Peter Studio 的角色与传播主体，区别只在于它们优先研究的具身能力不同：

- **机械臂：Manipulation & Assistant Research Track**。研究桌面 AI 助手的感知、语言、操作、数据和学习闭环，也可以通过人格、声音、屏幕和漫画式内容成为角色。
- **六足机器人：Locomotion & Character Research Track**。研究移动、环境探索、互动和角色扩展，也可以通过开源复现、失败测试和原创外壳成为内容主角。
- 两条线共享 Camera、Microphone、Speaker、Screen、LLM/VLM、控制与日志系统、实验数据和内容生产流程；不预设固定投入比例，也不要求同步达到相同成熟度。

落地顺序上，先让六足机器人通过一个可复现的 GitHub 开源项目获得第一个真实机器人闭环；机械臂研究同步进行，但可以先完成生态、硬件路径、LeRobot、任务和数据闭环研究，不要求立刻完成硬件部署。六足基线跑通后，再并行拓展六足能力与机械臂实践。未来再根据实验结果决定是否让两者协作。

## Local Robot + Remote GPU 架构

本地电脑为 RTX 3060 Laptop，采用“本地机器人控制 / 数据采集 + 云端 GPU 训练 + 本地推理”的架构。这样本地显卡有限时，项目仍然以真实机器人实践为优先，不转为纯仿真项目。

| 环境 | 主要职责 |
|---|---|
| RTX 3060 Laptop | Robot Control、SDK、Camera、Teleoperation、Data Collection、Dataset Inspection、Lightweight Inference、Debugging |
| Remote GPU | Policy Training、较大模型实验、必要时的 VLA Fine-tuning |

```text
Robot + Camera
↓
Local Laptop
↓
Teleoperation / Dataset
↓
Remote GPU
↓
Training
↓
Checkpoint
↓
Local Inference
↓
Real Robot Task
```

## Desktop AI Assistant Task Research

`桌面 AI 助手` 是确定的总体方向，但具体生活任务要先调研和比较，再决定 2–4 个 Flagship Task。前 1–2 周允许优先做用户场景研究、开源机器人案例研究、内容案例研究和技术可行性验证。

调研至少回答：

1. 个人级/开源机械臂当前能稳定做到什么；
2. LeRobot、SO-101 等生态常见哪些任务；
3. 各平台哪些机器人任务容易让普通观众产生兴趣；
4. 哪些 Demo 已经过度重复；
5. 哪些生活任务的价值一眼可懂；
6. 哪些任务具有明显的 AI 助手感；
7. 哪些任务视觉表现强、失败也有内容价值；
8. 哪些任务能从简单版本逐步升级到 Vision、Voice、LLM、Learning/VLA；
9. 哪些任务能自然接入 Camera、Voice、LLM、VLM、VLA、Screen、Speaker；
10. 哪些任务适合桌面机械臂，并满足安全、成本和空间限制。

每个候选任务按 1–5 分评价：Technical Feasibility、Beginner Feasibility、Visual Impact、Immediate Understandability、Life Relevance、AI Assistant Feeling、Failure Entertainment、Upgrade Potential、Repeatability、Safety、Cost、Content Potential。至少形成 15–30 个候选任务，并分为：

- **A. 很适合作为 Flagship Task**：值得进入重点比较；
- **B. 很适合做单期内容**：传播潜力强，但未必适合长期投入；
- **C. 很适合技术验证**：适合作为能力成长中的中间实验；
- **D. 暂时不适合**：记录技术难度、危险、特殊硬件、视觉效果差、观众难理解、同质化或与定位关联弱等原因。

### Candidate Task Directions

当前可以研究的候选方向包括桌面整理、递取物品、内容创作辅助、桌面办公辅助、人机互动、AI + 机械臂，以及调研发现的其他方向。它们都不是最终结论。最终任务必须同时具备可实现性、可理解性、生活意义、视觉表现、可重复实验、失败内容价值和 AI 能力升级空间。具体记录见 [task-research.md](robot-arm/tasks/task-research.md) 和 [task-selection.md](robot-arm/tasks/task-selection.md)。

### 影视 AI 助手的传播参照

JARVIS 等影视 AI 助手只作为传播参照，不作为项目名称。调研重点不是复制外观，而是分析观众为什么觉得它们“智能”：主动回应、记住上下文、看见环境、听懂语言、给出反馈、预测需求、操作现实世界、有声音和人格、提供视觉反馈、提醒用户犯错并与用户协作。再将其中可落地的体验优先映射到机械臂助手，同时把角色、声音、屏幕反馈和互动感扩展到六足机器人方向。

### Multimodal Personality Layer

这是后期正式里程碑，不要求现在购买硬件。它包含 Speaker、Microphone、ASR、TTS、Screen、Status UI、Simple Expressions 和 Assistant Personality。目标不是装饰机械臂，而是让用户明显感觉它是一个 AI 助手，并承担 Human-Robot Interaction 与内容表达作用。

### 动态调整规则

- 硬件未到货：优先推进环境验证、文档研究、仿真/示例控制链路、任务设计和内容准备；不虚构真实机器人结果。
- 硬件故障或环境失败：先保留日志并把失败转成 DX 素材，再切换到最小可行替代路径。
- 某项技术连续投入但没有产生机器人进展、Demo、内容、Portfolio 或职业证据：暂停深挖，改为完成一个可见的小闭环。
- 内容数据不理想：保留实验记录，比较 Hook、画面、时长、平台与叙事，不把单条播放量当作唯一成功标准。
- 新工具或新模型出现：只有在能显著降低实践门槛、提高证据质量或改变职业叙事时才插入；否则记录到 backlog。

## Flagship Projects

以下 Flagship Projects 是作品集与能力闭环，不等于预先锁定某几个具体生活任务。具体生活任务要经过 `Desktop AI Assistant Task Research` 后再进入 `Teach My Robot`、`Robot in Real Life` 等项目。

### Flagship 1 — I Built My First Open-Source Robot

**目标**：完成从硬件路径决策、到货验收、环境安装、第一次运动、第一次可控任务的完整闭环。

**过程证据**：预算与约束、购买决策、安装日志、版本信息、照片/视频、错误信息、第一次成功与失败。

**最终资产**：部署 Demo、Setup Guide、Troubleshooting Note、硬件真实体验文章/视频。

**对应 Case Study**：Case Study 01 — Open Source Robot Deployment。

### Flagship 2 — Teach My Robot

**目标**：让机器人通过 demonstration / imitation learning 学会一个经过调研与早期实验筛选、边界清晰的真实任务。

**过程证据**：任务定义、成功判定、遥操作、数据集样例、训练配置、推理结果、失败分类。

**最终资产**：从 Demonstration 到 Inference 的可复现实验、结果视频和面向非算法读者的解释。

**对应 Case Study**：Case Study 01 + Case Study 03 — Developer Education。

### Flagship 3 — Give My Robot a Brain

**目标**：探索 Voice / Language / Vision / VLA 如何影响机器人动作，明确哪些部分仍需要规则、安全检查或人工确认。

**过程证据**：输入、决策、动作的链路图；成功/失败案例；延迟、误解和安全边界记录。

**最终资产**：AI × Robot 实验 Demo、一篇“ChatGPT 有大脑但没有身体”的解释内容、架构说明。

**对应 Case Study**：Case Study 03 + Case Study 04。

### Flagship 4 — Robot in Real Life

**目标**：用连续 Challenge 测试经调研选出的真实生活任务对普通人的帮助，而不是只展示一次完美 Demo；在任务选定前，Challenge 也可以用于比较候选方向。

**过程证据**：明确任务、时间限制、失败风险、人工干预次数、完成时间、用户/观众反馈。

**最终资产**：Challenge 系列内容、任务评分表、Expectation vs Reality 复盘。

**对应 Case Study**：Case Study 05 — Technical Content Experiment。

### Flagship 5 — Developer Experience Case Study

**目标**：从新开发者视角研究一个真实开源机器人项目的 Discovery → Documentation → Installation → First Success → Community → Retention。

**过程证据**：每一步的实际耗时、阻塞点、文档截图/链接、错误信息、与成功路径的对照。

**最终资产**：DX Journey Map、Pain Point Backlog、入门教程、Developer Ecosystem 改进提案。

**对应 Case Study**：Case Study 02 — Developer Experience。

## 作品集五个 Case Study 的验收标准

| Case Study | 至少要证明什么 | 必须有的证据 |
|---|---|---|
| 01 Open Source Robot Deployment | 真正部署并使用过机器人 | 设备/环境/日志/视频/任务结果 |
| 02 Developer Experience | 能发现并结构化开发者痛点 | Journey、Pain Points、优先级、改进建议 |
| 03 Developer Education | 能把复杂技术讲清楚并帮助别人复现 | Tutorial、解释内容、复现反馈 |
| 04 Ecosystem Research | 能从生态和 GTM 角度比较项目 | 比较框架、来源、洞察、策略建议 |
| 05 Content Experiment | 能设计、分发、衡量并迭代技术内容 | 选题、脚本、发布记录、数据、迭代结论 |

## 本周以后的每周节奏

每 7 天创建/更新一个 `weekly/week-X.md`，回答本周复盘问题，并重新确认：

1. 下一周唯一最重要的机器人结果是什么？
2. 哪个内容值得制作，哪个只保留为素材？
3. 哪个 DX 痛点最值得写成 Case Study？
4. 哪个学习任务应删除或延后？
5. 下周必须交付什么 Portfolio Evidence？

Day 30 另做一次中期定位复盘，必须回答“我的差异化是否已经从学习者变成实践者 + 生态观察者 + 技术内容创作者”。

