# Environment Baseline

> Day 1–3 填写。不要把“应该支持”写成“已经验证”。

## System

- 记录日期：2026-08-28
- OS / 版本：Windows 10 Home China；OS Build 26200；WindowsDisplayVersion 未返回
- Linux / WSL / 远程 Linux：WSL 默认版本 2；实验室远程 SSH 可用
- CPU：AMD Ryzen 7 5800H
- RAM：17024741376 bytes，约 16 GB
- GPU / 显存：NVIDIA GeForce RTX 3060 Laptop / 6144 MiB（6 GB）
- 可用磁盘：C 盘总容量 214748360704 bytes，约 200 GB；剩余 23505158144 bytes，约 21.9 GB
- 摄像头：Integrated Camera；PnP 状态 OK

## Software

- Python / 包管理方式：
- Git：
- CUDA / Driver（如适用）：Driver 561.17；`nvidia-smi` 报告 CUDA 12.6；CUDA Toolkit 是否安装待确认
- 机器人项目 / commit：
- 关键依赖版本：

## Smoke Test

| 步骤 | 命令/入口 | 预期输出 | 实际输出 | 耗时 | 状态 | 证据 |
|---|---|---|---|---:|---|---|
| 1 | `nvidia-smi` | 能读取 GPU、显存、驱动和 CUDA 支持信息 | RTX 3060 Laptop；6144 MiB；Driver 561.17；CUDA 12.6；GPU Util 4% | 用户未提供 | 通过 | 用户提供的 PowerShell 输出 |
| 2 |  |  |  |  |  |  |
| 3 |  |  |  |  |  |  |

## Errors and Fixes

| 错误 | 首次出现步骤 | 解决/绕过 | 来源 | 是否可复现 |
|---|---|---|---|---|
| `nvidia-smi` 的首次环境状态 | Day 1 / Guided Step 2 | 当前 PowerShell 已成功读取 GPU；之前的失败记录保留为历史环境信息，不作为当前结果 | 用户终端输出 | 已复核 |

## Boundary

- 已验证：
- 仅完成替代验证：
- 仍需真实硬件验证：

### Guided Execution 记录

- Step 2 已完成：通过 Windows PowerShell 的 `nvidia-smi` 确认 RTX 3060 Laptop、6 GB 显存、驱动 561.17 和驱动报告的 CUDA 12.6。
- 边界：CUDA Toolkit 是否安装、CPU、RAM、磁盘和 Camera 尚未验证。

### Step 3：系统、CPU、RAM 与磁盘

- Step 3 已完成：Windows 10 Home China / OS Build 26200；AMD Ryzen 7 5800H；约 16 GB RAM；C 盘约 200 GB，剩余约 21.9 GB。
- 边界：WindowsDisplayVersion 和 CUDA Toolkit 尚未验证；磁盘剩余空间偏紧，后续需要管理数据集与模型文件。

### Step 4：摄像头与 Linux 环境

- Step 4 已完成：PowerShell 检测到 `Integrated Camera`，PnP 状态为 `OK`；`wsl --status` 确认默认版本为 2。
- 当前架构：Windows 本地负责机器人控制、摄像头、遥操作、数据采集与轻量推理；WSL2 或实验室远程 SSH 用于 Linux 工具链和较重实验，具体分工待后续验证。
- 边界：摄像头实际画面采集、Python/机器人依赖、实验室 SSH 连接细节尚未验证。

### Step 5：桌面空间与安全边界

- Step 5 已完成：桌面约 150 × 50 × 100 cm（长 × 宽 × 高），木质桌面，可固定底座；放置位置灵活，附近无墙、显示器或其他障碍物。
- 环境风险：无宠物、儿童或他人进入实验区域；当前无额外噪音或运动范围限制。
- 物体边界：用户表示允许接触的物体“都可以”、明确禁止接触的物体“都可以”；按“暂无特定禁触物体”记录，但实验仍默认禁止刀具、玻璃、液体、易碎品和靠近人体的动作。

### Step 7：桌面环境基线证据

- Step 7 已完成：已保存桌面全景照片 [`desk-baseline.jpg`](../../assets/day-01/desk-baseline.jpg)。
- 第一条观察：桌面面积足够，但现实工作区被笔记本支架、键盘、鼠标、饮品、杂物、线缆和两侧架体占据；机械臂进入生活场景后，首先需要面对“在真实杂乱桌面中找到安全可用空间”，而不是只在理想空桌面上完成动作。
- 工程含义：后续需要先规划一个可重复清空的工作区，并验证 Camera 对桌面边界、物体和线缆的可见性；照片是环境证据，不等于机器人 Camera 已完成采集验证。

