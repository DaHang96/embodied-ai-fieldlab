# NodeHexa V1 Hardware Expansion Audit

审计类型：NodeHexa Hardware Expansion / Pin Interface Audit  
审计日期：2026-09-01  
采购状态：本轮不采购、不加购、不下单、不付款  
官方 PCB / 官方固件：未修改

## 0. 结论摘要

本报告锁定的硬件基线是 NodeHexa 上游仓库 `ViolinLee/NodeHexa` 的 `master` 分支，审计 commit 为 [`80532566a18766e8163f4f506b7f17dd4f7b0c7c`](https://github.com/ViolinLee/NodeHexa/tree/80532566a18766e8163f4f506b7f17dd4f7b0c7c)。该版本是 ESP32 + 两块 PCA9685 舵机扩展板 + MG90S 类 18 路 PWM 舵机架构，并预留了 I2C、UART2 和一组 NodeMCU GPIO 引脚。

当前最适合的扩展路线是：

`NodeHexa ESP32 保持实时运动控制` + `外部 Raspberry Pi / PC 负责 Camera、Mic、Speaker、Screen、VLM/Agent` + `Wi-Fi/WebSocket 作为主链路`。

结论不是“所有接口都可以直接接”。主要边界如下：

- I2C：有专用 4P 接口，原则上支持传感器扩展，但接口标有 `+5V`，逻辑电平和上拉必须先实测。
- UART2：GPIO16/17 已由固件使用，并且被 Xiaozhi 扩展板占用/声明为主机链路；不能再把两个设备并联到同一 UART。
- 5V：主板和扩展口可见；最大可用电流没有被当前资料证明，不能据此承诺可直接带动树莓派、Jetson 或大功放。
- 3.3V：主板用户侧 17P/19P/4P 扩展口没有明确的一般 3.3V 供电针脚。
- 摄像头、麦克风、扬声器、屏幕和 VLM/VLA：建议由外部 AI 计算板承载，不应强行塞入主控 ESP32。
- 高扭矩 PWM 舵机：不仅是换舵机，还涉及机械安装、供电、线束、热和 PCB 负载验证。
- 总线舵机：需要新的总线收发器、协议、供电和机械接口，属于重大改造。

因此当前状态为：

```text
NODEHEXA_AI_EXPANSION_SUITABILITY      = SUPPORTED_WITH_EXTERNAL_COMPUTE
NODEHEXA_SENSOR_EXPANSION_SUITABILITY  = EASY_EXTENSION_WITH_ELECTRICAL_CHECKS
NODEHEXA_ACTUATOR_UPGRADE_SUITABILITY  = REQUIRES_POWER_AND_MECHANICAL_REDESIGN
READY_FOR_PURCHASE                     = false
```

## 1. 审计范围与证据等级

直接审计了以下上游文件：

- `README.md`
- `hardware/README.md`
- `hardware/PiHexa-V4.zip`
- `hardware/PiHexaSub-V3.zip`
- `hardware/PiHexaHatXiaozhi.zip`
- `firmware/src/main.cpp`
- `firmware/src/servo.cpp`
- `firmware/include/PinDefines.h`
- `firmware/include/config.h`
- `firmware/platformio.ini`
- 相关 `movement`、`leg`、`hexapod`、`motion_controller` 和 `hal/pwm` 文件

三个 ZIP 已解压并读取 EasyEDA Standard JSON 的 schematic / PCB 数据。报告中的证据等级：

- **已确认**：固件常量、原理图网络名、PCB 焊盘网络名或上游明确文字直接支持。
- **推导**：由引脚映射、器件引脚定义或多个文件相互印证得出。
- **待确认**：仅凭当前 JSON、网络命名或未做实物/EDA 连通性检查，无法安全确认。

## 2. 上游硬件基线

### 2.1 主控与板卡

| 模块 | 当前基线 | 证据 |
|---|---|---|
| 主控 | NodeMCU-32S / ESP32 classic | `platformio.ini`、PiHexa-V4 schematic |
| 主舵机板 | PiHexa-V4 | 上游 `hardware/README.md` |
| 舵机扩展 | 两块 PiHexaSub-V3，每块 9 路 | schematic/PCB；PCA9685 地址 `0x40` 与 `0x41` |
| 执行器 | 6 腿 × 3 关节 = 18 路 PWM | `servo.cpp` |
| 舵机协议 | PCA9685 产生 50 Hz PWM，脉宽约 500–2500 us | `servo.cpp` |
| 机械参考 | README 推荐/测试 MG90S 类舵机；README 另称 DS Power 或 Miuzei 21G servo | 上游 README |
| AI 扩展 | PiHexaHatXiaozhi，ESP32-S3 + I2S 麦克风/功放 | Xiaozhi schematic/PCB |

README 对 MG90S 版本差异有明确提醒；这说明“MG90S”不能被当作足够精确的工程型号，必须核对实际尺寸、电压、扭矩和质量。

### 2.2 固件已使用资源

| GPIO | 固件/板上用途 | 方向/协议 | 当前状态 |
|---|---|---|---|
| GPIO16 | `Serial2` RX | UART2，115200 | 已占用；可作为 AI 备用链路，但不能并联第二个设备 |
| GPIO17 | `Serial2` TX | UART2，115200 | 已占用；同上 |
| GPIO21 | `Wire` SDA | I2C | 已占用；可共享但必须做地址、电平和总线电容检查 |
| GPIO22 | `Wire` SCL | I2C | 已占用；同上 |
| GPIO25 | `BAT_LED` | 数字输出 | 已占用 LED |
| GPIO34 | `BAT_ADC` | ADC 输入 | 已占用电池分压采样，且 GPIO34 为输入专用 |
| GPIO6–11 | ESP32 SPI flash 相关 | 模块内部 | 禁止作为外部扩展 |

固件还使用 Wi-Fi/WebSocket 和文件系统。代码中出现的 `SPIFFS` 是片上 flash 文件系统，不等于已为用户外设分配了可用 SPI 总线。

### 2.3 当前已知的电池监测

固件使用 GPIO34 读取 100 kΩ / 47 kΩ 分压，10 次平均，并乘以 `BATTERY_VOLTAGE_GAIN = 1.0122`。低压阈值为约 7.2 V 警告/待机锁存和约 7.0 V 运动锁存。

这只能证明有电池电压监测；没有电流传感器，也没有从当前资料得到主板、VCC 或舵机电源的最大持续/峰值电流。

## 3. ESP32 完整扩展引脚地图

下表中的“可复用”指可以在设计中考虑，并不表示无需改固件即可使用。

| GPIO | 当前用途/板级去向 | 特殊风险 | 分类 |
|---:|---|---|---|
| 0 | NodeMCU 引出，当前未见固件外设 | 启动 strap | 条件可用 |
| 1 | NodeMCU 引出 | UART0 TX / 下载日志 | 条件可用 |
| 2 | NodeMCU 引出 | 启动 strap | 条件可用 |
| 3 | NodeMCU 引出 | UART0 RX / 下载日志 | 条件可用 |
| 4 | 侧边 header 引出，未见主板外设 | 一般无当前占用 | 安全空闲候选 |
| 5 | 侧边 header 引出 | 启动 strap | 条件可用 |
| 6–11 | ESP32 flash 内部 | flash 保留 | 禁止使用 |
| 12 | header 引出 | 启动/flash 电压 strap | 条件可用 |
| 13 | header 引出，未见主板外设 | 一般无当前占用 | 安全空闲候选 |
| 14 | header 引出，未见主板外设 | 一般无当前占用 | 安全空闲候选 |
| 15 | header 引出 | 启动 strap | 条件可用 |
| 16 | 19P 侧边 header；UART2 RX | Xiaozhi/主机串口链路 | 已占用 |
| 17 | 19P 侧边 header；UART2 TX | Xiaozhi/主机串口链路 | 已占用 |
| 18 | header 引出，未见主板外设 | 一般无当前占用 | 安全空闲候选 |
| 19 | header 引出，未见主板外设 | 一般无当前占用 | 安全空闲候选 |
| 21 | I2C SDA、PCA9685、4P I2C header | 总线共享、上拉/电平 | 已占用/可共享 |
| 22 | I2C SCL、PCA9685、4P I2C header | 总线共享、上拉/电平 | 已占用/可共享 |
| 23 | header 引出，未见主板外设 | 一般无当前占用 | 安全空闲候选 |
| 25 | 电池 LED | 改用会影响状态指示 | 已占用 |
| 26 | header 引出，未见主板外设 | 一般无当前占用 | 安全空闲候选 |
| 27 | header 引出，未见主板外设 | 一般无当前占用 | 安全空闲候选 |
| 32 | header 引出，未见主板外设 | 一般无当前占用 | 安全空闲候选 |
| 33 | header 引出，未见主板外设 | 一般无当前占用 | 安全空闲候选 |
| 34 | 电池 ADC 分压 | 输入专用，不能输出 | 已占用 |
| 35 | header 引出 | 输入专用 | 条件可用，仅输入 |
| 36 | SVP / header 引出 | 输入专用 | 条件可用，仅输入 |
| 39 | SVN / header 引出 | 输入专用 | 条件可用，仅输入 |

### 3.1 分类汇总

```text
SAFE_FREE_GPIO = GPIO4, 13, 14, 18, 19, 23, 26, 27, 32, 33
CONDITIONALLY_FREE_GPIO = GPIO0, 1, 2, 3, 5, 12, 15, 35, 36, 39
SHAREABLE_OCCUPIED = GPIO21, 22
OCCUPIED = GPIO16, 17, 25, 34
DO_NOT_USE_GPIO = GPIO6, 7, 8, 9, 10, 11
```

在真正接线前仍需用万用表确认：header 的针脚方向、是否有板上上拉/下拉、空闲电平和外接模块不会改变 ESP32 启动电平。

## 4. PiHexa-V4 连接器与扩展接口

### 4.1 4P I2C 接口

两个 4P 接口是直接的 I2C / 电源扩展：

| 逻辑针脚 | 接口 A | 接口 B |
|---:|---|---|
| 1 | SCL | GND |
| 2 | SDA | +5V |
| 3 | +5V | SDA |
| 4 | GND | SCL |

它们是同一 I2C 总线的不同排布/方向，不是两个独立 I2C 控制器。适合 IMU、ToF 或其他低速 I2C 设备，但当前没有明确的 3.3V 用户供电针脚，也没有找到 I2C 电平转换器的明确证据。对 3.3V 设备必须先确认 SDA/SCL 上拉电压；必要时使用外部 3.3V 供电和双向电平转换器。

### 4.2 两个 6P 舵机板电源接口

两组 6P 主板到 PiHexaSub-V3 的连接器只承担电源：每组由三针 `VCC` 和三针 `GND` 组成。I2C 由 4P 接口独立连接。

`VCC` 被用于舵机/扩展板电源轨的网络名称，但当前资料没有足够证据给出其最大持续电流、峰值电流、允许压降或热裕量。必须保持：

```text
SERVO_RAIL_MAX_CONTINUOUS_CURRENT = UNKNOWN
SERVO_RAIL_MAX_PEAK_CURRENT       = UNKNOWN
```

### 4.3 17P / 19P GPIO 侧边接口

主板两侧各有一组 17P/19P 公母连接器的同源引出，暴露 NodeMCU 大多数 GPIO、GND、SDA、SCL、5V 和 UART2。

右侧 19P 的原理图/PCB 映射为（前几项是 ESP32 模块内部 flash 网络，不是普通 GPIO）：

```text
pin19=CLK, 18=SD0, 17=SD1, 16=GPIO15,
15=GPIO2, 14=GPIO0, 13=GPIO4, 12=GPIO16, 11=GPIO17,
10=GPIO5, 9=GPIO18, 8=GPIO19, 7=GND, 6=SDA,
5=GPIO3/RX0, 4=GPIO1/TX0, 3=SCL, 2=GPIO23, 1=GND
```

这里的 EasyEDA/NodeMCU 物理编号与逻辑 GPIO 名称存在混用，实际接线应以丝印、原理图和万用表为准；上述映射已按 schematic 与 PCB pad net 对齐，但不能把 `SD0–SD3/CMD/CLK` 当作安全 GPIO。

左侧 17P/19P 主要暴露 GPIO34/35/32/33/25/26/27/14/12/13、输入相关引脚、GND 和 +5V；其中 GPIO34 仍是电池 ADC，GPIO25 仍是 LED。

### 4.4 电池输入与原始电压

XT30：PCB pad 1 为 GND，pad 2 标为 `VBAT`。主板 XL1509-5.0E1 的输入网络标为 `VCC`，输出为 `+5V`，并配有二极管、电感和电容。

从电源意图可以确认“电池输入经过降压得到 5V，并向舵机板供电”；但本次对 EasyEDA JSON 进行的是网络/焊盘级解析，没有完成整块 PCB 铜箔连通性追踪，因此：

```text
BATTERY_INPUT = XT30 VBAT/GND        [已确认]
5V_REGULATOR  = XL1509 -> +5V        [已确认]
VBAT_TO_VCC_COPPER_CONTINUITY       [待确认]
RAW_BATTERY_VOLTAGE_AT_SERVO_RAIL   [待确认]
```

接任何传感器、树莓派或舵机前，应实测 XT30、VCC、+5V、GND 对之间的电压，不能仅凭 `VCC` 标签当作安全 5V。

## 5. 电源架构审计

当前可还原的逻辑链路：

```text
电池/XT30
  -> 主板输入网络 VBAT/VCC（铜箔连续性待实测）
  -> XL1509-5.0E1 降压
  -> +5V
      -> NodeMCU-32S 5V 输入
      -> PiHexaSub-V3 逻辑/舵机接口
      -> PiHexaHatXiaozhi MainBoard5V
  -> VCC 原始/舵机电源链路（额定电压和最大电流待确认）
```

Xiaozhi 扩展板上：

- `MainBoard5V` 进入板上电源；
- `ME6211C33M5G-N` 产生本地 3.3V，供 ESP32-S3 和麦克风等逻辑部分；
- NS4168 类 D 功放使用 5V，并通过 2P 接口连接外部扬声器；
- USB-C VBUS 也是板上供电输入路径之一；
- 没有发现显示屏控制器或屏幕连接器。

### 5.1 外设供电判断

| 外设 | 能否直接由 NodeHexa 主板确认供电 | 结论 |
|---|---|---|
| IMU | I2C +5V 接口存在，但 3.3V 逻辑/上拉未确认 | 外部 3.3V/电平转换或实测后接入 |
| ToF | 同上 | 外部供电/电平检查 |
| OLED/LCD | 无专用屏幕接口，I2C 小屏可能共享总线 | 需要确认电压、电流、地址和机械安装 |
| USB/CSI Camera | 无主板接口 | 外部 Raspberry Pi/PC/独立相机板 |
| 麦克风 | Xiaozhi 自带 I2S 麦克风 | 保留 Xiaozhi或由外部 AI 板统一承载 |
| 扬声器 | Xiaozhi 5V 功放和 speaker connector | 可由 Xiaozhi承载，但电源/喇叭规格需实测 |
| Raspberry Pi | 主板 5V 最大电流未知 | 独立稳压/独立电源轨 |
| Jetson | 重量、峰值电流、散热都超出已证实范围 | 独立电源、结构和热设计 |

## 6. Xiaozhi 扩展板资源审计

PiHexaHatXiaozhi 并不是一个“多余的 ESP32 GPIO 扩展板”，而是一个有明确功能占用的音频板：

| 资源 | 用途 |
|---|---|
| ESP32-S3 GPIO / I2S1 | ICS-43434 数字麦克风：WS、SCK、DIN |
| ESP32-S3 GPIO / I2S2 | NS4168 功放：DOUT、BCLK、LRCK |
| ESP32-S3 TXD1/RXD1 | 与主 NodeMCU 之间的串口链路 |
| 5V | 功放和板上电源输入 |
| 3.3V | ME6211 本地 LDO 输出 |
| 2P speaker | 外接扬声器输出 |
| 17P/19P | 主要是主板/NodeMCU 侧的转接/贯通，不是已验证的额外 S3 GPIO 扩展 |

主 NodeMCU 的 GPIO16/17 在固件中就是 UART2，Xiaozhi 原理图又以 TXD1/RXD1 引出该串口链路。因此：

```text
UART2_SINGLE_LINK = Xiaozhi 或另一 AI/上位机设备二选一
UART2_PARALLEL_DEVICES = 禁止直接并联
```

若保留 Xiaozhi 做语音演示，建议树莓派走 Wi-Fi/WebSocket；若未来统一由树莓派负责 Camera/Mic/Speaker/Screen，则可以不装 Xiaozhi，避免串口资源分裂。两种方案都不要求改官方 PCB。

## 7. 计划中的 AI / 具身智能扩展

### 7.1 设备职责建议

```text
NodeHexa ESP32
  - IK / 腿部运动学
  - gait / motion
  - PCA9685 / 18 路舵机
  - 校准、低压保护、急停/停止
  - 电池电压监测

外部 AI 计算板（首选 Raspberry Pi 或 PC）
  - Camera
  - Mic / Speaker
  - Screen
  - VLM / LLM / Agent
  - 任务规划、语音理解、视觉目标识别
  - 将高层动作转换成 NodeHexa 已支持的动作命令
```

`VLM/VLA` 不应在 ESP32 classic 上运行。PC + RTX 3060 Laptop 或远程 GPU 可用于推理和训练；机器人端只需通过 Wi-Fi 或串口接收可控的高层动作。

### 7.2 连接架构

推荐的长期结构：

```text
PRIMARY_AI_LINK = Wi-Fi / WebSocket
BACKUP_AI_LINK  = UART2（115200，单设备独占）
```

备选方案：

- **保留 Xiaozhi**：Xiaozhi 通过 UART2，Raspberry Pi 通过 Wi-Fi；适合先做语音/角色 Demo。
- **统一 AI 板**：移除或暂不安装 Xiaozhi，Raspberry Pi 统一处理 Camera、Mic、Speaker、Screen，通过 Wi-Fi 为主、UART2 为备；适合长期研究。
- **增加串口桥接 MCU**：只有当两个物理设备都必须使用 UART2 时采用；会增加复杂度和故障点。

### 7.3 VLA 的动作接口

现有固件的高层动作空间可作为 VLA 第一版输出边界：前进、后退、转向、横移、姿态、单腿动作、距离、角度、动作序列、停止等。初期不建议让 VLA 直接输出 18 个舵机角度；应由 ESP32 保留 IK、限位、速度和安全控制。

### 7.4 IMU 闭环可行性

硬件层面：可从专用 I2C 口扩展 IMU。  
软件层面：当前资料没有现成的 IMU 稳定控制闭环；未来至少需要增加传感器驱动/任务、滤波、姿态估计、roll/pitch 修正、将修正量送入 body pose/IK 的路径，以及异常时的安全回退。

建议闭环：

```text
IMU -> 时间戳/滤波 -> roll/pitch -> body pose correction
    -> IK -> gait / servo command -> 姿态变化
```

本轮未改固件，因此不把“已有 I2C 接口”误写成“已有 IMU 稳定功能”。

## 8. 传感器扩展与执行器扩展分开判断

### 8.1 传感器

IMU、ToF、低速 OLED 属于相对容易的扩展，但仍受 5V 标注、电平、I2C 地址、上拉和供电余量约束。它们通常不需要立即修改主 PCB。

### 8.2 执行器

- **MG90S → 更高扭矩 PWM 舵机**：保留 PCA9685 控制方式的可能性较高，但要重新验证舵机体积、耳位、舵盘、输出轴、腿件强度、电池/BEC、线束和热。
- **PWM → 串行总线舵机**：需要总线收发器、协议驱动、ID/反馈、供电和机械接口改造，不是软件换一个库即可完成。
- **更大电池**：需要同时核对电压、BMS/保护、峰值放电、接头、保险丝、充电器、质量和重心；不能只看容量。

## 9. NODEHEXA_EXPANSION_MATRIX

| 能力/部件 | 状态 | 说明 |
|---|---|---|
| IMU | `EASY_EXTENSION` | I2C 口存在；电平、上拉和软件闭环需验证 |
| ToF | `EASY_EXTENSION` | I2C 口可用；地址、电平、供电需验证 |
| OLED | `EASY_EXTENSION` | 小型 I2C 屏可研究；无专用屏口，需确认电平/电流/安装 |
| LCD | `REQUIRES_EXTERNAL_BOARD` | 无已确认的显示控制接口，建议由 AI 板驱动 |
| Camera | `REQUIRES_EXTERNAL_BOARD` | ESP32-S3 Xiaozhi板没有被确认的相机接口；用 Pi/PC/独立相机板 |
| Mic | `SUPPORTED_NOW` | Xiaozhi 板已集成 I2S 麦克风；统一 AI 方案也可用外部麦克风 |
| Speaker | `SUPPORTED_NOW` | Xiaozhi 板含 NS4168 功放和扬声器接口；功率/喇叭需实测 |
| Screen | `REQUIRES_EXTERNAL_BOARD` | Xiaozhi 无屏幕控制器/连接器证据 |
| XiaoZhi | `SUPPORTED_NOW` | 音频板可用，但占用 UART2 链路 |
| ESP32-S3 CAM | `REQUIRES_EXTERNAL_BOARD` | 需独立供电、视频链路和上位机集成 |
| Raspberry Pi | `REQUIRES_POWER_REDESIGN` | 通信容易，主板 5V 最大电流未知，建议独立稳压/电源 |
| Jetson | `REQUIRES_POWER_REDESIGN` | 另需质量、散热和安装结构设计 |
| External PC | `SUPPORTED_NOW` | Wi-Fi/WebSocket 已有基础；机器人端不用承载大模型 |
| VLM | `REQUIRES_EXTERNAL_BOARD` | 在 PC/Pi/Jetson/远程 GPU 上运行 |
| Agent | `REQUIRES_EXTERNAL_BOARD` | 输出高层动作，不直接越过 ESP32 安全层 |
| VLA | `REQUIRES_EXTERNAL_BOARD` | 初期输出受限高层动作空间 |
| High-torque PWM servo | `REQUIRES_MECHANICAL_REDESIGN` | 机械 envelope、供电、热和结构强度均需重新确认 |
| Bus servo | `MAJOR_REDESIGN` | 总线硬件、协议、供电、反馈和机械接口都变化 |
| Larger battery | `REQUIRES_POWER_REDESIGN` | 电压、BMS、峰值电流、接头、保险和重心需重新设计 |

## 10. NodeHexa V1.5 推荐架构

### 10.1 推荐方案

```text
NodeHexa V1.5
  原 NodeHexa ESP32
    保留 IK、gait、舵机、校准、安全、电池监测

  I2C
    首先接 IMU；之后再评估 ToF/OLED

  Wi-Fi/WebSocket
    连接 Raspberry Pi 或 PC，作为 AI 主链路

  UART2
    作为备用诊断/低层命令链路；同一时间只接一个物理串口伙伴

  AI 侧
    Camera + Mic + Speaker + Screen + VLM/LLM/Agent
```

这是“扩展主板能力”的低风险路线：先验证原版运动，再把 AI 当作上层协作者，而不是让 AI 板直接接管 18 路舵机。

### 10.2 为什么不把所有功能直接接到 NodeHexa

NodeHexa 的 ESP32 和现有 PCB 已经明确承担实时运动、低压保护和两块 PCA9685 的控制。Camera、音频、屏幕和 VLM 对计算、带宽、存储、功耗和软件复杂度的要求不同。职责分层可以保留原有运动安全边界，也可以让 `peterstudio.online` 的机械臂/六足机器人角色体验逐步叠加，而无需先重做底板。

## 11. 当前无法确认的信息

以下内容不能从本次直接读取的固件、schematic、PCB JSON 和 README 安全得出：

1. XT30 的 `VBAT` 到 XL1509 输入 `VCC` 的完整 PCB 铜箔连续性。
2. 舵机 VCC 的实际额定电压、最大连续电流、峰值电流和各连接器允许电流。
3. XL1509 方案在当前 PCB 铜厚、散热和电感条件下的真实热能力。
4. 主板 5V 能否承载某一具体 Raspberry Pi、功放或屏幕型号。
5. 4P I2C 口的实际上拉电压、上拉阻值和总线电容余量。
6. 所有 17P/19P header 的丝印朝向与装配后针脚可接近性。
7. Xiaozhi S3 未引出的 GPIO 是否有可用的板内测试点。
8. NodeHexa 原作者实际使用的某一具体 DS Power/Miuzei 21G 商品型号。
9. 现有固件是否已经在某个未搜索到的分支中实现 IMU 稳定控制。

这些问题需要实物万用表/示波器/热测试、完整 EDA 连通性检查或厂家/作者资料，不能用推测补齐。

## 12. 最终回答

### 1. NodeHexa 是否支持直接接 IMU、ToF、OLED？

支持“通过 I2C 口扩展”的方向；不是无条件即插即用。必须先确认 4P 口的电压、上拉和传感器耐压，必要时使用外部 3.3V 供电与电平转换。

### 2. GPIO16/17 是否被 Xiaozhi 占用？

是。主固件把 GPIO16/17 配成 UART2；Xiaozhi 板也把对应串口作为与主机通信的链路。它们不能被两个设备直接并联。

### 3. 是否存在未使用 GPIO？

有，首选候选为 GPIO4、13、14、18、19、23、26、27、32、33；它们仍需在实际板上确认电平和没有隐藏负载。GPIO0/2/5/12/15 等是条件可用，GPIO6–11 禁用，GPIO34/35/36/39 只能输入。

### 4. 是否有 3.3V / 5V / 电池电压可用？

- 5V：有明确 `+5V` 网络和引出。
- 3.3V：NodeMCU 模块内部有 3.3V，但主板用户扩展 header 没有明确的一般 3.3V 输出。
- 电池输入：XT30 有 `VBAT`；6P 舵机链路有 `VCC/GND`，但需实测其与电池输入的关系及实际电压。

### 5. 是否能直接接 Raspberry Pi？

通信上可以，供电上不能直接承诺。建议 Pi 使用独立稳压/独立电源轨，NodeHexa 通过 Wi-Fi/WebSocket 通信。

### 6. 是否能直接接 Jetson？

不建议视为直接扩展。需要独立电源、散热、重量、安装和安全设计。

### 7. 是否能直接接 ESP32-S3 CAM？

可以作为外部独立模块研究，但不是 Xiaozhi 板的已确认直接能力；还需要视频传输、供电和上位机整合。

### 8. 是否支持 VLM/VLA？

支持外部计算架构，不支持在当前 NodeHexa ESP32 上直接运行。建议模型输出受限高层动作，由 ESP32 负责 IK、限位和舵机安全。

### 9. 能否加入 IMU 闭环稳定？

硬件连接路径可行，软件当前没有被证明已经完成。需要新增采样、滤波、姿态估计、body pose/IK 修正和回退逻辑。

### 10. Xiaozhi 是否限制后续 AI 扩展？

它不会限制所有扩展，但会占用 UART2 并把音频职责固定在一块板上。短期语音 Demo 可保留；长期统一 Camera/Mic/Speaker/Screen/VLM 时，外部 Raspberry Pi/PC 方案更清晰。

### 11. 是否能把 MG90S 换成 30kg 舵机？

不能仅凭 PCA9685 的 PWM 兼容性判定。机械外形、安装耳、舵盘、输出轴、供电和结构强度都必须重新验证；当前应视为需要机械与电源重设计。

### 12. 是否能升级总线舵机？

不是直接升级。需要总线硬件、协议、反馈、供电和机械接口的重大改造。

### 13. NodeHexa 是否适合作为 V1.5 AI 机器人底座？

适合，前提是采用分层架构：NodeHexa 负责实时运动，Pi/PC 负责 AI 与多模态交互，先使用 Wi-Fi/WebSocket，I2C 先接 IMU。

### 14. 现在是否可以宣称“所有计划都能直接实现”？

不可以。摄像头、屏幕、Pi、Jetson、VLA、高扭矩执行器和电源能力仍有明确边界；本报告已把它们分别标为外部板、电源重设计、机械重设计或重大改造。

## 13. 下一步建议

在不改官方 PCB/固件、不采购的前提下，下一步应按这个顺序推进：

1. 对一块实物 PiHexa-V4 做 XT30、VCC、+5V、3V3、GND 的万用表电压确认。
2. 确认 4P I2C 口 SDA/SCL 的空闲上拉电压和上拉阻值。
3. 用一个低风险 I2C 设备做总线扫描，先不接高功耗外设。
4. 记录原版 NodeHexa 运动时的电池电压、舵机 rail 电压跌落和整机电流。
5. 再决定 Xiaozhi 保留为语音副线，还是由 Raspberry Pi 统一音频/视觉/屏幕。
6. 只有完成以上电气基线后，才进入具体传感器、AI 计算板和执行器扩展的采购审计。

**本轮结论：不采购；不修改官方 PCB；不修改官方固件；READY_FOR_PURCHASE = false。**
