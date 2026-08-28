# Daily Content Production Loop 设计记录

## 目标

为 `embodied-ai-60days` 增加一套长期执行规则，使每个 Day 的真实机器人/AI 助手实践都能在不牺牲安全与真实性的前提下，持续沉淀为 Project Record、Personal Build Log、Social Media Content、Portfolio Evidence 和 SEO Website Content Opportunity 标记。

## 存放与影响范围

- 完整规则新增到项目根目录 `CONTENT_PRODUCTION_LOOP.md`。
- `README.md` 增加简短入口，并明确 Personal Build Log 与独立的 Embodied AI SEO Website 不属于同一项目。
- `daily/day-01.md` 增加执行前预案、Today's Capture List、真实结果优先和安全拍摄提示的衔接。
- 保留现有 `Content Idea of the Day`，将其定义为实验前预案，实验完成后允许被真实结果完全改写。
- 不改变现有 Roadmap、Developer Experience、Portfolio 核心结构。
- 不生成 Day 8–14。

## Daily Content Production Loop

每个 Day 采用以下闭环：

`开始 Day N → 当天任务 + Today's Capture List → 用户执行真实实验 → 用户汇报真实结果 → 更新项目记录 → Personal Blog 判断与 Publishing Pack → Social Media 判断与 Publishing Pack → Portfolio Evidence → SEO Website Content Opportunity 标记`

实验前不写死最终故事。意外成功、失败、报错、视觉画面、真实 Developer Pain Point 或有趣的人机互动，都可以让执行后的内容方向取代原有预案。

## 实验前输出

当用户说“开始 Day N”时，输出 Today's Goal、核心 Tasks、Robot/AI Assistant Practice、Knowledge、Today's Capture List、Safety Reminder 和 Definition of Done。Capture List 分为 Must Capture、Nice to Have、Technical Evidence、Human / Story Moments；当天的 Content Idea 作为预案，不是最终脚本。

Capture List 必须提醒记录开始状态、关键动作、第一次成功/失败、最终结果、Before/After、终端/错误/配置/版本、Dataset、Robot State、Camera、Calibration、Logs、Success Rate、Timing、Hardware Connection，以及真实反应、困惑、决策、放弃方案和角色化瞬间。

## 安全与真实性

拍摄不能影响机器人安全。禁止为了镜头重现危险动作、靠近运行中的机械臂、故意制造危险失败、使用刀具/玻璃/高温物体/液体，或在人体附近执行未经验证的动作。安全与镜头冲突时安全优先。

禁止制造假的“第一次”、把仿真说成真实机器人、把准备购买说成已购买、把未经测试的方案写成确定教程、隐藏关键失败、夸大结果或伪造数据、成功率、反馈和情绪。缺失镜头只能安全补拍静态或非首次素材，不能伪造已经发生的事件。

## 实验后 Reality Check

当用户说“Day N 完成”并提供结果后，先整理实际完成、未完成、Success、Failure、Error、Experiment Result、Data、时间成本、意外情况、照片/视频/Screenshot、真实感受、Developer Pain Point 和证据，再判断今天真正值得讲的故事。

## Publishing Decision

Social Media 使用 S/A/B/C/Skip：S 为强视觉、强冲突、明确结果和强追更价值；A 值得制作；B 保留并与其他 Day 合并；C 主要作为博客、Portfolio 或 Developer Experience；Skip 表示不建议公开发布。B/C/Skip 必须说明“今天不建议单独发布”及素材未来去向。

Personal Blog 独立判断，不与 Social Media 绑定。即使社交媒体是 C/Skip，Calibration 排错、安装失败或 DX 记录仍可能值得写 Personal Build Log。

## Publishing Pack

S/A 社交内容包包括 Best Story Angle、3 秒 Hook、至少 5 个不同类型标题（好奇、冲突、结果、生活化、科技感）、3–5 个 6–12 字封面文案、30–90 秒脚本和 Shot List。脚本按 0–3s、3–10s、10–30s、30–50s、50s–结尾组织，并逐段写画面、口播、字幕和是否保留现场原声。根据真实已有素材区分“已有”和“缺失”，说明可安全补拍内容。

Personal Blog 包括 3–5 个标题、2–4 句 Summary、第一人称完整文章、真实素材插入点，以及 Verified、Observation、Hypothesis、Unverified 小节。文章结构覆盖 Today I Wanted To、Why、Setup、What I Did、What Happened、Success、Failure、Errors、Troubleshooting、Result、What I Learned、Developer Experience、What This Means for My Desktop AI Assistant 和 Next。

## 平台与项目记录

只为适合的平台提供适配建议，不要求全平台发布：抖音快速进入结果，小红书强调真实体验/价格/桌面生活，Bilibili 保留过程和技术解释，YouTube/X/知乎按题材决定。无论是否发布，都必须更新 Daily Log、Experiment Result、Developer Experience、Progress、Assets 和 Portfolio Evidence。

每篇 Personal Build Log 记录 Day、Date、Project Stage、Robot、Hardware、Software、Experiment、Result、Status、Main Failure 和 Main Success，逐渐形成可浏览的项目 Timeline；不要求每天都写博客。

## 两个独立网站

Personal Build Log 属于当前桌面 AI 助手项目，服务于 Build in Public、时间线、Portfolio、求职证据、技术实践和 DX 记录，不以 SEO 流量为目标。

Embodied AI SEO Website 属于另一个项目，负责 SEO、Keyword Research、Topic Cluster、Search Console、GEO、Internal Linking、Backlinks、Programmatic SEO 和 Organic Growth。本项目只在有足够真实证据时标记 SEO Website Content Opportunity，并记录主题、转化价值、证据是否足够和还需验证什么；不执行 SEO Strategy。

## Portfolio Evidence

Day N 完成后标记可进入 Case Study 01–05 的证据，例如 First Motion、Deployment、Hardware Decision、Environment Setup、Developer Journey、Documentation Pain Point、Experiment Design、Failure Analysis、Tutorial、AI Assistant Interaction、Video Content 和 Human-Robot Interaction。

## 触发格式

### 开始 Day N

依次输出：Today's Goal、今日核心 Tasks、Robot / AI Assistant Practice、Knowledge、Today's Capture List、Must Capture、Nice to Have、Technical Evidence、Human / Story Moments、当天 Content Idea 预案、Safety Reminder 和 Definition of Done。不提前写死最终发布脚本。

### Day N 完成，结果如下……

依次输出：Reality Check、Project Record 更新、Personal Blog Decision、Social Media Decision、缺失素材、Portfolio Evidence、SEO Website Content Opportunity 和基于真实结果的 Next-Step Insight。除非用户明确要求，不自动生成 Day N+1 的完整计划。
