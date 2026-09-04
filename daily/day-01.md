# Day 01

## Today's Goal

建立项目基线：明确时间、预算、设备、空间、安全与早期实验任务的约束，让后续六足机器人落地、机械臂研究、Robot Task Research 和内容方向有真实依据。

## Project Content Line

> 我正在用 60 天做出并运行开源具身机器人，看看它们在真实世界里到底能做什么。

具体任务和应用叙事暂不预设；先通过 [task-research.md](../robot-arm/tasks/task-research.md) 和早期实验寻找答案。

本日执行遵循 [`CONTENT_PRODUCTION_LOOP.md`](../CONTENT_PRODUCTION_LOOP.md)。下面的 `Content Idea of the Day` 只是实验前预案；完成 Day 1 后，以真实发生的结果、证据和意外情况重新判断最值得讲的故事。

## Guided Execution Record

### Step 1：时间与预算

状态：已完成。

- 机械臂预算上限：2000；
- 配件/摄像头额外预算：1000；
- 工作日投入：每天 2 小时；
- 周末投入：每天 3 小时；
- 按满周估算：约 16 小时/周；
- Remote GPU：使用实验室远程 SSH，暂无个人月度预算；
- 可接受硬件等待时间：5 天。

这组信息已同步到 [`decision-memo.md`](../robot-arm/hardware/decision-memo.md)。每周投入仍以实际执行记录为准。

### Step 2：电脑与 GPU

状态：已完成。

- OS：Windows 10 Home China，OS Build 26200；
- GPU：NVIDIA GeForce RTX 3060 Laptop；
- 显存：6144 MiB（6 GB）；
- 驱动：561.17；
- `nvidia-smi` 报告的 CUDA 版本：12.6；
- 当时显存占用：1547 / 6144 MiB；
- 当时 GPU 利用率：4%。

已同步到 [`environment-baseline.md`](../robot-arm/setup/environment-baseline.md) 和 [`decision-memo.md`](../robot-arm/hardware/decision-memo.md)。CUDA Toolkit 尚未验证。

### Step 3：系统、CPU、RAM 与磁盘

状态：已完成。

- 系统：Windows 10 Home China，OS Build 26200；
- CPU：AMD Ryzen 7 5800H；
- RAM：约 16 GB；
- C 盘：约 200 GB，总剩余约 21.9 GB；
- WindowsDisplayVersion：未返回，待确认。

已同步到 [`environment-baseline.md`](../robot-arm/setup/environment-baseline.md) 和 [`decision-memo.md`](../robot-arm/hardware/decision-memo.md)。磁盘剩余空间偏紧，后续需要控制数据集和模型文件占用。

### Step 4：摄像头与 Linux 环境

状态：已完成。

- 摄像头：`Integrated Camera`，PnP 状态 `OK`；
- WSL：默认版本 2；
- 实验室远程 Linux：SSH 已确认可用；
- 初步架构：Windows 本地负责机器人控制、Camera、遥操作、数据采集和轻量推理；WSL2/实验室 SSH 用于 Linux 工具链和较重实验。

已同步到 [`environment-baseline.md`](../robot-arm/setup/environment-baseline.md) 和 [`decision-memo.md`](../robot-arm/hardware/decision-memo.md)。摄像头实际画面、Python/机器人依赖和远程 SSH 连接细节仍待验证。

### Step 5：桌面空间与安全边界

状态：已完成。

- 桌面约 150 × 50 × 100 cm（长 × 宽 × 高），材质为木头；
- 机械臂放置位置灵活，底座可以固定；
- 附近无墙、显示器或其他障碍物；
- 无宠物、儿童或他人进入实验区域；
- 当前无额外噪音或运动范围限制；
- “允许接触”和“禁止接触”均填写为“都可以”，暂按暂无特定禁触物体记录；实际实验仍默认排除刀具、玻璃、液体、易碎品和靠近人体的动作。

已同步到 [`environment-baseline.md`](../robot-arm/setup/environment-baseline.md) 和 [`decision-memo.md`](../robot-arm/hardware/decision-memo.md)。

### Step 6：第一项临时安全实验

状态：已定义，尚未执行。

- 实验对象：优先使用折叠后的面巾纸；如果太轻、太软或无法稳定夹取，切换为小海绵或软布；
- 任务：从起始 A 区抓取，抬升约 3 cm，移动到目标 B 区并释放；
- 成功标准：无人工救援完成完整动作，连续 5 次中至少成功 3 次；
- 最多尝试次数：每轮最多 10 次，并记录成功率、失败类型和人工干预；
- 允许人工干预：动作停止后重新摆放物体、重新定位起点或执行安全急停；动作中不得触碰机械臂或代替它完成抓取；
- 立即停止：底座松动、碰撞、异常抖动或噪音、物体接近桌边、线缆受拉、人员进入区域、发热/异味，或任何无法确认安全的情况。

