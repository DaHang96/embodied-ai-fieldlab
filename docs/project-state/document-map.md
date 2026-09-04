# Project Document Map

## 使用顺序

1. 先读 [`current-state.md`](current-state.md) 了解当前状态和决策边界。
2. 再读 [`PROGRESS.md`](../../PROGRESS.md) 了解已完成证据、阻塞和下一入口。
3. 需要规划时读 [`ROADMAP.md`](../../ROADMAP.md) 和对应 `daily/day-NN.md`。
4. 需要证据时读 `hexapod/`、`robot-arm/`、`developer-experience/` 和 `content/`。
5. 换电脑时读根目录 [`PORTABILITY.md`](../../PORTABILITY.md)，不要假设用户级工具和硬件环境已恢复。

## 生命周期

| 目录/文件 | 角色 | 是否可作为当前决策依据 |
|---|---|---|
| `README.md` | 项目范围与总叙事 | 是 |
| `ROADMAP.md` | 阶段、里程碑和调整规则 | 是 |
| `PROGRESS.md` | 当前进度 Dashboard | 是 |
| `CONTENT_PRODUCTION_LOOP.md` | 长期执行协议 | 是 |
| `docs/project-state/` | 状态、归并和治理记录 | 是；按更新时间读取 |
| `daily/`、`weekly/` | 计划、执行记录和复盘 | 是；真实结果优先 |
| `hexapod/`、`robot-arm/` | 研究、实验和采购证据 | 是；需要查看报告状态 |
| `content/` | 内容草稿和选题 | 不是项目状态来源 |
| `docs/superpowers/` | 历史规格、计划和设计过程 | 默认否，仅作背景 |

## 历史文件规则

历史文件不删除。若其中的目标、价格、路线或状态被后续决策取代，应在文件开头增加“历史/已被取代”说明，并在 `current-state.md` 中保留当前结论。

## Workspace Rule

当前电脑的主工作区是：

```text
当前 clone 的实际根目录
```

当前 Codex worktree 仅作为待审查的旧工作副本，不继续编辑，不自动合并，不删除。换电脑后不需要复现这个 worktree 路径。
