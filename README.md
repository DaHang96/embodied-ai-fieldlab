# Embodied AI FieldLab

## 具身智能 60 天实践与职业作品集

> Embodied AI × Developer Ecosystem × Technical Content

这是一个以真实实践为核心的 60 天项目。最终交付物不是一张“学过哪些技术”的清单，而是一套可以向具身智能公司展示的公开作品集：真实部署记录、机器人实验、开发者体验研究、技术教育内容、生态研究和内容增长实验。

## 项目定位

本项目的总目标是：

> 在 60 天内真正做出并运行开源具身机器人，通过六足机器人和机械臂的实际实验，探索它们能做什么，并把过程沉淀为原创内容和作品集。

这不是一份“学过哪些技术”的清单，而是一条真实的工程实践线：从选择开源方案、购买与组装、通电和控制，到记录失败、测量结果、尝试真实任务，再把证据沉淀为 PeterStudio 内容和职业作品集。

当前采用两条并行的实体机器人路线：

- **六足机器人 / NodeHexa V1**：首台实体机器人，优先复现开源硬件并完成基础运动、控制链和后续扩展验证。官方基础套件已经购买，当前等待到货。
- **机械臂**：另一条具身智能研究与实验路线，后续并行推进；具体硬件、任务和 AI 接入以早期验证为准，尚未提前锁死。

“桌面 AI 助手”不再是项目总目标，而是一个可选的应用方向。随着六足机器人和机械臂获得视觉、语音、语言模型、屏幕或扬声器等能力，我会根据真实实验判断哪些体验值得发展成助手，而不是先假设答案。

项目持续回答三个问题：

1. 开源具身机器人在个人条件下到底能否被复现和运行？
2. 六足机器人和机械臂分别能做什么，限制在哪里？
3. 如何把真实的硬件、软件、失败和实验结果转化为普通人看得懂的原创内容与可验证作品集？

项目希望形成的职业叙事是：

> 我真正部署和使用过开源机器人，理解机器人开发者在上手过程中的阻力，能够把复杂的具身智能技术转化为易懂、有画面、可传播的内容，并能从 Developer Ecosystem / Product Marketing / GTM 的角度提出改进方案。

三条执行线：

1. **六足机器人落地**：以 NodeHexa V1 为第一台实体机器人，从到货、装配、控制到基础运动，建立可验证的开源具身机器人基线。
2. **机械臂具身智能研究**：并行研究开源机械臂、遥操作、Camera、数据、策略和真实任务；具体硬件与任务根据早期证据决定。
3. **内容、Developer Experience 与作品集**：用 PeterStudio、社交媒体、开发者体验记录和 Portfolio Case Study 公开沉淀前两条线的真实过程。

技术理解、实验设计和职业映射是三条线的支撑机制，不单独构成第四条主线。

### 能力成长主线

60 天不是 60 个相互独立的小实验，而是一条从“能运行”走向“能理解、能行动、能解释”的成长线：

1. **让机器人真正动起来**：机械结构、舵机、电源、固件、标定和安全。
2. **让机器人可观察、可调试**：日志、状态反馈、Camera、传感器和可重复实验。
3. **让机器人理解输入**：语音、自然语言、LLM / VLM，以及它们在真实系统中的边界。
4. **让机器人完成可重复任务**：遥操作、数据、策略、学习和真实环境验证。
5. **让机器人形成可感知的交互体验**：Screen、Speaker、Voice 和视觉人格作为后续扩展，不预设为早期必做项。
6. **把能力与失败变成作品**：实验记录、解释型内容、Developer Experience 和 Portfolio Evidence。

影视 AI 助手可以作为帮助观众理解的传播 Hook，但不是项目正式名称或预设终点。项目会逐渐形成自己的名字、视觉形象、语气、屏幕表情和人格设定。

## 范围边界

本项目不负责网站 SEO、关键词计划、Topic Cluster、网站架构、Search Console、Backlink、Programmatic SEO 或网站日常运营。这些属于独立的网站增长项目。

如果实践中产生适合网站的 Tutorial、Troubleshooting、Hardware Review、Open Source Review、Developer Guide 或 Case Study，只在 daily 文件中标记为 **Website Content Opportunity**，不在此项目中执行 SEO 策略。

## 长期内容生产规则

