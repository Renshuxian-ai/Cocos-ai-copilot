# Changelog

本文件记录 Cocos AI Copilot 的正式版本变化。

## 0.1.0 — 2026-10-07

首个正式版本。

### 新增

- 在 Cocos Creator 内提供可停靠的 AI Copilot 聊天与执行面板。
- 通过 Codex app-server 连接模型、权限审批、Skills 和 MCP 服务；兼容 Codex `0.160.1` 及更高稳定版，推荐最新稳定版。
- 内置 Cocos Runtime，覆盖 Scene、Hierarchy、Node、Component、Prefab、资源、脚本诊断、Preview、截图和运行时输入等 Cocos 操作。
- 内置 4 项 Skills：Cocos MCP Workflow revision 6、UI Composition revision 4、2D Image Toolkit revision 2、Preview Debug revision 4。
- 图片 Artifact、会话持久化、图片处理、AssetDB 导入、SpriteFrame 配置与场景放置工作流。
- 音频 Artifact、WAV / MP3 / OGG 处理、AssetDB 导入、AudioSource 配置与 Preview 验证工作流。
- 当前 Game View Preview 会话的 Runtime Error Capture，包含结构化错误、堆栈、来源位置、去重计数和会话边界。
- Turn 级 Review、目标定位和带身份/前置条件检查的 Undo。
- 本地 stdio 与远程 HTTP 外部 MCP 配置，以及当前 Cocos 扩展中相关服务的识别展示。
- 会话保存、归档、附件、排队消息、Turn 进行中调整方向、模型与权限选择。

### 修复与稳定性

- 修复 Codex 图片生成完成事件只有结构化 `result` 时首条回复不显示图片 Artifact 的问题；补充内容哈希去重和会话重开恢复。
- 明确并强制区分 `cc.assetManager.loadAny(id, callback)` 与 `cc.resources.load(path, cc.SpriteFrame, callback)`；错误参数在执行前返回明确错误，目标绑定和共用加载器提供类型检查及有界超时。
- 修复首次图片和音频导入时项目目录、AssetDB 刷新与 ImageAsset / SpriteFrame / AudioClip 就绪等待链路。
- 修复本机代理可能把 loopback Cocos MCP 请求转发并造成 HTTP 502 的问题，同时保留用户已有代理配置。
- 修复 MCP 已连接但 Cocos Tools 没有进入当前会话的问题。
- 修复 Shadow DOM 事件重定向导致排队消息“编辑消息”无响应的问题；编辑后原文字、附件和钉子会回填到消息框，原消息 ID 与 FIFO 顺序保持不变。
- 设置 → Cocos MCP → 查看详情中的版本改为显示 Copilot 产品版本 `0.1.0`，不再显示内部 Runtime 版本。
- 完善 Preview 输入取消、失败/恢复状态、脚本作用域、诊断噪音分类、MCP 状态与配置字段持久化。

### 已验证范围

- Cocos Creator `3.8.8`，Windows x64。
- 已验收 RC 在第二台全新电脑完成真实安装、模型流程、资源工作流、Preview / Runtime 与人工玩法验收后，原 ZIP 未重建、未重打包，仅改为正式文件名。

### 已知限制

- 其他 Cocos Creator 版本和操作系统尚未作为 `0.1.0` 的正式支持矩阵完成认证。
- Codex、模型账号和 API 凭据需由用户另行提供。
- Review / Undo 不能替代版本控制，也不能无条件覆盖冲突或撤销未记录的外部修改。
- Preview 自动输入和截图不能替代完整人工试玩、设备测试和原生构建验收。
- Runtime Error Capture 以当前 Creator Game View Preview 会话为主要边界。

