---
title: "Peter Studio #00：第一位成员正在路上"
series: "Peter Studio Build Log"
status: draft
date: 2026-09-04
site: peterstudio.online
authors:
  - name: Peter Zhang
    role: Builder / Writer

# writing-tech-post contract
archetype:
  primary: migration
  absorbed: research-translation
  hybrid-note: "这是一个个人项目里程碑：记录我如何从多个开源六足路线迁移到第一台已购买的实体机器人，研究型比较只服务于真实部署决定。"
audience:
  rung-target: engineer-adopter
depth-tuple:
  opening-rung: R1
  body-residency: "R1 → R2 → R3 with R1 anchors"
  closing-rung: R1
  traversal: spiral
voice:
  publisher: other
  register: team-narrative
length-band:
  estimated-words: 1700
  archetype-band: "Personal Build Log / Project Milestone"
evidence-forms:
  - table
  - screenshot
  - structured-output-schema
disclosure:
  blameless-register: not-applicable
  coordinated-disclosure: not-applicable
  paper-link-first: not-applicable
  what-wed-do-differently: not-applicable
  vendor-naming-discipline: audit-required
closer:
  shape: shipping-status-roadmap
status: drafting
meta:
  description: "我原本在给机器人设计大脑，后来发现自己连一个可以在桌上失败的身体都没有。于是我比较三条路线，买下了 NodeHexa V1。"
  tags:
    - Peter Studio
    - Build Log
    - NodeHexa
    - Hexapod
    - Embodied AI
    - Open Source Robot
---

# Peter Studio #00：第一位成员正在路上

我原本想先给机器人装上大脑。

Camera、语音、LLM、VLM、VLA，还有一套听起来很像未来的能力路线。我甚至已经开始讨论它以后能不能成为桌面 AI 助手。

然后我发现：我的工作台上连一只真正的机器人都没有。

没有舵机在转，没有电池在放电，也没有一条腿会在我写错代码之后突然抬起来吓我一跳。只有电脑里的仓库、浏览器里的商品页，以及一份越来越长的“等实物到手再验证”清单。

所以我做了一个看起来不太像 AI 项目的决定：

我先买了一只六足机器人。

## 这 60 天，先让一个机器人进入现实

这次项目的目标已经重新收敛：

> 在 60 天内真正做出并运行开源具身机器人，通过六足机器人和机械臂的实际实验，探索它们能做什么，并把过程沉淀为原创内容和作品集。

这里的关键词是“做出并运行”。

不是读完多少篇论文，不是把多少模型名写进 Roadmap，也不是提前宣布机器人最终要负责整理桌面、递东西，还是变成一个会说话的机械臂。那些都可以是后续方向，但现在还没有资格成为结论。

我现在需要的是一个真实的身体：可以拆、可以装、可以接线、可以失败，最好还能在某一天真的走起来。

## 我把三个项目摆上桌面，结果问题变复杂了

我一开始以为，选六足机器人就是比较价格。后来才发现，真正要比较的是“哪条路线最可能在个人条件下产生第一段真实证据”。

我的约束很具体：预算上限 1500 元，希望一周左右看到第一次行走，没有 3D 打印机，接受找打印服务，也愿意先使用 Arduino 或 ESP32 这类入门控制方案。最重要的是，我不想买完零件之后才发现它们根本不是同一台机器人需要的零件。

第一条路线是 **hexapod-ium**。

它的优势很直接：12 个舵机，控制结构比较轻量，Arduino / ESP32 加 PCA9685 的入门路径也比较清楚。对于“先让一个东西动起来”这个目标，它很有吸引力。少一些关节，意味着少一些舵机、接线和校准工作，也意味着预算比较容易控制。

但它的问题也很直接：我还没有拿到足够确定的结构、扩展和长期维护证据。它适合做快速验证，却还不足以让我确信，后面几十天的实验和内容都会围绕它展开。

