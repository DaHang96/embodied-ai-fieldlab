# Day 02

## Today's Goal

完成首台实体机器人路线决策，并启动通用 Robot Task Research；不追求“最强配置”，只选择 60 天内最可能走完真实闭环的开源机器人路径。

## Guided Execution Record

### Step 1：确认当前硬件资源

状态：已完成。

- 当前没有机械臂；
- 没有已购买的 SO-101 或其他型号；
- 没有可借用机械臂或借用渠道；
- 没有配套电源、夹爪或控制器。

因此，Day 2 的候选比较以“预算内可获得、文档可复现、能尽快形成真实硬件闭环、保留后续感知/控制扩展空间”为基本筛选条件。已同步到 [`decision-memo.md`](../robot-arm/hardware/decision-memo.md)。本日最终选择已在后续 NodeHexa 采购记录中完成收口。

## Actual Outcome

状态：**核心任务已完成；进入 NodeHexa 到货前准备阶段。**

- 首台实体机器人：官方 NodeHexa V1；
- 采购状态：已购买，尚未到货；
- 具体配置：套餐 B、2000mAh 电池、含充电器、部分组装；
- 当前边界：不能写成已到货、已组装或已运行；
- 后续入口：从到货清点和安全验收开始，不重新进行无依据的路线选购。

## Why It Matters

真实部署是差异化的核心证据。一个能被买到、装起来、重复运行的中等路径，比收藏一堆无法落地的模型名更有职业价值。

## Tasks

1. 基于官方文档、项目仓库、器材说明和社区资料，比较六足机器人与机械臂候选路径；记录成本、复现入口、兼容性和扩展边界。
2. 用 1–5 分评价：上手门槛、文档质量、社区可求助性、基础运动可验证性、扩展能力、维修风险和内容价值。
3. 做出一个明确动作：首台实体机器人选择官方 NodeHexa V1 基础套件；不要把购买写成到货或已运行。
4. 把最可能踩坑的 5 个点写入 `developer-experience/pain-points/`，每个点包含“预期、实际证据、影响、下一步验证”。
5. 从开源机器人案例和真实生活场景开始补充 `robot-arm/tasks/task-research.md`，统一记录为 Robot Task Research，不做最终任务选择。

## Robot Practice

为早期验证任务列出所需最小能力：机器人形态、运动范围、相机视角、物体材质、重复次数和人工干预方式，并标注它只是候选任务实验，不是最终 Flagship Task。

## Knowledge

- 开源硬件、SDK、驱动、数据工具和模型之间的关系。
- 为什么硬件兼容性和文档路径会决定数据闭环能否完成。

## Developer Experience

做一次“从搜索到第一次成功”的文档审计：新用户能否在 10 分钟内找到安装入口、硬件清单、版本要求和验证命令？记录找不到的地方。

## Content Idea of the Day

- Content Level：**S**
- Hook：**“我本来想先研究机器人的大脑，结果第一步变成：先选一台真的能买到、装起来、跑起来的机器人。”**
- Core Conflict：开源项目看起来都能运行，但成本、零件、文档、装配和第一次成功之间隔着一整张现实清单。
- Visual Moment：候选机器人评分表、NodeHexa 套件图片、配件清单和最终决策动作。
- Experiment：用同一套标准比较开源机器人路径，并记录它们适合哪些 Robot Task 候选实验。
- Failure Possibility：设备缺货、配件不全、系统不兼容、总成本超出预期，或硬件根本不适合候选任务。
- Payoff：观众得到可复用的开源机器人选型判断，也能看到“买到套件”距离“机器人运行”究竟还有多少步。
- Platforms：小红书、Bilibili、抖音、知乎、X。
- Long-form Potential：Hardware Decision Case Study + 选型表格/教程。

## Website Content Opportunity

有：`开源机器人路径比较`。前提是保留候选、评分依据、真实报价/时间和最终结果；只作为内容机会，不延伸为 SEO 计划。

## Assets Created

- `robot-arm/hardware/decision-memo.md` 初版
- 候选路径比较表
- 购买/借用/暂缓的决定记录
- 5 条初始 Developer Pain Point
- 内容选题卡 02

## Portfolio Value

为 Case Study 01 的决策透明度、Case Study 02 的 Discovery/Documentation 观察提供证据。

## Reflection

填写：今天哪个评分项改变了最终选择？哪一个“看起来便宜”的方案其实隐藏了什么成本？

## Tomorrow

让本地环境完成一次最小可复现的安装/运行验证，尽早暴露系统依赖风险。
