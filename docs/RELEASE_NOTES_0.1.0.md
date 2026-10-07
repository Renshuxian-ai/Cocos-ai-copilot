# Cocos AI Copilot 0.1.0 Release Notes

发布日期：2026-10-07

## 发布摘要

Cocos AI Copilot 0.1.0 是首个正式版本。它把 Codex 的自然语言工作流带入 Cocos Creator，并通过内置 Cocos Runtime、Built-in Skills、资源工作台、Preview / Runtime 证据和 Review / Undo，形成从“描述目标”到“检查改动和运行结果”的项目内闭环。

本次正式包直接使用已在第二台全新电脑完成真实验收的 RC ZIP。包内版本原本已经是 `0.1.0`，未包含 RC 专用逻辑或用户可见 RC 标记，因此没有重新构建或重新打包，只把文件名改为 `cocos-ai-copilot-0.1.0.zip`。重命名前后的文件大小和 SHA256 完全一致。

## 重点能力

- 在 Creator 内通过自然语言检查和操作 Scene、Node、Component、Prefab 与项目资源。
- 图片生成/附件以聊天 Artifact 卡片交付并随会话保存；支持处理、导入、SpriteFrame 配置、场景绑定和 Preview 验证。
- 音频以聊天 Artifact 交付；支持处理、导入 AudioClip、配置 AudioSource 和 Preview / Runtime 验证。
- 启动或复用 Preview，发送会话绑定的 Game View 输入，读取运行时状态并在需要时截图。
- 捕获当前 Game View Preview 会话中的 Runtime errors、异常堆栈和重复次数。
- 通过 Review 检查每个 Turn 的项目改动，并对满足前置条件的受支持改动执行 Undo。
- 内置 Cocos Runtime 和 4 项 Skills；可选配置本地 stdio 或远程 HTTP 外部 MCP。

## 兼容性

- 正式支持并完成验收：Cocos Creator `3.8.8`，Windows x64。
- Codex 最低兼容版本：`0.160.1` 稳定版。
- 推荐：使用当前最新 Codex 稳定版。更高稳定版允许连接，但不表示每个未来版本都已逐版认证。
- Codex 以 app-server 模式运行；Codex 本体、账号和 API 凭据不包含在扩展包中。

## 安装与升级注意

手动安装或从早期包升级时，请先关闭 Creator 并完整删除旧的 `extensions/cocos-ai-copilot`，然后干净复制正式包中的同名目录。不要覆盖合并旧目录，以免残留文件造成入口或模块不一致。

## 发布完整性

- 正式文件名：`cocos-ai-copilot-0.1.0.zip`
- 大小：`2,248,843 bytes`
- SHA256：`38121A724018D93F95CB4A0E5FC03DF6B193FF8F1CFF140E87CE22B4919B3426`
- 包内生产文件：818
- 与已验收 RC：字节内容完全一致，仅文件名变化

## 已知限制

- `0.1.0` 未认证其他 Creator 版本、macOS 或 Linux。
- Preview Runtime Error Capture 以当前 Creator Game View Preview 会话为边界。
- Review / Undo 仅处理已记录且仍满足身份与前置条件的受支持改动；冲突需人工解决。
- 自动 Preview 操作不是完整游戏通关、设备兼容性或发布质量证明，最终发布仍需开发者审核和人工试玩。
- 外部 MCP、模型服务以及生成媒体的可用性、权限与内容责任取决于相应服务和用户配置。

