# V2 One-Leg Servo Prototype Selection

> 状态：研究与选型，不是采购授权。本文将原版 v2 复现执行器与未来 Engineering V2 执行器分开；本阶段最多建议 3 只舵机用于一条腿原型，不购买 18 只。

## 结论先行

```text
READY_FOR_REPLICA_SERVO_SEARCH = true
READY_FOR_FINAL_ENGINEERING_SERVO_SEARCH = false
V2_HIGH_TORQUE_SERVO_DROP_IN = UNVERIFIED
READY_FOR_18_SERVO_PURCHASE = false
```

```text
PRIMARY_ONE_LEG_TEST_SERVO = SPT17HV
BACKUP_ONE_LEG_TEST_SERVO = DS-S007M（条件备选，需先找到可验证淘宝 SKU/价格）
```

当前最合理的动作是：只为 `ONE_LEG_PROTOTYPE` 研究/准备 3 只约 21g class PWM 舵机。SPT17HV 是本轮实际淘宝链路中数据最完整、目标 SKU 和页面价格已验证的候选；DS-S007M 与上游 README 的事实基准更接近，但本轮没有找到可验证的淘宝目标 SKU 和最终价格，因此不能直接作为已通过采购候选。

## 1. 原版实机经验基准

首版基准是 `rookidroid/hexapod` 的 `v2`，仓库为 `rookidroid/hexapod`，当前审计 commit 为 `afebcb6f9ab694504131cc8d34188cc550aa5536`。v2 README 明确写的是 DS Power 或 Miuzei 21G servo，并非 MG92B；MG92B 记录属于 mochi 分支/另一条路线。参考：[v2 README](https://github.com/rookidroid/hexapod/tree/v2)、[v2 commit](https://github.com/rookidroid/hexapod/commit/afebcb6f9ab694504131cc8d34188cc550aa5536)。

作者的演化记录表明：v2 使用更强的 21g 舵机，架构能够把机器人自身撑起来并实现运动；质量较差的 21g 舵机会产生明显 jitter。这是“已演示的最低类别”证据，不是所有 21g 舵机都可靠，也不能推出“30 kgf·cm stall 是 v2 行走最低要求”。

因此本报告采用：

```text
EMPIRICAL_REFERENCE = v2 + 21g-class servo
                       = demonstrated self-support / locomotion-capable architecture
```

## 2. Replica 与 Engineering 扭矩需求

### REPLICA_SERVO_REQUIREMENT

目标是尽量复现作者的 v2 运动能力，而不是提前把未来的 Camera、电池、计算设备和外壳负载加入原版复现。

| 指标 | 原型目标 | 可信度/说明 |
|---|---|---|
| 重量 | 约 20–25 g，21g class | 【推导】来自 v2 README 与作者实机经验；具体型号仍需实测 |
| 控制 | PWM RC servo | 【项目已确认】原版控制链路按 PWM 舵机设计 |
| 电压 | 约 6.0–7.4 V 优先 | 【推导】与候选高压微型舵机和项目电源架构匹配；实际范围须看厂家资料 |
| 堵转扭矩 | 优先 ≥ 6 kgf·cm | 【推导】本轮作为候选筛选门槛，不等同于 v2 的已证明最低值 |
| 角度 | 180° 优先 | 【项目/候选接口】与腿部位置控制和测试计划相容 |
| 尺寸 | 21g 微型舵机级，必须落入 STL 安装 envelope | 【必须实测】当前 cavity/安装孔距尚未完全确认 |
| 齿轮/输出轴 | 金属齿优先；25T 优先 | 【推导/待确认】必须与实际舵盘和 STL 接口复核 |
| 实际价格 | 目标 SKU 页面价格可读 | 【强制】不能使用“￥xx 起” |

### ENGINEERING_SERVO_REQUIREMENT

目标是未来承载 Camera、传感器、电池、屏幕/音箱和计算设备后仍有可靠余量。这里继续使用已建立的 Jacobian + dynamic load + stall derating 模型；保守的 Femur 约 30 kgf·cm stall class 是 Engineering 需求，不是原版 v2 的最低行走要求。

工程需求必须区分：

```text
requiredStaticTorque
requiredDynamicTorque
recommendedOperatingTorque
servoStallTorque
```

厂家未提供 continuous torque 时，不能把 stall torque 当作额定连续工作扭矩；只采用保守降额，并把该参数标为【厂家未提供连续扭矩】。

## 3. 本轮淘宝候选

本轮遵循：`taobao-keyword-search → taobao-product-detail → taobao-sku-detail → taobao-product-engineering-detail → hexapod-procurement`。未加购、未下单、未付款。

### 候选 A：SPT17HV（条件主选）

- 淘宝链接：[SPT17HV 商品页](https://item.taobao.com/item.htm?id=691878395047)
- 商品标题：`SPT17HV 6kg 7.4v高压速金属钢齿17g数码转向舵机换挡差速固定翼`
- 型号/品牌：`SPT17HV` / `SPT`，【淘宝 DOM/详情图已确认】
- 目标 SKU：`180度/500-2500us 6-8.4v 0.09s`，【SKU 已点击并确认 selected/active】
- 页面价格：`¥73.71`；页面同时显示原/折前金额约 `¥80.51`，【目标 SKU 选择后重新读取】
- 默认价与目标 SKU 价：均为 `¥73.71`，`priceChanged=false`；这表示本次变体同价，不是使用默认价冒充目标价。
- 可售性：页面显示“有货”；公开库存数量未提供，`stock=null`。

| 参数 | 值 | 状态 |
|---|---|---|
| 重量 | 17g（详情图） | 【已确认】 |
| 工作电压 | 7.4V 详情文字；SKU 显示 6–8.4V | 【已确认】但需厂家资料复核 |
| 堵转扭矩 | 0.6 N·m，约 6.12 kgf·cm | 【已确认】详情图/页面；连续扭矩未提供 |
| 空载速度 | 0.09 s/60°（目标 SKU 文本） | 【已确认】 |
| 角度 | 180°，500–2500 μs | 【已确认】 |
| 输出轴 | 5.94 mm、25T | 【已确认】详情文字/图；舵盘具体兼容仍需试装 |
| 齿轮 | 不锈钢/金属齿 | 【已确认】 |
| 防护 | IP65 | 【已确认】页面文字；桌面实验不等于完整防水验证 |
| 外形 | 详情尺寸图含 40.20 mm 安装相关长度、13.00 mm 宽度、28.00 mm 机身长度、Ø4.30 孔标注；部分箭头映射仍不完整 | 【部分已确认】 |
| 堵转/峰值电流 | 未找到 | 【待确认】 |
| 安装孔中心距 | 未找到清晰独立标注 | 【待确认】 |
| 厂家连续扭矩 | 未提供 | 【厂家未提供连续扭矩】 |

**评分与状态：** 条件候选/中等可信，不是高可信候选。原因是目标 SKU、价格、重量、扭矩、电压、速度、角度和 25T 已有证据，但强制工程字段中的电流、完整安装孔距和完整尺寸映射仍缺失。若按严格自动门槛，缺少堵转/峰值电流应保留 `REJECTED_PARAMETER_MISSING` 风险，不能直接扩展为 18 只。

### 候选 B：DSPOWER DS-S007M（事实基准/条件备选）

- 厂家页面：[DSPOWER DS-S007M](https://www.dspowerservo.com/ds-s007m-21g-metal-gear-micro-servo-product/)
- 型号：`DS-S007M`，重量 `21±1g`，尺寸 `29.6×13.2×34.3 mm`，PWM，【厂家已确认】。
- 电压：`4.8–7.4V`；堵转扭矩 `≥6 kgf·cm`；堵转电流 `≤2.7A`；空载电流 `≤200mA @4.8V`、`≤210mA @6.0V`；空载速度 `≤0.22s/60°`；脉宽 `500–2500μs`；工作角度 `180±10°`（1000–2000μs）；这些优先采用厂家资料。
- 金属齿、25T/输出轴信息在厂家页面可见，但页面存在不同产品页表述，需以实际销售 SKU 和实物舵盘再确认。
- 本轮淘宝精确搜索 `DS-S007M`、`DSpower 21g 25T 7.4V 6kg` 未获得可验证的目标商品 SKU 和最终页面价格，因此不能把它写成已通过价格核验的淘宝候选。

**状态：** 条件备选；`REJECTED_PRICE`（本轮作为采购候选的价格字段缺失），不是产品本身淘汰。若后续找到淘宝目标 SKU 并验证页面价格，它是最值得优先复核的备选，因为它同时最接近上游 README 的 DS Power 事实基准。

### 候选 C：EMAX ES3054 HV（淘汰）

- 淘宝链接：[EMAX ES3054 HV 商品页](https://item.taobao.com/item.htm?id=1077436413264)
- 目标 SKU：`ES3054 HV高压版 + EMAX银燕舵机`，实际页面价格 `¥175.42`，有货；SKU 选择已确认。
- 详情图确认：20.5±0.5g、6.0/8.4V、空载速度 0.13/0.09 s/60°、堵转扭矩 3.4/4.7 kg·cm、堵转最大电流 1.0/1.3A、PWM、500–2500μs、180°±10°、23T、2BB、金属齿。
- 官方参考：[EMAX ES3054HV](https://emaxmodel.com/products/es3054hv-all-purpose-high-voltage-metal-gear-digital-servo)

**状态：** `REJECTED_TORQUE`。重量、控制和数据完整度不错，但 8.4V 堵转扭矩约 4.7 kg·cm，低于本轮 Replica 候选优先门槛约 6 kgf·cm；不适合作为这条 v2 腿的首选受力舵机。

### 候选 D：MJ-65MG（淘汰为当前采购候选）

- 淘宝链接：[MJ-65MG 商品页](https://item.taobao.com/item.htm?id=919696907510)
- 页面识别到 7.4V、黑/红色 SKU，页面显示“45 起”，点击颜色后仍未获得明确的目标 SKU 实际价格。
- 关键尺寸、电流、明确扭矩定义、输出轴齿数和角度也未完整确认。

**状态：** `REJECTED_PRICE` + `REJECTED_PARAMETER_MISSING`。不是说产品一定不能用，而是不能进入本轮可验证采购候选。

### Miuzei 搜索结果

本轮 `Miuzei 21g 舵机` 搜索未获得可核验的相关舵机商品，结果主要是无关的齿轮/电池类商品。因此不编造 Miuzei 具体 SKU，也不把无关结果列入候选。

## 4. 推荐 3 只原型舵机

```text
建议数量：3 只
用途：Coxa / Femur / Tibia 各 1，先打印并装配一条 v2 腿
建议型号：SPT17HV × 3（当前只形成建议，不执行采购）
```

选择理由：SPT17HV 是本轮唯一同时满足“目标 SKU 已实际点击、页面价格已重新读取、约 21g 微型尺寸级、180°、6 kgf·cm 级、7.4V 高压、25T”和淘宝详情图片有工程参数的实际候选。它仍不是最终高可信结论，购买前必须补齐/实测电流、安装孔距、完整 cavity fit 和舵盘间隙。

备选优先级：先找 DS-S007M 的可验证淘宝 SKU；若找不到，再把 MJ-65MG 作为线索重新搜索，但不能使用其“45 起”作为 BOM 单价。

## 5. 单腿测试计划

### 测试顺序

1. 单舵机 PWM 90° 定位；先限速、低占空/低风险供电。
2. 单舵机完整 180° 运动范围；确认端点、方向和软件限位，禁止撞机械止挡。
3. Coxa/Femur/Tibia 三舵机装配一条 v2 腿；先悬空，不装足端负载。
4. 悬空步态；验证动作序列、抖动、反向和舵机同步。
5. 逐渐施加载荷；从极小载荷开始，每级记录动作和温度。
6. 记录工作电流；至少记录单舵机和三舵机同时动作。
7. 记录峰值电流；必须使用合适的电流测量设备，不用软件估算替代实测。
8. 连续运行 10 分钟并记录温升；出现异常声、抖动、过热或掉位立即停止。
9. 检查齿轮间隙与 jitter；比较冷机/热机和不同姿态。
10. 检查打印件、舵盘、输出轴和孔距；拍摄装配证据并记录干涉点。

### 通过标准

- 三个目标 SKU 与实际舵机标签/包装一致；
- 90° 与 180° 指令可重复到位，无明显撞限位；
- 一条腿可完成悬空动作，Coxa/Femur/Tibia 方向正确；
- 无持续明显 jitter、齿轮跳齿、输出轴打滑或打印件开裂；
- 10 分钟测试后无异常过热、位置漂移或电源掉压；
- 工作/峰值电流已记录，并能据此修正电池、BEC、保险丝、线径和连接器；
- 机械接口尺寸、舵盘齿数和 horn clearance 已由实物或明确测量证据确认。

只有全部核心标准通过，才可将：

```text
READY_FOR_18_SERVO_PURCHASE = true
```

否则保持 `false`。

## 6. 当前无法确认的问题

- v2 STL 的 servo cavity、安装耳间隙、螺钉中心距、输出轴到安装面的距离和 horn 旋转间隙仍未完成可靠的结构级测量；
- SPT17HV 的堵转/峰值电流、完整机身高度和安装孔中心距未在当前淘宝详情中确认；
- DS-S007M 的淘宝实际 SKU、最终价格和与 v2 STL 的实物适配尚未确认；
- 21g 舵机的实际持续扭矩、热性能和低质量批次 jitter 风险必须通过实机测试；
- 当前项目尚无实测整机质量，因此 Engineering V2 的 Jacobian 结果仍是低置信度质量预算下的保守模型；
- 本轮未找到可用的 Miuzei 商品页面；
- 价格可能随活动、地区和登录状态变化，最终应以再次选择目标 SKU 后的页面显示为准。

## 7. 决策

本轮采用“两阶段执行器验证策略”：

1. 先验证原版 v2 的 21g-class Replica 路线，最多 3 只，目标是一条能运动的腿；
2. 单腿证据通过后，再决定是否采购 18 只同型号，或修改结构进入 Engineering V2；
3. 在机械接口和负载模型没有进一步证据前，不启动 30–40 kgf·cm 级最终工程舵机采购；
4. `READY_FOR_FINAL_ENGINEERING_SERVO_SEARCH = false` 保持不变。

**本报告结论：** `SPT17HV` 可作为当前单腿原型的条件主选，`DS-S007M` 是更贴近上游事实基准的条件备选；当前不能批准 18 只采购。
