# Guided Execution Mode 设计记录

## 目标

将当前项目的 Day 执行方式从“输出完整 Markdown 清单”升级为教练式、逐步推进的对话执行。对话是执行入口，Markdown 是后台记录；用户主要负责回答问题、执行操作、做实验、拍素材和汇报真实结果，Codex 负责检查、记录、更新和动态调整。

## 存放位置与优先级

- 完整规则追加到根目录 `CONTENT_PRODUCTION_LOOP.md`。
- `Guided Execution Mode` 位于原有 Daily Content Production Loop 触发协议之前，并明确优先于“一次性展示完整 Day Markdown”的方式。
- `README.md` 增加简短入口说明。
- 现有 `daily/day-01.md` 至 `daily/day-07.md` 保留为后台计划和记录模板，本轮不修改其内容、不启动 Day 1，也不生成 Day 8–14。

## Guided Execution Mode

当用户说 `开始 Day N` 时，先用简短 Brief 说明当天最终目标、重要性和阶段数量，然后立即进入 Step 1。一次只推进一个实际步骤，不一次性抛出全部 Tasks。

每个 Step 使用固定结构：

```text
### Step X：名称
目的：一句话
你现在要做：具体动作
请回复我：需要返回的信息或结果
Capture：只有这一步值得保存时才提醒
```

如果需要用户提供信息，给出可以直接复制回答的模板；如果需要用户操作，给出明确的 PowerShell/应用操作指令，一次最多 1–3 个相关操作。每一步完成后检查结果，判断是否成功，自动更新对应 Markdown，再进入下一步。

## 动态执行原则

- 检查信息是否足够，发现矛盾或缺口时先指出并补问。
- 用户不手动维护项目 Markdown；Codex 将同一事实整理到所有真正需要更新的文件。
- 原计划只是路线参考，真实执行结果优先；系统不兼容、意外失败、意外成功或新发现都可以改变当天路线。
- 每一步明确区分 Must 和 Optional，避免把拍摄、实验、写作和发布混成同一个硬性任务。
- Capture List 嵌入对应执行步骤，在真实动作或关键结果发生前提醒 Must Capture，并等待用户确认准备好；不要求用户记住整天清单。
- 执行阶段只提醒捕捉素材、证据和数据，不打断用户生成标题、封面、博客正文或完整脚本。

## Day Acceptance 与 Content Processing

核心任务完成后，先输出 Day Acceptance：完成了什么、没完成什么、原因和产生的真实资产。然后进入 Content Processing Phase：

1. Personal Blog：Write / Weekly / Skip；
2. Social Media：S / A / B / C / Skip；
3. Portfolio：当天产生的证据；
4. SEO Website Opportunity：有 / 无。

只有值得发布时才生成对应 Publishing Pack。最后输出项目进展、已自动更新的文件和下次继续时的起点；不自动展开 Day N+1，除非用户明确要求。

## 触发协议

### `开始 Day N`

输出顺序为：

1. Phase 0 — Brief：最终目标、为什么重要、预计几个阶段；
2. Phase 1 — Step-by-Step Execution：立即开始 Step 1；
3. 每次只展示一个 Step，并等待用户回复；
4. Phase 2 — Verify：检查结果、更新文件、决定下一步。

不在开场一次性输出完整 Day Markdown 清单；当天 Capture 只在相关步骤前按需提醒。

### `Day N 完成，结果如下……`

收到真实结果后，执行 Reality Check、Project Record 更新、Day Acceptance、Content Processing、Portfolio/SEO 判断和 Close。原有 Personal Blog、Social Media、Portfolio、SEO 和真实性规则继续有效。
