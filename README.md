# Embodied AI FieldLab

## 具身智能 60 天实践与职业作品集

> Embodied AI × Developer Ecosystem × Technical Content

这是一个以真实实践为核心的 60 天项目。最终交付物不是一张“学过哪些技术”的清单，而是一套可以向具身智能公司展示的公开作品集：真实部署记录、机器人实验、开发者体验研究、技术教育内容、生态研究和内容增长实验。

## 项目定位

项目唯一确定的总体方向是：

> 我正在尝试打造一个真正存在于物理世界中的「桌面 AI 助手」。

我希望探索一个问题：

> 当 AI 不再只存在于聊天框，而真正拥有眼睛、耳朵、声音和一只机械手之后，它能不能成为一个真正参与日常生活的桌面 AI 助手？

这个助手不是普通的软件 Agent，也不是聊天框里的 AI。它逐渐拥有：

- 机械臂：手
- Camera：眼睛
- Microphone：耳朵
- LLM / VLM / VLA：大脑
- Speaker：嘴
- Screen：脸、表情和 UI
- Robot Policy：动作能力

项目不预设它最终要完成哪一种生活任务。具体任务要经过 `Desktop AI Assistant Task Research`、开源机器人案例、内容案例和早期实验后再决定。当前候选方向包括桌面整理、递取物品、内容创作辅助、桌面办公辅助、人机互动、AI + 机械臂，以及调研中发现的其他更有趣、更适合当前能力的任务。候选方向不等于最终 Flagship Task，研究记录见 [task-research.md](robot-arm/tasks/task-research.md)，最终选择记录见 [task-selection.md](robot-arm/tasks/task-selection.md)。

### Peter Studio 与双机器人并行分工

`peterstudio.online` 是这个项目的个人机器人工作台与 Physical AI Build Log。它记录一个人如何从自己的桌面实验室出发，逐步打造真实存在于物理世界中的机器人伙伴。

- **机械臂是 Manipulation & Assistant Research Track**：研究桌面 AI 助手如何看见、听懂、回应并安全地操作现实物体，同时也可以成为 Peter Studio 的角色与传播主体；
- **六足机器人是 Locomotion & Character Research Track**：先通过开源项目完成仿真或实体落地，再研究移动性、环境探索、互动感和角色扩展；它同样可以成为 Peter Studio 的角色与传播主体；
- 两者采用并行双轨，可以共享 Camera、Voice、Screen、LLM/VLM、控制、日志和内容生产基础；不预设固定投入比例，也不要求同步达到相同成熟度；
- 具体生活任务仍然保持开放，必须经过任务调研、评分和早期实验后再决定。

Peter Studio 可以借鉴漫画和电影中个人发明家工作台的创作感，但最终使用原创视觉语言：临时拼装、桌面实验室、手写笔记、零件、工具、机器人草稿、测试痕迹、失败记录、状态标签和漫画式分镜。

项目希望形成的职业叙事是：

> 我真正部署和使用过开源机器人，理解机器人开发者在上手过程中的阻力，能够把复杂的具身智能技术转化为易懂、有画面、可传播的内容，并能从 Developer Ecosystem / Product Marketing / GTM 的角度提出改进方案。

四条主线：

1. **真实机器人实践**：Hardware → Environment → Teleoperation → Data → Policy → Inference → Real Task；真实任务先通过调研与早期实验筛选。
2. **够用的技术理解**：理解机器人、模仿学习、VLA 等概念在真实系统中的作用，不追求算法研究深度。
3. **内容实验**：围绕“桌面 AI 助手获得了什么新能力、为什么失败”创作实验、失败记录和解释型内容。
4. **职业作品集**：每周将可验证的证据沉淀进 Case Study，并持续映射到目标岗位。

### 能力成长主线

60 天不是 60 个相互独立的小实验，而是一条逐步形成助手能力的成长线：

1. 给 AI 一只手：安装、标定、遥操作和安全的基础桌面动作。
2. 给 AI 一双眼睛：Camera、图像/视频、物体观察和 VLM 基础。
3. 让 AI 听懂我：Microphone、ASR、自然语言命令和 LLM。
4. 让 AI 开口说话：Speaker、TTS 以及执行前后反馈。
5. 给 AI 一张脸：Screen、状态 UI、简单表情和视觉人格。
6. 让 AI 学会技能：Demonstration、Dataset、Imitation Learning、Policy、VLA、Training 和 Inference。

JARVIS、现实版贾维斯和影视 AI 助手可以作为帮助观众理解的传播 Hook，但不是项目正式名称。项目会逐渐形成自己的名字、视觉形象、语气、屏幕表情和人格设定。

## 范围边界

本项目不负责网站 SEO、关键词计划、Topic Cluster、网站架构、Search Console、Backlink、Programmatic SEO 或网站日常运营。这些属于独立的网站增长项目。

如果实践中产生适合网站的 Tutorial、Troubleshooting、Hardware Review、Open Source Review、Developer Guide 或 Case Study，只在 daily 文件中标记为 **Website Content Opportunity**，不在此项目中执行 SEO 策略。

