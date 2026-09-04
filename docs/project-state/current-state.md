# Current Project State

> 这是当前项目状态的单一事实来源。若本文件与历史研究、旧计划或个人草稿冲突，以本文件和 `PROGRESS.md` 的最新可验证记录为准。
>
> 最后更新：2026-09-04

## State

```text
PROJECT_STATE = ORGANIZED_EXECUTION_BASELINE
CURRENT_STAGE = DAY_2_COMPLETE_PRE_ARRIVAL
CANONICAL_WORKSPACE = D:\embodied-ai-v2-new\embodied-ai-fieldlab
CURRENT_EDIT_WORKSPACE = CANONICAL_WORKSPACE
DAY_2_STATUS = COMPLETE
NODEHEXA_STATUS = PURCHASED_WAITING_FOR_ARRIVAL
READY_FOR_DAY_3 = true
```

## North Star

> 在 60 天内真正做出并运行开源具身机器人，通过六足机器人和机械臂的实际实验，探索它们能做什么，并把过程沉淀为原创内容和作品集。

“桌面 AI 助手”不是总目标，只是未来可能验证的一种应用方向。任何具体任务都必须经过 `Robot Task Research` 和早期实验，不能从旧示例直接升级为最终结论。

## Three Execution Lines

1. **NodeHexa 六足机器人落地**：到货、清点、装配、供电、控制、第一次运动和后续扩展验证。
2. **机械臂具身智能研究**：硬件、遥操作、Camera、数据、策略和真实任务研究；硬件与任务暂不锁死。
3. **内容、Developer Experience 与 Portfolio**：PeterStudio、社交媒体、开发者体验和 Case Study 记录前两条线的真实证据。

SEO 网站是独立项目；本项目最多记录 `SEO Website Content Opportunity`，不执行 SEO 策略。

## Purchased Hardware

```text
ROBOT = NodeHexa V1
KIT = 套餐 B：全套散件（无机盖）·部分组装
BATTERY = 2000mAh 2S LiPo
CHARGER = INCLUDED
PURCHASE_STATUS = PURCHASED
ARRIVAL_STATUS = WAITING
```

购买记录：[2026-09-02 NodeHexa V1 Purchase Log](../../hexapod/logs/2026-09-02-nodehexa-v1-purchase.md)

## Gates

```text
READY_FOR_NODEHEXA_BASE_PURCHASE = SATISFIED_BY_PURCHASE
READY_FOR_NODEHEXA_ARRIVAL_EXECUTION = true
READY_FOR_SENSOR_EXPANSION_PURCHASE = false
READY_FOR_AI_COMPUTE_PURCHASE = false
READY_FOR_ACTUATOR_UPGRADE_PURCHASE = false
READY_FOR_18_SERVO_PURCHASE = false
FINAL_FLAGSHIP_TASK_SELECTED = false
```

## Next Execution Entry

在用户说“开始 Day 3”后，使用 `CONTENT_PRODUCTION_LOOP.md` 中的 Guided Execution Mode，一次只推进一个步骤。当前不重新选购 NodeHexa、不提前采购传感器/AI 计算设备/执行器升级，也不提前锁定最终 Robot Task。

到货后执行顺序：

```text
到货记录
→ 物料清点
→ 打印件/紧固件复核
→ 电池与电源安全检查
→ 结构装配复核
→ 控制软件/固件准备
→ 低风险上电
→ 单动作验证
→ 悬空/站立/基础行走
→ 失败与数据记录
```

## Document Authority

| 信息类型 | 当前权威入口 |
|---|---|
| 总目标与项目范围 | `README.md` |
| 60 天阶段与里程碑 | `ROADMAP.md` |
| 当前进度与阻塞 | `PROGRESS.md` 与本文件 |
| 每日执行方式 | `CONTENT_PRODUCTION_LOOP.md` |
| Day 计划与实际记录 | `daily/day-NN.md` |
| 六足证据与采购研究 | `hexapod/` |
| Robot Task Research | `robot-arm/tasks/task-research.md` |
| PeterStudio 写作人格 | `PERSONA.md` 与 `skills/blog/references/personas/peterstudio-voice.json` |
| 历史方案与设计过程 | `docs/superpowers/`，仅作历史背景 |

## Rules

- 计划文件不能覆盖真实执行结果；真实结果必须回写 `PROGRESS.md` 和对应日志。
- “已购买”不等于“已到货”；“已到货”不等于“已组装”；“已运行”必须有照片、视频、日志或终端证据。
- 历史研究不删除，但必须通过标题、状态或本文件避免被误读为当前决策。
- 不在主工作区和 Codex worktree 之间来回编辑；D 盘主工作区是唯一继续编辑入口。
