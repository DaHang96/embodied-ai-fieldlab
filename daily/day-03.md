# Day 03

## Today's Goal

完成 NodeHexa 到货前的环境与控制链准备，并验证 RTX 3060 Laptop + Remote GPU 架构中的最小软件链路；没有硬件时只做替代验证。

## Why It Matters

环境问题往往是开发者第一次成功前最大的隐形成本。把它提前暴露，既能减少后续返工，也能直接形成 Developer Experience 素材。

## Tasks

1. 记录 NodeHexa 官方仓库、固件、控制入口和当前版本信息，标记已确认与待到货验证项。
2. 完成本地 Windows/WSL 环境的最小检查，记录 OS、Python、驱动、显存、磁盘和关键工具版本。
3. 为到货后的 USB 烧录、串口/Wi-Fi 控制和安全停机准备验证清单；不把清单写成已运行结果。
4. 复核 RTX 3060 Laptop + Remote GPU 的职责边界：本地控制/采集/轻量推理，Remote GPU 训练或较大模型实验。
5. 如果环境无法完成软件 smoke test，记录阻塞并切换到文档旅程、代码审计或数据格式验证，不进行无目的排错。

## Robot Practice

验证“控制命令 → NodeHexa 固件/接口 → 机器人动作”链路中目前能验证的软件环节。没有硬件时，不把示例运行称为真实机器人成功。

## Knowledge

- Python 环境、驱动、硬件接口、数据集格式为什么会影响机器人实践。
- smoke test、reproducibility、版本锁定和日志的作用。

## Developer Experience

重点记录：官方是否解释了 Windows/Linux 边界、GPU 要求、安装顺序和预期输出；错误信息是否告诉新手下一步该做什么。

## Content Idea of the Day

- Content Level：**A**
- Hook：**“机器人还没到，我先要证明自己的电脑不会在第一步就把它拦在门外。”**
- Core Conflict：开源项目的代码可以提前下载，但真正的控制链还要面对版本、端口、驱动、网络和硬件到货后的未知变量。
- Visual Moment：电脑配置、RTX 3060 显存、终端命令、成功输出、难懂的报错和本地/云端链路图交替出现。
- Experiment：从零复核 NodeHexa 的软件入口和本地/远程算力分工，记录今天真正验证了什么、还缺什么硬件证据。
- Failure Possibility：依赖冲突、驱动不兼容、显存不足或文档命令过时，导致机器人还无法进入真实控制链。
- Payoff：观众看到“机器人项目的第一关可能不是 AI，而是让电脑和控制链先准备好”。
- Platforms：Bilibili、抖音、小红书、YouTube、X。
- Long-form Potential：Setup Guide + Troubleshooting Note。

## Website Content Opportunity

有：`NodeHexa 到货前环境与控制链准备`。如果出现真实错误和解决步骤，适合沉淀为 Troubleshooting；不要在本项目中做关键词或站内优化。

## Assets Created

- `robot-arm/setup/environment-baseline.md`
- 一次 smoke test 日志
- 依赖/错误/解决记录
- 内容选题卡 03

## Portfolio Value

为 Case Study 01 的环境证据、Case Study 02 的 Onboarding 痛点、Case Study 03 的复现教程素材提供基础。

## Reflection

填写：今天最耗时的步骤是什么？如果只能改官方文档一处，我会改哪一处？

## Tomorrow

把真实上手路径画成新开发者 Journey Map，明确从 Discovery 到 First Success 的断点。