## 长期内容生产规则

[`CONTENT_PRODUCTION_LOOP.md`](CONTENT_PRODUCTION_LOOP.md) 是每日执行、素材捕捉、真实结果复盘、Personal Blog / Social Media 发布判断和 Portfolio Evidence 更新的长期工作协议。默认使用其中的 **Guided Execution Mode**：对话是执行入口，Codex 一次只推进一个步骤并自动维护 Markdown；现有各日的 `Content Idea of the Day` 都是实验前预案，执行后的真实结果可以完全改写原故事。

项目 Markdown 默认由 Codex 在后台维护。你的主要工作是回答问题、执行操作、做实验、拍摄素材、提供真实结果和做决策，不需要把同一信息重复复制到多个文件。

### Personal Build Log 与 SEO Website

`peterstudio.online` 的 Personal Build Log 属于当前机器人工作台项目，用于记录机械臂与六足机器人的并行研究、角色成长、Build in Public、技术实践、Developer Experience、Portfolio 和求职证据，不以 SEO 流量为目标。`bimanual.org` 是另一个独立项目，继续负责具身智能资讯、技术解释、SEO Strategy、Keyword Research、Topic Cluster、Search Console、GEO、Internal Linking、Backlinks、Programmatic SEO 和 Organic Growth。本项目只标记有充分真实证据支撑的 `SEO Website Content Opportunity`，不执行 SEO Strategy。

## 目录导航

- [ROADMAP.md](ROADMAP.md)：60 天阶段、里程碑、旗舰项目和调整机制。
- [CONTENT_PRODUCTION_LOOP.md](CONTENT_PRODUCTION_LOOP.md)：每日素材捕捉、真实结果复盘、发布判断和证据沉淀规则。
- [PROGRESS.md](PROGRESS.md)：总进度 Dashboard，每天或每周更新。
- [daily/](daily/)：Day 1–7 已详细设计，后续按真实进展动态生成。
- [weekly/](weekly/)：每 7 天复盘并重排下一周。
- [robot-arm/](robot-arm/)：硬件、环境、实验、故障和 Demo 记录。
- [robot-arm/tasks/](robot-arm/tasks/)：桌面 AI 助手生活任务的调研、评分和最终选择记录。
- [knowledge/](knowledge/)：为当前实践服务的机器人知识。
- [developer-experience/](developer-experience/)：上手、文档、痛点和改进想法。
- [content/](content/)：选题、脚本、实验、发布和素材。
- [ecosystem/](ecosystem/)：公司、开源项目、开发者项目和研究。
- [portfolio/](portfolio/)：五个 Case Study 的证据与成稿。
- [career/](career/)：目标岗位、目标公司、JD 分析和简历素材。

## 每日工作规则

每天最多 3–5 个核心任务，且至少产生一种可积累资产：Experiment、Photo、Video、Demo、Tutorial、Troubleshooting Note、Developer Experience Note、Content Idea、Script、Research Note、Community Interaction 或 Portfolio Material。

每个 Content Idea 先回答：一个完全不知道 ROS2、VLA、LeRobot 的普通人，为什么会点开？内容主标题优先表达助手获得了什么能力、遇到了什么失败或正在解决什么生活问题；技术名词放到解释段、长内容和 Developer Education 资产中。优先级是：普通观众能快速理解、真实机器人画面、明确目标、失败可能、最终结果、幽默/反差/人格，最后再加入技术解释。

记录成功，也记录失败。所有关键实践都尽量保留：

- 预期 vs. 实际结果
- 具体环境、版本、设备和耗时
- 错误信息与解决过程
- 官方文档中不清楚、过时或默认读者已知的部分
- 如果我是 Developer Ecosystem Manager，会如何降低下一位开发者的门槛

## 如何推进

1. 先执行 [daily/day-01.md](daily/day-01.md)，完成后把真实结果、截图、日志、耗时和疑问反馈回来。
2. 每天根据实际状态调整下一天，不把失败改写成成功。
3. Day 7 完成第一次周复盘；Day 30 完成中期定位复盘；Day 60 完成公开作品集复盘。
4. 若某项技术深挖同时不能明显推动机器人、内容、Developer Ecosystem、Portfolio 或职业竞争力，暂停深挖，回到可验证的实践闭环。

## 第一阶段的完成定义

Day 7 时，至少应拥有：

- 一份经过约束条件筛选的机械臂路径决策备忘录，并完成购买/租借/借用动作或明确阻塞原因；
- 一份本地环境与硬件基线；
- 一次可复现的控制链路验证（真实机械臂优先，尚未到货时用仿真/示例/摄像头替代并标明边界）；
- 至少一条 Developer Experience 痛点记录；
- 一份桌面 AI 助手候选任务的初始调研与评分记录，不把候选方向写成最终结论；
- 7 个经过传播潜力分级的内容选题，其中至少 2 个进入脚本或拍摄准备；
- 一个可进入作品集的初始案例素材包；
- 一篇 Week 1 复盘，能说明下一周要继续什么、删除什么。

项目开始日期：2026-08-28（以实际执行 Day 1 为准）
