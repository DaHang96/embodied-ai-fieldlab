# 60 天 Roadmap

## 北极星结果

60 天结束时，作品集首页能够清晰呈现：

> 我不是只“了解”具身智能，而是实际部署过开源机器人，做过真实任务，研究过开发者上手体验，并能把技术转化为内容、教育材料和生态策略。

## 60 天阶段与里程碑

| 阶段 | 天数 | 重点 | 退出证据 |
|---|---:|---|---|
| M0 项目启动 | Day 1 | 明确定位、约束、设备决策标准和证据格式 | 基线记录、候选路径评分、Day 1 资产 |
| M1 选型与准备 | Day 2–7 | 确认硬件路径、准备环境、拆解文档和第一次内容叙事 | 决策备忘录、环境清单、控制链路计划、2 个高潜内容进入制作 |
| M2 真实部署 | Day 8–14 | 到货验收、安装、环境配置、第一次运动；记录全部摩擦 | First Motion 证据、安装日志、首个 DX Pain Point |
| M3 遥操作与感知 | Day 15–21 | 理解关节/末端/坐标、相机、标定、遥操作和安全边界 | Teleoperation Demo、相机/标定记录、故障复盘 |
| M4 数据闭环 | Day 22–30 | 设计一个现实任务，采集 demonstration，形成最小数据集 | Dataset、任务定义、评估标准、Day 30 复盘 |
| M5 Policy 基线 | Day 31–37 | 使用现成教程或基线完成训练/推理，不为数学细节失控 | Training/Inference 记录、成功率或失败率、Expectation vs Reality 内容 |
| M6 AI 接入 | Day 38–44 | 尝试语言、视觉或 VLA 组件接入，明确决策与动作的边界 | Voice/Language → Decision → Action Demo 或诚实的失败实验 |
| M7 Robot in Real Life | Day 45–51 | 用 7 天 Challenge 测试机器人对真实生活任务的帮助程度 | 连续实验素材、任务评分、观众/用户反馈、内容实验数据 |
| M8 生态与教育资产 | Day 52–56 | 完成生态研究、Developer Experience Case Study 和教程 | 生态比较、教程 + 视频/图文、改进策略 |
| M9 作品集与求职包装 | Day 57–60 | 打磨 5 个 Case Study、职业叙事、Demo 索引和下一步计划 | Portfolio 首页、简历素材、公开链接清单、最终复盘 |

### 动态调整规则

- 硬件未到货：优先推进环境验证、文档研究、仿真/示例控制链路、任务设计和内容准备；不虚构真实机器人结果。
- 硬件故障或环境失败：先保留日志并把失败转成 DX 素材，再切换到最小可行替代路径。
- 某项技术连续投入但没有产生机器人进展、Demo、内容、Portfolio 或职业证据：暂停深挖，改为完成一个可见的小闭环。
- 内容数据不理想：保留实验记录，比较 Hook、画面、时长、平台与叙事，不把单条播放量当作唯一成功标准。
- 新工具或新模型出现：只有在能显著降低实践门槛、提高证据质量或改变职业叙事时才插入；否则记录到 backlog。

## Flagship Projects

### Flagship 1 — I Built My First Open-Source Robot

**目标**：完成从硬件路径决策、到货验收、环境安装、第一次运动、第一次可控任务的完整闭环。

**过程证据**：预算与约束、购买决策、安装日志、版本信息、照片/视频、错误信息、第一次成功与失败。

**最终资产**：部署 Demo、Setup Guide、Troubleshooting Note、硬件真实体验文章/视频。

**对应 Case Study**：Case Study 01 — Open Source Robot Deployment。

### Flagship 2 — Teach My Robot

**目标**：让机器人通过 demonstration / imitation learning 学会一个边界清晰的真实任务。

**过程证据**：任务定义、成功判定、遥操作、数据集样例、训练配置、推理结果、失败分类。

**最终资产**：从 Demonstration 到 Inference 的可复现实验、结果视频和面向非算法读者的解释。

**对应 Case Study**：Case Study 01 + Case Study 03 — Developer Education。

### Flagship 3 — Give My Robot a Brain

**目标**：探索 Voice / Language / Vision / VLA 如何影响机器人动作，明确哪些部分仍需要规则、安全检查或人工确认。

**过程证据**：输入、决策、动作的链路图；成功/失败案例；延迟、误解和安全边界记录。

**最终资产**：AI × Robot 实验 Demo、一篇“ChatGPT 有大脑但没有身体”的解释内容、架构说明。

**对应 Case Study**：Case Study 03 + Case Study 04。

### Flagship 4 — Robot in Real Life

**目标**：用连续 Challenge 测试机器人对普通人真实生活的帮助，而不是只展示一次完美 Demo。

**过程证据**：明确任务、时间限制、失败风险、人工干预次数、完成时间、用户/观众反馈。

**最终资产**：Challenge 系列内容、任务评分表、Expectation vs Reality 复盘。

**对应 Case Study**：Case Study 05 — Technical Content Experiment。

### Flagship 5 — Developer Experience Case Study

**目标**：从新开发者视角研究一个真实开源机器人项目的 Discovery → Documentation → Installation → First Success → Community → Retention。

**过程证据**：每一步的实际耗时、阻塞点、文档截图/链接、错误信息、与成功路径的对照。

**最终资产**：DX Journey Map、Pain Point Backlog、入门教程、Developer Ecosystem 改进提案。

**对应 Case Study**：Case Study 02 — Developer Experience。

## 作品集五个 Case Study 的验收标准

| Case Study | 至少要证明什么 | 必须有的证据 |
|---|---|---|
| 01 Open Source Robot Deployment | 真正部署并使用过机器人 | 设备/环境/日志/视频/任务结果 |
| 02 Developer Experience | 能发现并结构化开发者痛点 | Journey、Pain Points、优先级、改进建议 |
| 03 Developer Education | 能把复杂技术讲清楚并帮助别人复现 | Tutorial、解释内容、复现反馈 |
| 04 Ecosystem Research | 能从生态和 GTM 角度比较项目 | 比较框架、来源、洞察、策略建议 |
| 05 Content Experiment | 能设计、分发、衡量并迭代技术内容 | 选题、脚本、发布记录、数据、迭代结论 |

## 本周以后的每周节奏

每 7 天创建/更新一个 `weekly/week-X.md`，回答本周复盘问题，并重新确认：

1. 下一周唯一最重要的机器人结果是什么？
2. 哪个内容值得制作，哪个只保留为素材？
3. 哪个 DX 痛点最值得写成 Case Study？
4. 哪个学习任务应删除或延后？
5. 下周必须交付什么 Portfolio Evidence？

Day 30 另做一次中期定位复盘，必须回答“我的差异化是否已经从学习者变成实践者 + 生态观察者 + 技术内容创作者”。

