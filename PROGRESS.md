# Project Progress Dashboard

> 当前状态权威入口：[`docs/project-state/current-state.md`](docs/project-state/current-state.md)
> 最后更新：2026-09-04｜当前执行阶段：Day 2 已完成，NodeHexa 到货前准备 / 60

## Day

- [x] Day 01
- [x] Day 02
- 总进度：**Day 2 已完成；当前处于 NodeHexa 到货前准备阶段**
- 当前阶段：M1 开源机器人路线、硬件选型与准备
- 当前唯一优先结果：完成 NodeHexa V1 到货前准备；到货后从清点、装配复核、安全上电和首次运动开始

## Robot

当前路径状态（三条执行线并行）：

`Hardware Ordered` → `Hardware Arrived` → `Setup` → `Teleoperation` → `Data Collection` → `Training` → `Inference` → `Real Task`

| 轨道 / 节点 | 状态 | 证据位置 |
|---|---|---|
| 六足 / NodeHexa V1 — Hardware Ordered | **已完成**：用户已购买官方基础套件；套餐 B、2000mAh 电池、含充电器、部分组装 | 用户采购决策；待补订单/到货证据 |
| 六足 / 到货前准备 | **进行中**：整理验收、装配、安全供电与首次运动流程 | `docs/project-state/phase-1-execution-realignment.md` |
| 六足 / Hardware Arrived | 未开始 | 待到货验收记录 |
| 六足 / Setup → First Motion | 未开始 | 待建立六足硬件记录 |
| 六足 / Teleoperation → Real Task | 未开始 | 待建立实验记录 |
| 机械臂 / Hardware Ordered → Real Task | 未开始 | `robot-arm/hardware/`、`robot-arm/experiments/` |
| 内容 / PeterStudio + Social + Portfolio | **持续记录**：围绕真实机器人进展，不预设任务结论 | `content/`、`portfolio/`、`PERSONA.md` |

## Content

| 指标 | 当前值 | 目标/说明 |
|---|---:|---|
| Ideas | 7 | Week 1 每天至少 1 个 |
| Drafts | 1 | PeterStudio #00 已完成初稿，待事实复核与后续发布处理 |
| Scripts | 0 | 至少把 2 个高潜选题推进到脚本/拍摄准备 |
| Published | 0 | 不强制每天发布，优先保证真实素材 |
| S-Level Content | 2 个已预选 | Day 7 根据真实素材确认是否进入制作 |
| Best Performing Content | N/A | 发布后记录平台、播放、完播、互动和反馈 |

## Developer Ecosystem

| 指标 | 当前值 |
|---|---:|
| Projects Studied | 0 |
| Developer Pain Points Found | 0 |
| Tutorials Created | 0 |
| Community Contributions | 0 |

## Portfolio

| Case Study | 进度 | 当前证据 |
|---|---:|---|
| 01 Open Source Robot Deployment | 0% | 尚未开始 |
| 02 Developer Experience | 0% | 尚未开始 |
| 03 Developer Education | 0% | 尚未开始 |
| 04 Embodied AI Ecosystem Research | 0% | 尚未开始 |
| 05 Technical Content Experiment | 0% | 尚未开始 |

## Career

- Target Roles：见 [`career/target-roles.md`](career/target-roles.md)
- Target Companies：待 Day 2–7 建立筛选表
- JD Studied：0
- Applications：0

## 最近完成的资产

| 日期 | 资产 | 路径 | 进入哪个 Case Study |
|---|---|---|---|
| Day 1 | 桌面环境基线照片、环境实测记录、临时实验规格 | `assets/day-01/desk-baseline.jpg` / `daily/day-01.md` / `robot-arm/setup/environment-baseline.md` | 01 Open Source Robot Deployment / 02 Developer Experience / 05 Technical Content Experiment |
| 2026-09-03 | NodeHexa V1 基础套件采购决策 | 用户确认：套餐 B、2000mAh 电池、含充电器、部分组装；等待到货 | 01 Open Source Robot Deployment / 02 Developer Experience / 05 Technical Content Experiment |
| 2026-09-03 | PeterStudio #00 文章初稿 | `content/ideas/2026-09-03-peter-studio-log-00-first-robot.md` | 01 Open Source Robot Deployment / 04 Embodied AI Ecosystem Research / 05 Technical Content Experiment |
| 2026-09-04 | Phase 1 项目归并与执行重排 | 统一总目标、三条执行线、到货前状态和到货后顺序；保留旧研究路径 | `docs/project-state/phase-1-execution-realignment.md` |
| — | 项目初始化 | `README.md` / `ROADMAP.md` | 全部 |