这是用于硬件和数据闭环验证的临时实验载体，不是最终 Flagship Task。已同步到 [`decision-memo.md`](../robot-arm/hardware/decision-memo.md)。

### Step 7：桌面环境基线证据

状态：已完成。

- 已保存桌面全景照片：[`assets/day-01/desk-baseline.jpg`](../assets/day-01/desk-baseline.jpg)；
- 第一条观察：桌面面积足够，但现实工作区被笔记本支架、键盘、鼠标、饮品、杂物、线缆和两侧架体占据；机械臂进入真实生活后，首先要解决的是在杂乱桌面中找到安全、可重复的工作空间；
- 工程含义：后续需要先规划可重复清空的机械臂工作区，并验证 Camera 对桌面边界、物体和线缆的可见性；这张照片本身不代表机器人 Camera 已完成采集验证。

已同步到 [`environment-baseline.md`](../robot-arm/setup/environment-baseline.md) 和 [`decision-memo.md`](../robot-arm/hardware/decision-memo.md)。

## Why It Matters

如果不先写约束，60 天很容易变成阅读 ROS2、VLA 和论文的学习清单。今天的结果会直接影响机器人路径、第一周内容和最终作品集的可信度。

## Tasks

1. 复制本文件中的“项目基线”问题，写入 `robot-arm/hardware/decision-memo.md`：预算上限、每周可投入时间、桌面空间、电脑系统/GPU/RAM、相机、噪音/安全限制、可接受的到货等待时间。
2. 记录本地环境基线：OS、Python、GPU/显存、可用磁盘、是否能使用 Linux/WSL/远程 Linux；只记录事实，不急着修环境。
3. 选择一个用于早期验证的安全任务，例如“抓取并移动一个软质桌面物体”；写出成功标准、失败标准、人工干预规则和安全边界。它只是实验载体，不是最终 Flagship Task。暂不选择水、刀具、玻璃或靠近人体的任务。
4. 拍一张工作空间基线照片/短视频，并写下今天对“机器人进入现实生活”的第一条观察。
5. 将当前想到的机器人任务和可能的助手体验记录到 [task-research.md](../robot-arm/tasks/task-research.md)，标注“尚未调研、尚未评分”。

## Compute Plan

电脑方案：**RTX 3060 Laptop + Remote GPU**。

- 本地机器人控制、Camera、Teleoperation、数据采集、数据检查、轻量推理和调试；
- Remote GPU 训练 Policy、运行较大模型实验，以及必要时进行 VLA Fine-tuning；
- 最终链路：本地机器人/数据采集 → Remote GPU 训练 → 本地推理 → 真实机器人任务。

## Robot Practice

今天不要求任何机器人运动。先把 Hardware → Environment → Robot → Camera → Task 的最小闭环画出来，并标注哪些环节已经具备、哪些尚未具备。

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
- Hook：**“我决定用 60 天做出一台真正会动的开源机器人，但第一天发现：连它该做什么都还没决定。”**
- Core Conflict：软件想法可以很快写出来，物理机器人却需要真实空间、预算、硬件和一个值得反复实验的任务。
- Visual Moment：桌面空间、RTX 3060 Laptop、候选任务卡片、软质物体和安全边界同框。
- Experiment：公开建立机器人项目的约束表与 Robot Task Research 入口，记录哪些方向值得继续验证。
- Failure Possibility：发现预算、空间、电脑或机械臂能力无法支持某个想法；淘汰候选本身就是有效结果。
- Payoff：观众看到一个有明确问题、可持续追更的真实起点，而不是泛泛的“我要学机器人”。
- Platforms：小红书、抖音、Bilibili、YouTube Shorts、X。
- Long-form Potential：可扩展为“普通人第一次买开源机械臂前必须回答的 10 个问题”。

## Today's Capture List

### Must Capture

- 改动前的工作空间全景；
- RTX 3060 Laptop 和当前电脑配置状态；
- 预算、时间、空间、安全和设备约束表；
- 当前候选任务卡片；
- 早期实验物体和任务草图；
- 今天关于“机器人如何进入现实生活”的第一条观察。

### Nice to Have

- 桌面和电脑的近景；
- 候选任务卡片的不同角度；
- 用户与桌面同框；
- 约束表、物体和项目文件同时入镜的 B-roll。

### Technical Evidence

