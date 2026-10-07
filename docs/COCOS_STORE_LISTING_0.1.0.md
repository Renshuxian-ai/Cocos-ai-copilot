# Cocos 扩展市场上架文案 — Cocos AI Copilot 0.1.0

## 产品名称

Cocos AI Copilot

## 一句话介绍

在 Cocos Creator 内，用自然语言驱动场景、资源与 Preview / Runtime 验证。

## 详细介绍

Cocos AI Copilot 是面向 Cocos Creator 的项目内 AI 开发助手。它以可停靠面板运行，通过 Codex app-server 连接模型与工具，并使用扩展自带的 Cocos Runtime 理解当前项目、场景层级、节点、组件和资源。

你可以直接描述要完成的开发目标：读取或调整 Scene / Node / Component，处理和导入图片、音频资源，配置 SpriteFrame 或 AudioSource，运行 Preview，检查运行时状态与错误，再通过 Review 查看本次改动。对于受支持且前置条件仍成立的改动，还可以执行 Undo。

Cocos AI Copilot 强调可检查的工程流程：图片与音频以聊天 Artifact 交付，资源导入需要 AssetDB 就绪证据，Preview 操作与当前运行会话绑定，Runtime errors 保留来源和堆栈，项目写入进入 Review。它帮助开发者减少重复操作，但不会替代代码审查、版本控制、人工试玩和目标平台测试。

## 核心功能亮点

- 自然语言 Cocos 开发：在 Creator 内描述目标，读取项目上下文并执行对应 Cocos 工作流。
- Scene / Node / Component：检查与操作场景、层级、节点、组件、常见 UI、Prefab 和资源引用。
- 图片资源工作流：图片生成/附件聊天卡片、会话持久化、去重、裁剪、透明处理、缩放、旋转、颜色调整、合成、遮罩、Sprite Sheet、Nine-Slice、过滤、导入与场景放置。
- 音频资源工作流：WAV / MP3 / OGG 试听与处理、版本保存、AudioClip 导入、AudioSource 配置和运行时验证。
- Preview / Runtime 验证：启动或复用 Preview，在 Game View 发送会话绑定的键盘、鼠标和触摸输入，读取语义状态并按需截图。
- Runtime Error Capture：捕获当前 Game View Preview 会话的 `console.error`、未捕获异常和未处理 Promise rejection，保留堆栈、来源位置与重复次数。
- Review / Undo：按 Turn 审阅已记录的项目改动，定位目标，并在安全前置条件满足时撤销支持的改动。
- 内置 Cocos Runtime：无需另装独立 Cocos MCP 扩展。
- 4 项 Built-in Skills：Cocos MCP Workflow、UI Composition、2D Image Toolkit、Preview Debug。
- 外部 MCP 配置：支持手动管理本地 stdio 或远程 HTTP 服务。

## 安装方法

### 扩展市场

在 Cocos 扩展市场安装 `Cocos AI Copilot`，然后重新打开目标项目，通过菜单“AI Copilot”打开面板。

### 手动 ZIP

1. 关闭 Cocos Creator。
2. 如已安装旧版，完整删除 `<项目目录>\extensions\cocos-ai-copilot`，不要覆盖合并旧目录。
3. 解压正式 ZIP，将其中的 `extensions\cocos-ai-copilot` 放到项目对应目录。
4. 重新打开项目，并在设置 → Cocos MCP → 查看详情中确认版本为 `0.1.0`。

## 首次使用方法

1. 打开 AI Copilot 设置 → Runtime，确认自动发现的 Codex 已连接；如自动发现失败，手动选择 Codex 可执行程序并测试连接。
2. 在模型服务中使用 ChatGPT 登录，或配置并验证 OpenAI / DeepSeek API Key。
3. 在 Cocos MCP 页面确认内置 Runtime、Tools 和 4 / 4 Skills 已就绪。
4. 新建会话，先请求 Copilot 读取当前 Scene / Hierarchy，再描述要实现的改动、限制和验证标准。
5. 完成后检查 Artifact、Preview / Runtime 证据和 Review；需要回退时再使用 Undo。

## 适用版本

- Cocos AI Copilot：`0.1.0`
- 已验证并正式支持：Cocos Creator `3.8.8`，Windows x64
- Codex：`0.160.1` 或更高稳定版，建议使用最新稳定版

Codex 以 app-server 模式连接。Codex 本体、模型账号和 API 凭据不包含在本扩展中。

## 已知限制

- 其他 Cocos Creator 版本和操作系统尚未完成 `0.1.0` 正式认证。
- Codex 预发布版本不在当前兼容策略内；未来稳定版虽允许连接，但不代表已逐版认证。
- Runtime Error Capture 以当前 Creator Game View Preview 会话为主要边界，不替代浏览器、模拟器和原生构建的全平台日志验证。
- Review / Undo 不能替代版本控制；只覆盖已记录、受支持且仍满足身份与前置条件的改动。
- 自动输入、状态读取和截图不等于完整人工试玩或目标设备验收。
- 图片和音频生成质量、内容权利、模型与外部 MCP 的可用性取决于相应服务和用户配置。

## 建议截图清单

1. Cocos Creator 主界面 + 停靠的 AI Copilot 面板，展示自然语言请求与执行结果。
2. Scene / Hierarchy / Inspector 与 Copilot 同屏，展示 Node / Component 操作前后对照。
3. 聊天中的多张图片 Artifact 卡片，以及图片编辑/预览工作台。
4. 音频 Artifact 卡片与音频编辑工作台，展示波形、裁切/淡入淡出和 AudioSource 配置。
5. Game View Preview 与运行时验证证据，展示输入结果、状态读取和截图。
6. Runtime Error Capture，展示结构化错误、来源位置、堆栈和重复次数；使用演示错误，不包含用户隐私。
7. Review / Undo 页面，展示一次 Turn 的 Scene、Node、Component 或资源改动及撤销状态。
8. 设置 → Cocos MCP，展示版本 `0.1.0`、内置 Tools 和 4 / 4 Skills 已就绪。
9. 外部 MCP 配置页，展示本地 stdio / 远程 HTTP 的配置入口；不要展示真实密钥。

## 建议演示视频清单

建议制作一段 60–90 秒、未经能力夸大的真实录屏：

1. 打开已安装的扩展并确认 Runtime / Cocos MCP 就绪。
2. 用自然语言读取当前场景并新增或调整一个 UI 节点与组件。
3. 生成或附加一张图片，展示聊天 Artifact、导入 SpriteFrame 和场景绑定。
4. 导入一段音频，展示音频处理、AudioClip / AudioSource 配置。
5. 启动 Game View Preview，完成一次输入与状态验证，并展示 Runtime Error Capture。
6. 打开 Review 查看改动，再演示一次满足前置条件的 Undo。

录制中应使用真实运行结果，避免剪辑出尚未实现的功能，也不要露出 API Key、项目私有路径或用户账号信息。

