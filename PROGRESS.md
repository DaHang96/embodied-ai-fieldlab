# Project Progress Dashboard

> 最后更新：2026-08-31｜当前执行日：Day 2 / 60

## Day

- [x] Day 01
- [ ] Day 02
- 总进度：**1 / 60（Day 1 核心基线已完成）**
- 当前阶段：M0 项目启动 / Day 2 硬件与任务调研
- 今日唯一优先结果：完成候选机械臂路径和候选生活任务的证据化比较

## Robot

当前路径状态：

`Hardware Ordered` → `Hardware Arrived` → `Setup` → `Teleoperation` → `Data Collection` → `Training` → `Inference` → `Real Task`

| 节点 | 状态 | 证据位置 |
|---|---|---|
| Hardware Ordered | 未开始 | `robot-arm/hardware/` |
| Hardware Arrived | 未开始 | `robot-arm/hardware/` |
| Setup | 未开始 | `robot-arm/setup/` |
| Teleoperation | 未开始 | `robot-arm/experiments/` |
| Data Collection | 未开始 | `robot-arm/experiments/` |
| Training | 未开始 | `robot-arm/experiments/` |
| Inference | 未开始 | `robot-arm/experiments/` |
| Real Task | 未开始 | `robot-arm/demos/` |

## Content

| 指标 | 当前值 | 目标/说明 |
|---|---:|---|
| Ideas | 7 | Week 1 每天至少 1 个 |
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
| — | 项目初始化 | `README.md` / `ROADMAP.md` | 全部 |

## 当前阻塞与决定

- 阻塞：最终硬件型号、机器人 Camera 实际采集、Python/机器人依赖和候选任务研究尚未完成。
- 决定：Day 1–2 先做约束收集和候选路径评分；在证据不足前不把购买写成已完成。
- 风险：硬件物流/兼容性、环境依赖、内容拍摄能力、时间不足。

### Peter Studio 方向决策（2026-08-31）

- `peterstudio.online` 将重建为 Peter Studio 个人机器人工作台与 Physical AI Build Log，使用原创的桌面实验室、临时拼装、手写笔记、失败记录和漫画式分镜表达两个机器人真实成长过程。
- **机械臂与六足机器人采用并行双轨**：机械臂偏操作与桌面 AI 助手研究，六足机器人偏移动、探索与角色研究；两者都可以成为 Peter Studio 的角色与传播主体。
- 六足机器人先通过可复现的 GitHub 开源项目完成仿真或实体落地；机械臂研究同步进行，先推进生态、硬件路径、任务和数据闭环研究，不要求立即部署。
- Camera、Microphone、Speaker、Screen、LLM/VLM、控制、日志和内容流程可以共享，但不预设固定投入比例，也不要求两个机器人同步达到相同成熟度。
- 具体生活任务和最终 Flagship Task 仍保持开放，继续通过任务调研、评分和早期实验决定。
- `bimanual.org` 继续作为独立的具身智能资讯与 SEO 网站；Peter Studio 记录“我正在造什么”，而不是复制资讯站内容。
- 下一步继续使用 Guided Execution Mode，从当前未完成的 Day 2 任务调研状态推进；不会自动生成 Day 3 或 Day 8–14。

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

## 更新规则

- 每天结束时更新 Day、Robot、Content、DX、Portfolio 和阻塞项。
- 每完成一个资产，就写入“最近完成的资产”，附上路径和证据。
- 每周复盘后更新下一周的唯一关键结果，并删除低价值任务。
- 进度只按可验证证据推进，不按阅读页数或“感觉学会了”推进。