[`CONTENT_PRODUCTION_LOOP.md`](CONTENT_PRODUCTION_LOOP.md) 是每日执行、素材捕捉、真实结果复盘、Personal Blog / Social Media 发布判断和 Portfolio Evidence 更新的长期工作协议。默认使用其中的 **Guided Execution Mode**：对话是执行入口，Codex 一次只推进一个步骤并自动维护 Markdown；现有各日的 `Content Idea of the Day` 都是实验前预案，执行后的真实结果可以完全改写原故事。

项目 Markdown 默认由 Codex 在后台维护。你的主要工作是回答问题、执行操作、做实验、拍摄素材、提供真实结果和做决策，不需要把同一信息重复复制到多个文件。

### Personal Build Log 与 SEO Website

Personal Build Log 属于当前具身机器人实践项目，用于 Build in Public、项目时间线、技术实践、Developer Experience、Portfolio 和求职证据，不以 SEO 流量为目标。Embodied AI SEO Website 属于另一个项目，负责 SEO Strategy、Keyword Research、Topic Cluster、Search Console、GEO、Internal Linking、Backlinks、Programmatic SEO 和 Organic Growth。本项目只标记有充分真实证据支撑的 `SEO Website Content Opportunity`，不执行 SEO Strategy。

## 目录导航

- [ROADMAP.md](ROADMAP.md)：60 天阶段、里程碑、旗舰项目和调整机制。
- [CONTENT_PRODUCTION_LOOP.md](CONTENT_PRODUCTION_LOOP.md)：每日素材捕捉、真实结果复盘、发布判断和证据沉淀规则。
- [PROGRESS.md](PROGRESS.md)：总进度 Dashboard，每天或每周更新。
- [PORTABILITY.md](PORTABILITY.md)：换电脑恢复项目、Skills、机器人环境和 Smoke Test。
- [docs/project-state/current-state.md](docs/project-state/current-state.md)：当前状态、唯一决策入口和工作区规则。
- [docs/project-state/document-map.md](docs/project-state/document-map.md)：文档角色、生命周期和读取顺序。
- [daily/](daily/)：Day 1–7 已详细设计，后续按真实进展动态生成。
- [weekly/](weekly/)：每 7 天复盘并重排下一周。
- [robot-arm/](robot-arm/)：硬件、环境、实验、故障和 Demo 记录。
- [robot-arm/tasks/](robot-arm/tasks/)：通用 `Robot Task Research`、候选任务评分和最终选择记录；“助手”只是可能的应用方向，不是预设结论。
- [knowledge/](knowledge/)：为当前实践服务的机器人知识。
- [developer-experience/](developer-experience/)：上手、文档、痛点和改进想法。
- [content/](content/)：选题、脚本、实验、发布和素材。
- [ecosystem/](ecosystem/)：公司、开源项目、开发者项目和研究。
- [portfolio/](portfolio/)：五个 Case Study 的证据与成稿。
- [career/](career/)：目标岗位、目标公司、JD 分析和简历素材。

## 每日工作规则

每天最多 3–5 个核心任务，且至少产生一种可积累资产：Experiment、Photo、Video、Demo、Tutorial、Troubleshooting Note、Developer Experience Note、Content Idea、Script、Research Note、Community Interaction 或 Portfolio Material。

每个 Content Idea 先回答：一个完全不知道 ROS2、VLA、LeRobot 的普通人，为什么会点开？内容主标题优先表达机器人获得了什么能力、遇到了什么失败或正在解决什么现实问题；如果实验确实涉及助手体验，再把它作为叙事角度。技术名词放到解释段、长内容和 Developer Education 资产中。优先级是：普通观众能快速理解、真实机器人画面、明确目标、失败可能、最终结果、幽默/反差/人格，最后再加入技术解释。

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

- 一条已经选定并进入真实执行的开源机器人路径；当前为 NodeHexa V1 基础套件，已购买但尚未到货，不能提前写成已运行；
- 一份本地环境与硬件基线；
- 一次可复现的控制链路验证（优先使用到货后的 NodeHexa；尚未到货时用仿真/示例/代码审计替代并标明边界）；
- 至少一条 Developer Experience 痛点记录；
- 一份 `Robot Task Research` 候选任务与初始评分记录，不把任何候选方向写成最终结论；
- 7 个经过传播潜力分级的内容选题，其中至少 2 个进入脚本或拍摄准备；
- 一个可进入作品集的初始案例素材包；
- 一篇 Week 1 复盘，能说明下一周要继续什么、删除什么。

项目开始日期：2026-08-28（以实际执行 Day 1 为准）
