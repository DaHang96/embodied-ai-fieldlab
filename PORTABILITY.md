# Portability and New-Computer Setup

> 用途：确保项目换到另一台电脑后，文档、Codex 执行规则、机器人阶段依赖和研究流程仍能继续。
>
> 当前状态：`DOCUMENTS_PORTABLE = true`；`FULL_EXECUTION_PORTABLE = PENDING_NEW_MACHINE_SMOKE_TEST`

## 1. 当前结论

项目的核心 Markdown、研究记录、Persona、PeterStudio Voice 和项目级写作 Skills 已纳入 Git，可以通过 clone 恢复。

但以下内容不会自动随仓库恢复：

- 用户级 Codex Skills；
- 浏览器登录状态、淘宝登录状态和验证码处理状态；
- SSH 私钥、Remote GPU 登录配置和本机凭据；
- Windows/WSL、VS Code、PlatformIO、USB 驱动和机器人硬件；
- 未纳入 Git 的原始视频、数据集、模型和临时文件。

因此，换电脑时需要完成本文件的安装清单和 Smoke Test，不能只 clone 后就假设机器人环境已经可运行。

## 2. 恢复顺序

### Step 1 — Clone

```powershell
git clone https://github.com/DaHang96/embodied-ai-fieldlab.git
Set-Location embodied-ai-fieldlab
git status
```

仓库路径可以不同；项目文档使用相对链接，不要求固定在 D 盘。

### Step 2 — 验证项目文件

```powershell
rg --files -g '*.md' -g '*.json' | Measure-Object
Test-Path .\README.md
Test-Path .\PROGRESS.md
Test-Path .\docs\project-state\current-state.md
Test-Path .\.agents\skills\blog-persona\SKILL.md
Test-Path .\.agents\skills\writing-tech-post\SKILL.md
```

### Step 3 — 恢复项目级 Skills

以下 Skills 已经在仓库内：

- `.agents/skills/blog-persona/`
- `.agents/skills/writing-tech-post/`

它们不依赖当前电脑的绝对路径。

### Step 4 — 按需安装用户级操作 Skills

淘宝研究和浏览器自动化属于用户级工具，不把登录状态或临时浏览器数据提交进仓库。需要在新电脑按官方来源重新安装：

| Skill | 用途 | 作用域 |
|---|---|---|
| `browser-act` | 浏览器自动化 | 用户级 |
| `taobao-keyword-search` | 淘宝关键词搜索 | 用户级 |
| `taobao-product-detail` | 淘宝商品 DOM 详情 | 用户级 |
| `taobao-product-engineering-detail` | 淘宝详情长图工程参数 | 用户级 |
| `taobao-sku-detail` | 淘宝目标 SKU 真实价格 | 用户级 |
| `taobao-sku-image-detail` | 淘宝 SKU 商品图库审计 | 用户级 |
| `hexapod-procurement` | 六足机器人采购分析编排 | 用户级 |

安装后，应确认它们位于新电脑的 `%USERPROFILE%\.agents\skills\`，而不是依赖本项目中的临时目录。淘宝登录必须由用户人工完成，项目不保存账号信息。

### Step 5 — 恢复机器人开发环境

NodeHexa 到货后再安装和验证：

- VS Code；
- PlatformIO；
- Arduino/ESP32 或项目要求的 PlatformIO 工具链；
- USB 数据线和对应串口驱动；
- NodeHexa 固件/控制代码；
- 本地 Windows 与 WSL/Remote GPU 的职责边界。

这些属于硬件执行阶段依赖，不应在尚未到货时伪装成已验证环境。

## 3. 当前电脑相关信息

RTX 3060 Laptop、Windows/WSL、实验室 SSH 和桌面尺寸属于当前执行环境事实，记录在：

- `robot-arm/setup/environment-baseline.md`
- `PROGRESS.md`

换电脑后必须重新测量并追加新环境记录，不覆盖旧电脑证据。

## 4. Smoke Test Definition

新电脑达到可继续执行的最低标准：

- Git clone 成功；
- README、当前状态和 Day 文件可以打开；
- 项目级 Skills 可以被 Codex 发现；
- `rg --files` 能发现主要目录；
- Guided Execution Mode 可以读取当前状态；
- NodeHexa 到货后，VS Code/PlatformIO 能识别项目和串口；
- 第一次真实运动前完成电源、急停和连接检查。

只有完成新电脑 Smoke Test，才将：

```text
FULL_EXECUTION_PORTABLE = true
```

## 5. 禁止同步的内容

- API key、密码、Cookie、淘宝登录信息；
- SSH 私钥和 Remote GPU 凭据；
- 浏览器 profile；
- 未经整理的模型、数据集和大型原始视频；
- 当前电脑的临时路径、临时下载目录和本地缓存。

## 6. 当前主工作区

当前电脑的主工作区是历史事实，不是跨电脑运行要求：

```text
D:\embodied-ai-v2-new\embodied-ai-fieldlab
```

项目在其他电脑上应以 clone 后的实际路径作为根目录，所有新增文档必须优先使用相对路径或占位符。