## 当前阻塞与决定

- 当前阻塞：NodeHexa V1 尚未到货；到货验收、安装、供电、固件/控制链和首次运动尚未开始。机械臂仍未落地，Camera/AI 扩展也未进入实物验证。
- 已完成决定：比较多个开源六足项目后，首台实体机器人选择官方 NodeHexa V1 基础套件；用户已完成购买，当前状态只能记为 Hardware Ordered，不能提前写成已到货或已运行。
- 当前策略：NodeHexa 负责先建立可运行的具身机器人基线；机械臂继续作为并行研究路线；内容、Developer Experience 和 Portfolio 同步记录；最终任务与 AI 扩展根据真实实验结果再决定。
- 风险：硬件物流/兼容性、环境依赖、内容拍摄能力、时间不足。

### Guided Execution 更新

- Step 1 已完成：机械臂预算 2000，配件/摄像头额外预算 1000；工作日每天 2 小时、周末每天 3 小时，按满周估算约 16 小时；Remote GPU 使用实验室远程 SSH；可接受硬件等待 5 天。
- Step 2 已完成：Windows PowerShell `nvidia-smi` 确认 NVIDIA GeForce RTX 3060 Laptop、6144 MiB 显存、驱动 561.17、驱动报告 CUDA 12.6；当时 GPU 利用率 4%。
- Step 3 已完成：Windows 10 Home China / OS Build 26200；AMD Ryzen 7 5800H；约 16 GB RAM；C 盘约 200 GB，剩余约 21.9 GB。
- Step 4 已完成：检测到 Integrated Camera（PnP OK）；WSL 默认版本 2；实验室远程 SSH 可用。初步采用 Windows 本地 + WSL2/Remote GPU 分工。
- Step 5 已完成：桌面约 150 × 50 × 100 cm，木质，可固定底座；附近无墙、显示器或其他障碍物；无宠物、儿童或他人进入风险；无额外噪音或运动范围限制。
- Step 6 已定义：临时基线实验为抓取并移动折叠后的面巾纸，必要时切换为小海绵/软布；目标是连续 5 次至少成功 3 次，每轮最多 10 次，并记录失败与人工干预。该实验不等于最终 Flagship Task。
- Step 7 已完成：保存桌面全景基线照片；观察到实际工作区存在笔记本支架、键盘、鼠标、饮品、杂物、线缆和两侧架体，后续需要先清空并规划可重复工作区。
- 仍未确认：WindowsDisplayVersion、CUDA Toolkit、摄像头实际采集、Python/机器人依赖、实验室 SSH 连接细节和最终硬件路径。
- Day 1 验收：核心基线已完成；机械臂动作、机器人 Camera 采集和候选任务研究仍未完成。桌面照片已保存为 `assets/day-01/desk-baseline.jpg`，暂定 Personal Blog Write、Social Media A，SEO Website Skip。
- Day 2 Step 1 已完成：确认当前无机械臂、无配套设备、无借用渠道；候选研究按机械臂 2000、配件/摄像头 1000、5 天等待和数据闭环约束进行。
- Day 2 路线决策已完成：在多个开源六足项目中选择 NodeHexa V1 作为首台实体机器人，并购买官方基础套件；Day 2 现已完成，当前等待到货，后续从验收而不是重新选购开始。
- Phase 1 已完成文件归并与执行重排：D 盘主项目作为唯一编辑入口；Codex worktree 暂停编辑，Git 分支尚未合并。

## 更新规则

- 每天结束时更新 Day、Robot、Content、DX、Portfolio 和阻塞项。
- 每完成一个资产，就写入“最近完成的资产”，附上路径和证据。
- 每周复盘后更新下一周的唯一关键结果，并删除低价值任务。
- 进度只按可验证证据推进，不按阅读页数或“感觉学会了”推进。