第二条路线是 **[rookidroid/hexapod](https://github.com/rookidroid/hexapod)**。

它更像一台“有角色潜力的机器人”：18 自由度、ESP32 / Pico、Wi‑Fi 和网页标定，后续接入 Camera、语音或其他交互时，想象空间很大。它也更接近我最初想做的那种会观察环境、和人互动的机器人。

问题是，18 个自由度很快把“机器人”翻译成一串具体账单：更多舵机、更高的供电压力、更复杂的校准，还有机械接口是否真的匹配。前面做执行器分析时，我甚至一度走到了 30–40 kgf·cm 级高扭矩舵机的工程路线，结果价格先把我从浪漫的机器人想象里拽回了现实。

这条路线并不是不值得做，而是它把首版目标变成了一个更大的工程项目。对于“我能不能先拥有一台会动的实体机器人”，它需要我先解决太多尚未锁定的机械问题。

第三条路线是 **[ggldnl/Hexapod](https://github.com/ggldnl/Hexapod)**。

它的魅力在软件侧：Raspberry Pi、Servo2040、Python / ROS2 和仿真链路，适合继续研究更完整的机器人系统。如果我的第一目标是搭建软件架构、理解仿真到真实机器人的迁移，它会很有价值。

但它不太适合我当前的一周目标。它更像一条值得认真研究的中长期路线，而不是一个可以让我尽快面对真实舵机、真实电池和真实装配错误的入口。

这三条路线没有绝对的冠军。它们只是把风险放在了不同的位置：

| 路线 | 主要风险 |
|---|---|
| hexapod-ium | 后续结构和扩展证据不足 |
| rookidroid/hexapod | 执行器、机械接口、校准和预算压力较大 |
| ggldnl/Hexapod | 软件与部署路径较长，首周实体闭环风险较高 |

比较到这里，我得到的不是一个答案，而是一个新问题：

有没有一套资料、结构和套件，能让我先把第一台实体机器人跑通，再决定它以后往哪里长？

## NodeHexa 把问题从“研究”推到了“等待快递”

后来我找到了 [ViolinLee/NodeHexa](https://github.com/ViolinLee/NodeHexa)。

它没有承诺直接给我一个会说话的 AI 助手，也没有替我完成具身智能最难的部分。它提供的是更基础、也更适合当前阶段的东西：公开项目、器材准备说明、控制板、舵机驱动板、结构件和基础运动路径。

这正是我当时缺的。

我的下一条闭环不需要先长这样：

**语言 → 推理 → 规划 → 动作**

它需要先长这样：

**打印件 → 舵机 → 控制板 → 电池 → 基础控制 → 第一次运动**

如果第二条链路还没有跑通，第一条链路就很容易变成 PPT。PPT 当然也可以很有未来感，只是它不会在桌上走。

NodeHexa 也不是“买了就赢”。它的真实质量、舵机一致性、供电安全、装配难度、控制链和运动稳定性，都要等到货后验证。官方资料说明的是项目路径，不是我手上这一套零件已经通过验收。

但至少从这一天开始，我终于有了一个具体的问题可以解决，而不是继续给抽象的机器人增加新名词。

## 这次我到底买了什么

我购买的是 NodeHexa V1 基础套件：

| 项目 | 选择 |
|---|---|
| 套餐 | B：全套散件、无机盖、部分组装 |
| 电池 | 2000mAh 2S |
| 充电器 | 包含 |
| 组装状态 | M1.2 螺丝相关的部分打印件已组装 |
| 当前阶段 | 已购买，等待到货 |
| 价格 | 六百元级，精确成交价以订单为准 |

部分组装不是“卖家帮我把机器人做好了”。它主要替我完成了一部分 M1.2 螺丝相关的打印件装配，剩下的主体结构、舵机、M2 螺丝、接线、供电检查、控制和首次运动，仍然会回到我的桌面上。

我愿意用大约 50 元的差价，换掉一部分最容易卡住的细小装配工作，同时保留理解这台机器人结构的机会。这个取舍比“全部组装好”更适合现在的 Peter Studio：我需要降低无谓的装配门槛，但不能把工程过程也一起外包出去。

电池选择了 2000mAh，而不是 850mAh。

它大约重 96g，850mAh 版本大约 45g。2000mAh 会增加整机负担，所以它不是单纯的“更大就更好”。我选择它，是希望后续测试和拍摄时少受续航限制，也为少量扩展留下余量。至于它是否真的更适合这台机器人，要等到货后测续航、运动状态和电流，不能靠容量数字提前宣布答案。

## 订单完成，但机器人还没有完成

这是这篇日志里最容易被写错的一句话：

我买到了 NodeHexa，不等于我已经拥有一台会运行的 NodeHexa。

当前状态只有：

**Hardware Ordered**

还没有：

- 开箱清点；
- 打印件和紧固件核对；
- 电池和接口检查；
- 结构装配；
- 上电；
- 基础控制；
- 第一次运动。

小小的进度标签，可能是目前最重要的工程证据。它提醒我不要把商品详情图当成实物，把“官方项目可以运行”当成“我的这台已经运行”，也不要为了让文章结尾更漂亮，偷偷把时间线往前挪。

## 这次购买给三条内容线留下了什么

对 PeterStudio 来说，这不只是一笔硬件支出。

**Personal Build Log** 得到了一位真正会抵达工作台的“第一位成员”。后面可以记录开箱、装配、第一次上电、失败和第一次行走。

**Developer Experience** 得到了一条真实的新手路径：从开源项目发现、配置比较、工具准备，到安装、控制和第一次成功。每一个卡点都可能是下一个开发者会遇到的卡点。

**Social Media / Portfolio** 得到了一条可以连续拍摄的故事线：零件平铺、打印件装配、18 个舵机如何进入身体、第一次站立，以及它不听话时我如何排查。它还没有成果，但已经有了明确的冲突和后续章节。

机械臂也没有被取消。它会继续作为并行路线，研究操作、感知、人机协作和 AI 接入。至于哪一个任务最值得让机器人学习，仍然要等早期实验，而不是今天凭想象写死。

## 下一页，不由我来编

NodeHexa 到货后，下一阶段会按这个顺序进行：

**到货清点 → 安全检查 → 结构装配 → 接线确认 → 上电 → 基础控制 → 第一次运动**

我希望下一条日志可以写它第一次站起来的样子。

但如果它没有站起来，我也会写清楚：是装配错了、供电出了问题、控制链没有跑通，还是我把某个看似合理的假设写反了。

现在，Peter Studio 还没有第一台会走的机器人。

但第一位成员已经在路上。项目也终于从“我想研究具身智能”，变成了一个更具体、更麻烦、也更值得记录的问题：

**我能不能把这套东西，真的装起来并让它动起来？**

---

**参考与证据**

- [NodeHexa 官方 GitHub 仓库](https://github.com/ViolinLee/NodeHexa)
- [NodeHexa 官方器材准备说明](https://mp.weixin.qq.com/s/QebT1wd3da98jmFbrUHNdA)
- [rookidroid/hexapod](https://github.com/rookidroid/hexapod)
- [ggldnl/Hexapod](https://github.com/ggldnl/Hexapod)
- [Embodied AI FieldLab Day 2 记录](../../daily/day-02.md)

Tags：Peter Studio · Build Log · NodeHexa · Hexapod · Embodied AI · Open Source Robot
