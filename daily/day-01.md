# Day 01

## Today's Goal

建立项目基线：明确时间、预算、设备、空间、安全与第一项真实任务的约束，让后续机械臂选型和内容方向有真实依据。

## Why It Matters

如果不先写清约束，60 天很容易变成阅读 ROS2、VLA 和论文的学习清单。今天的结果会直接影响硬件路径、第一周内容和最终作品集的可信度。

## Tasks

1. 复制本文件中的“项目基线”问题，写入 `robot-arm/hardware/decision-memo.md`：预算上限、每周可投入时间、桌面空间、电脑系统/GPU/RAM、相机、噪音/安全限制、可接受的到货等待时间。
2. 记录本地环境基线：OS、Python、GPU/显存、可用磁盘、是否能使用 Linux/WSL/远程 Linux；只记录事实，不急着修环境。
3. 选定一个第一任务候选，例如“抓取并移动一个软质桌面物体”；写出成功标准、失败标准、人工干预规则和安全边界。第一任务暂不选择水、刀具、玻璃或靠近人体的任务。
4. 拍一张工作空间基线照片/短视频，并写下今天对“机器人进入现实生活”的第一条观察。

## Robot Practice

今天不要求机械臂运动。先把 Hardware → Environment → Robot → Camera → Task 的最小闭环画出来，并标注哪些环节已经具备、哪些尚未具备。

## Knowledge

- Robot arm、DoF、end effector、camera、teleoperation、dataset、policy 分别在闭环中做什么。
- “能运行代码”不等于“能完成任务”：任务定义和安全边界同样是系统的一部分。

## Developer Experience

记录：

- 第一次接触这个项目时，不知道哪些信息？
- 哪些硬件/软件依赖目前最模糊？
- 如果官方文档默认用户已经知道某个概念，写下来。

## Content Idea of the Day

- Content Level：**A**
- Hook：**“我准备把一只开源机械臂带进现实生活，但第一步不是学 VLA，而是先算清楚自己到底能不能养得起它。”**
- Core Conflict：想拥有机器人和真实预算、空间、电脑限制之间的冲突。
- Visual Moment：桌面空间、电脑配置、预算/约束清单和第一任务草图同框。
- Experiment：公开建立“第一只开源机械臂”的约束表，并承诺 60 天后用真实结果对照。
- Failure Possibility：发现电脑、空间或预算并不适合原先设想；这个发现本身就是诚实的开场。
- Payoff：观众看到一个可追更的起点，而不是泛泛的学习宣言。
- Platforms：小红书、抖音、Bilibili、YouTube Shorts、X。
- Long-form Potential：可扩展为“普通人第一次买开源机械臂前必须回答的 10 个问题”。

## Website Content Opportunity

暂记为候选：`真实约束下的开源机械臂选型决策`。只有在完成实际比较、购买或替代路径验证后，才值得写成网站文章；今天不做 SEO 规划。

## Assets Created

- `robot-arm/hardware/decision-memo.md`
- `robot-arm/setup/environment-baseline.md`
- 第一任务定义草案
- 工作空间照片/短视频
- 内容选题卡 01

## Portfolio Value

为 Case Study 01（Deployment）的约束与决策证据、Case Study 05（Content Experiment）的起始素材提供基线。

## Reflection

填写：今天哪个约束最可能改变硬件选择？我原来对“机器人能帮普通人”的哪个假设最不确定？

## Tomorrow

用真实约束比较 2–3 条硬件路径，并形成“买/借/租/暂缓”的明确决策。