- OS、Python、GPU/显存、可用磁盘和 Camera 信息；
- `robot-arm/hardware/decision-memo.md`；
- `robot-arm/setup/environment-baseline.md`；
- `robot-arm/tasks/task-research.md`；
- Local Robot + Remote GPU 分工记录；
- 尚未验证的项目边界和待补信息。

### Human / Story Moments

- 看到预算或空间限制时的真实反应；
- 对最终任务尚未确定的困惑；
- 放弃某个候选方向的瞬间；
- 发现“软件能力”和“拥有身体的机器人”之间差距的瞬间；
- 对 60 天目标最不确定的地方。

## Safety Reminder

Day 1 不要求机械臂运动。不要为了拍摄引入刀具、玻璃、高温物体、液体，或在运行中的机械臂附近补拍镜头。未来所有动作拍摄都遵循 [`CONTENT_PRODUCTION_LOOP.md`](../CONTENT_PRODUCTION_LOOP.md) 中的安全与真实性规则。

## Day Acceptance

状态：核心任务已完成（基线建立），硬件动作尚未开始。

### 已完成

- 记录了预算、投入时间、Remote GPU 和硬件等待约束；
- 确认 Windows 10、Ryzen 7 5800H、约 16 GB RAM、RTX 3060 Laptop 6 GB；
- 确认 Integrated Camera、WSL2 和实验室远程 SSH；
- 记录桌面尺寸、固定能力和安全边界；
- 定义了不等于最终 Flagship Task 的临时抓取移动实验；
- 保存真实桌面环境照片和第一条生活化观察。

### 尚未完成

- 尚未购买或接入机械臂；
- 尚未验证机器人 Camera 实际采集、Python/机器人依赖和远程 SSH 连接细节；
- 尚未执行临时抓取实验；
- 尚未完成 15–30 个候选生活任务的调研、评分和最终选择。

### 今日真实资产

- 桌面环境基线照片：[`assets/day-01/desk-baseline.jpg`](../assets/day-01/desk-baseline.jpg)；
- GPU、OS、CPU、RAM、磁盘和 Camera/WSL 实测记录；
- 临时安全实验定义；
  - 一条关键观察：机器人必须面对真实杂乱环境，而不是只在理想化实验台上工作。

## Content Processing

### Personal Blog

Write。建议记录今天的真实起点、设备约束和“桌面面积够，但实际可用空间被日常物品切碎”的观察。

### Social Media

A。首选内容角度：**“我想做一台真正会动的机器人，第一天先发现它需要面对一张真实的桌子。”** 真实桌面照片、RTX 3060 和尚未确定的任务方向共同构成第一条内容的冲突。

### Portfolio

保留桌面照片、环境基线、约束决策和临时实验规格，作为项目从真实环境出发的第一组证据。

### SEO Website Opportunity

暂不单独制作 SEO 页面；当前证据量不足，先作为 Personal Build Log 的 Day 1 记录。

## Close

- Day 1 进展：完成从“想做机器人”到“明确真实环境约束”的基线建立；
- 已自动更新：`daily/day-01.md`、`robot-arm/hardware/decision-memo.md`、`robot-arm/setup/environment-baseline.md`、`PROGRESS.md`，并保存 `assets/day-01/desk-baseline.jpg`；
- 下一次继续：从硬件路径与候选 Robot Task Research 开始，不预设最终 Flagship Task。

## Definition of Done

完成后向 Codex 汇报：实际完成了什么、哪些内容仍为空白、证据文件/照片路径、真实耗时、意外发现和初始 Developer Pain Point。Codex 会先更新 Project Record，再独立判断 Personal Blog、Social Media、Portfolio Evidence 和 SEO Website Content Opportunity；不会直接把本日预案当成最终稿。

## Website Content Opportunity

暂记为候选：`真实约束下的开源机械臂选型决策`。只有在完成实际比较、购买或替代路径验证后，才值得写成网站文章；今天不做 SEO 规划。

## Assets Created

- `robot-arm/hardware/decision-memo.md`
- `robot-arm/setup/environment-baseline.md`
- `robot-arm/tasks/task-research.md` 初始候选任务方向
- 一个安全早期实验任务定义草案
- 工作空间照片/短视频
- 内容选题卡 01

## Portfolio Value

为 Case Study 01（Deployment）的约束与决策证据、Case Study 05（Content Experiment）的起始素材提供基线。

## Reflection

填写：今天哪个约束最可能改变硬件选择？我原来对“机器人能帮普通人”的哪个假设最不确定？

## Tomorrow

用真实约束比较 2–3 条硬件路径，并形成“买/借/租/暂缓”的明确决策。
