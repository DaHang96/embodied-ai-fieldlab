# Day 02

## Today's Goal

完成机械臂实践路径的候选比较与决策，不追求“最强配置”，只选择 60 天内最可能走完闭环的路径。

## Why It Matters

真实部署是差异化的核心证据。一个能被买到、装起来、重复运行的中等路径，比收藏一堆无法落地的模型名更有职业价值。

## Tasks

1. 基于官方文档、产品/仓库页面和社区反馈，列出 2–3 条候选路径；记录访问日期、总成本估算、供货/借用状态、兼容性和数据闭环能力。
2. 用 1–5 分评价：上手门槛、文档质量、社区可求助性、摄像头/遥操作支持、数据采集路径、维修风险、第一任务适配度。
3. 做出一个明确动作：下单、联系借用/租用、或写明暂缓原因与替代路径。不要把“准备购买”写成“已购买”。
4. 把最可能踩坑的 5 个点写入 `developer-experience/pain-points/`，每个点包含“预期、实际证据、影响、下一步验证”。

## Robot Practice

为第一任务列出所需最小能力：末端执行器、桌面范围、相机视角、物体材质、重复次数和人工干预方式。

## Knowledge

- 开源硬件、SDK、驱动、数据工具和模型之间的关系。
- 为什么硬件兼容性和文档路径会决定数据闭环能否完成。

## Developer Experience

做一次“从搜索到第一次成功”的文档审计：新用户能否在 10 分钟内找到安装入口、硬件清单、版本要求和验证命令？记录找不到的地方。

## Content Idea of the Day

- Content Level：**S**
- Hook：**“普通人买第一只开源机械臂，最容易被忽略的不是价格，而是这 7 个无法退货的坑。”**
- Core Conflict：宣传页上的“开箱即用”与真实部署所需的电脑、线材、驱动、空间和时间之间的落差。
- Visual Moment：候选路径评分表、配件清单、官方文档入口和最终决策动作。
- Experiment：用同一套标准比较候选路径，并公开哪些因素让你放弃某条路。
- Failure Possibility：候选设备缺货、配件不全、系统不兼容或总成本超出预期。
- Payoff：观众得到可复用的购买判断框架；失败也能解释“为什么没有盲目下单”。
- Platforms：小红书、Bilibili、抖音、知乎、X。
- Long-form Potential：Hardware Decision Case Study + 选型表格/教程。

## Website Content Opportunity

有：`开源机械臂实践路径比较`。前提是保留候选、评分依据、真实报价/时间和最终结果；只作为内容机会，不延伸为 SEO 计划。

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

