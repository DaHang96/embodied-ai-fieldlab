# Phase 0 Workspace Reconciliation

> 日期：2026-09-04
> 状态：Phase 0 已完成；本文件只记录工作区对齐，不代表核心文档已重写。

## Canonical Workspace

正式项目目录确定为：

`D:\embodied-ai-v2-new\embodied-ai-fieldlab`

正式项目分支当前为：`main`

Phase 0 审计时的本地提交：`3971351`

后续项目状态、实验记录、内容草稿和 Git 提交都应以此目录为源头。

## Source Worktree

本次资料来源为：

`C:\Users\zhanghang\.codex\worktrees\fa68\embodied-ai-fieldlab`

来源分支：`docs/peter-studio-robot-workbench-direction`

来源提交：`74000b6`

该 worktree 保留原样，暂不删除、重置或继续作为正式执行目录。

## Migrated Files

以下 5 份文件原来只存在于 Codex worktree，已复制到正式项目目录；复制过程中没有覆盖 D 盘现有文件：

- `hexapod/logs/2026-09-02-nodehexa-v1-purchase.md`
- `hexapod/research/project-comparison.md`
- `hexapod/research/nodehexa-v1-final-base-kit-procurement-audit.md`
- `hexapod/research/nodehexa-v1-hardware-expansion-audit.md`
- `hexapod/research/v2-one-leg-servo-prototype-selection.md`

迁移策略是保留研究证据，后续再在核心状态文件中明确哪些内容已被 NodeHexa 当前决策取代；本阶段没有删除历史路线。

## D-Drive-Only Assets

以下内容以 D 盘版本为准，没有用 worktree 版本覆盖：

- `PERSONA.md`
- `skills/blog/references/personas/peterstudio-voice.json`
- `content/ideas/2026-09-03-peter-studio-log-00-first-robot.md`

其中 `PERSONA.md` 和 `PeterStudio Voice v1.0` 是 PeterStudio 文章的规范来源。

## Known Differences To Resolve In Phase 1

Phase 0 只完成文件归并，以下问题保留到核心文档整理阶段：

1. `README.md`、`ROADMAP.md` 和部分任务研究文件仍残留“桌面 AI 助手是总目标”的旧叙事。
2. `CONTENT_PRODUCTION_LOOP.md` 仍有以桌面 AI 助手为中心的旧内容 Hook，需要改为通用的机器人能力/实验叙事。
3. `PROGRESS.md` 需要统一为“Day 2 采购决策已完成，NodeHexa 等待到货”。
4. NodeHexa 采购审计中存在 `B + 850mAh / ¥619` 的旧推荐与实际购买的 `B + 2000mAh / 约¥634` 并存问题。
5. `daily/day-03.md` 至 `daily/day-07.md` 需要标记为原计划模板，不能伪装成已执行。
6. `robot-arm/tasks/` 需要保留历史路径，但改用通用 Robot Task Research / Selection 命名。
7. 项目根目录的临时截图、上游快照和淘宝中间产物需要在后续 `.gitignore` 与资产归档阶段处理；本阶段不删除它们。

## Phase 0 Safety Notes

- 未执行 `git reset`、`git checkout` 或删除操作。
- 未覆盖 D 盘任何现有文件。
- 未修改 README、ROADMAP、PROGRESS、Day 文件或 Persona 文件。
- worktree 原始 5 份研究文件仍然保留，可用于逐项校验。

## Phase 1 Entry Condition

进入 Phase 1 前，正式项目中已经具备：

- PeterStudio Persona 与 Voice；
- NodeHexa 采购与研究档案；
- 三条主线所需的历史证据；
- 一个明确的正式项目目录。

Phase 1 将只整理状态、叙事和执行顺序，不重新研究或采购 NodeHexa。
