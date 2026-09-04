# Day 04

## Today's Goal

把 NodeHexa 与机械臂的实践拆成新开发者可以理解的控制链路，并完成一次文档/教程上手旅程记录，为到货验收和 Robot Task Research 建立可解释的能力证据。

## Why It Matters

Developer Ecosystem 的价值不只是“我成功了”，而是能解释另一个人为什么卡住、怎样更快成功，以及产品团队应该优先修什么。

## Tasks

1. 画出当前项目的最小链路：硬件 → 主控/固件 → 控制输入 → 运动 → 观察 → 任务记录。
2. 从新用户视角走一遍 NodeHexa 官方资料，记录到货后每一步的目标、输入、输出和待确认项。
3. 把至少 3 个真实上手痛点按影响 × 频率 × 修复成本排序，并为最高优先级痛点提出文档改进方案。
4. 为一个候选 Robot Task 制作一页 storyboard：开场问题、机器人动作、失败画面、解释点和结尾结果，并标注它不是最终 Flagship Task。

## Robot Practice

若硬件已到，检查桌面布局、相机视野和安全停机方式；若未到，用纸面/仿真把验收、控制和候选任务动作顺序设计出来。所有动作都作为候选任务的早期验证，不提前锁定最终任务。

## Knowledge

- 坐标系、标定、遥操作和动作轨迹的基本作用。
- 机器人任务为什么需要“可观察、可重复、可判定”的成功标准。

## Developer Experience

建立 `developer-experience/onboarding/journey-map-day-04.md`，将每个步骤标记为：清晰、可推断、阻塞、未验证。

## Content Idea of the Day

- Content Level：**A**
- Hook：**“机器人项目最容易被忽略的部分：从按下按钮，到它真的动起来，中间到底发生了什么？”**
- Core Conflict：观众看到机器人动作，以为系统已经完成；真实项目还要处理电源、固件、控制输入、安全停机和结果判定。
- Visual Moment：控制链路图叠加真实桌面/相机视角，展示同一个动作如何因为“看到了但没对准”而失败。
- Experiment：把 NodeHexa 的到货验收与基础运动链拆成普通观众能跟上的“装好 → 接通 → 控制 → 运动”。
- Failure Possibility：供电错误、控制输入不通、安全停机缺失或动作顺序不完整；每一种失败都说明系统还缺哪一层能力。
- Payoff：把抽象的机器人系统变成观众能看懂的“从零件到动作”，同时为后续任务比较留下证据。
- Platforms：Bilibili、知乎、YouTube、X、小红书。
- Long-form Potential：控制链路 Explained、Tutorial、Developer Education Case Study。

## Website Content Opportunity

有：`NodeHexa 从套件到第一次运动的控制链路图解`。适合在有真实截图/日志后写成解释型文章；不做 SEO 执行。

## Assets Created

- 控制链路图
- `developer-experience/onboarding/journey-map-day-04.md`
- 3 条排序后的痛点及改进建议
- 第一任务 storyboard
- 内容选题卡 04

## Portfolio Value

为 Case Study 02 的 Journey Map 和 Case Study 03 的教育材料提供骨架。

## Reflection

填写：哪一步只有机器人开发者才会觉得“显而易见”？我能否用一张图解释它？

## Tomorrow

继续完善到货验收与候选 Robot Task 评估标准；不在本日锁定最终任务。

