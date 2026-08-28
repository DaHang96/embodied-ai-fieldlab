# Day 04

## Today's Goal

把机器人实践拆成新开发者可以理解的控制链路，并完成一次文档/教程上手旅程记录。

## Why It Matters

Developer Ecosystem 的价值不只是“我成功了”，而是能解释另一个人为什么卡住、怎样更快成功，以及产品团队应该优先修什么。

## Tasks

1. 画出当前项目的最小链路：Hardware → Driver/SDK → Camera → Calibration → Teleoperation → Dataset → Policy/Inference → Task。
2. 从一个新用户视角走一遍官方文档，记录每一步的目标、输入、输出、实际耗时和阻塞点。
3. 把至少 3 个痛点按影响 × 频率 × 修复成本排序，并为最高优先级痛点提出一个具体文档改进方案。
4. 为第一任务制作一页 storyboard：开场问题、机器人动作、失败画面、解释点和结尾结果。

## Robot Practice

若硬件已到，检查桌面布局、相机视野和安全停机方式；若未到，用纸面/仿真把动作顺序和相机视角设计出来。

## Knowledge

- 坐标系、标定、遥操作和动作轨迹的基本作用。
- 机器人任务为什么需要“可观察、可重复、可判定”的成功标准。

## Developer Experience

建立 `developer-experience/onboarding/journey-map-day-04.md`，将每个步骤标记为：清晰、可推断、阻塞、未验证。

## Content Idea of the Day

- Content Level：**A**
- Hook：**“机器人真正难的不是让它动起来，而是让它知道自己该对准哪里。”**
- Core Conflict：观众看到机械臂移动，以为问题已经解决；真实系统还要处理坐标、相机、标定、轨迹和任务判定。
- Visual Moment：一张控制链路图叠加真实桌面/相机视角，展示同一个动作如何在不同坐标下出错。
- Experiment：用一个简单物体演示“看到了但抓不准”或用纸面/仿真解释这条链路。
- Failure Possibility：视角遮挡、坐标误解、标定偏差或动作顺序不完整。
- Payoff：把抽象的机器人系统变成观众能看懂的“从看到到做到”。
- Platforms：Bilibili、知乎、YouTube、X、小红书。
- Long-form Potential：控制链路 Explained、Tutorial、Developer Education Case Study。

## Website Content Opportunity

有：`机器人第一次任务的控制链路图解`。适合在有真实截图/日志后写成解释型文章；不做 SEO 执行。

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

锁定第一项真实任务和评估标准，准备一个可安全拍摄、可重复、可公开解释的实验。

