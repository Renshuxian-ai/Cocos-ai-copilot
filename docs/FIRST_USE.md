# Cocos AI Copilot 0.1.0 首次使用说明

## 1. 打开并确认环境

1. 在 Cocos Creator 中打开目标项目。
2. 通过菜单“AI Copilot”打开可停靠面板。
3. 打开设置 → Runtime，确认 Codex 已连接。最低兼容版本为 `0.160.1`，建议使用最新稳定版。
4. 打开设置 → 模型服务，完成 ChatGPT 登录，或配置并验证 OpenAI / DeepSeek API Key。
5. 打开设置 → Cocos MCP，确认内置 Cocos Runtime 已连接、Tools 可用，并显示 4 / 4 Skills 已就绪。

## 2. 从只读检查开始

第一次进入项目时，先让 Copilot 建立上下文。例如：

> 读取当前场景、Hierarchy 和选中节点，概括现有 UI 结构，先不要修改任何内容。

确认 Copilot 返回的是当前项目和当前场景后，再描述修改目标、不可破坏的部分以及验收条件。

## 3. Scene / Node / Component 工作流

可以用自然语言要求 Copilot：

- 检查或创建 Scene、Node、Canvas、Label、Button、Sprite、Camera；
- 调整 Node 的位置、旋转、缩放、激活状态；
- 检查、添加、移除或配置 Component；
- 处理 Prefab、资源引用和脚本诊断；
- 保存场景并通过 Preview 验证。

推荐在请求中写清目标节点、期望值和验证方式。例如：

> 在当前 Canvas 下添加一个名为 StartButton 的按钮，保持现有层级不变；绑定完成后读取组件属性，并在 Game View Preview 中验证点击事件和显示结果。

## 4. 图片资源工作流

可以发送图片附件，或让支持图片生成的当前模型交付图片。正式流程会把交付图片登记为当前聊天消息的图片 Artifact 卡片；重新打开会话后卡片仍应存在，同一图片不会因后续检视重复登记。

可请求的处理包括裁剪、透明边缘清理、缩放、画布扩展、翻转、旋转、透明度和颜色调整、合成、遮罩、Sprite Sheet、Nine-Slice、像素画过滤，以及导入、配置和放置到场景。

建议明确：

- 输出尺寸和 PNG / JPEG 格式；
- 是否需要透明背景；
- 是否使用 nearest 像素过滤；
- 目标项目路径；
- 是否放入场景并运行 Preview 验证。

图片写入项目后，仍应以 AssetDB 返回的 ImageAsset / SpriteFrame 标识和场景读取结果为准；“已生成图片”或“已检视图片”本身不等同于“已导入并绑定到项目”。

## 5. 音频资源工作流

音频 Artifact 可在聊天中试听并进入音频编辑工作台。支持 WAV、MP3、OGG 的裁切、淡入淡出、增益、归一化、声道、采样率和格式处理；处理结果可以保存为新版本、导入项目、配置 AudioSource，并在 Preview 中验证。

导入与绑定是两个独立步骤：只有 AssetDB 确认 AudioClip 就绪，且 AudioSource 读取结果与预期一致，才算配置完成。

## 6. Preview / Runtime 验证

需要运行验证时，在请求中明确授权启动 Preview。Copilot 可以启动或复用 Creator Preview，并在 Game View 内发送会话绑定的键盘、鼠标或触摸输入。

一次可靠验证通常同时包含：

- 输入或操作返回的 Preview 会话标识；
- 同一会话中的节点、组件、游戏状态或可见文本变化；
- 当视觉布局重要时，再补充 Game View 截图。

发送成功只证明输入已投递，不等于玩法结果已经正确。

## 7. Runtime Error Capture

若 Preview 出现异常，可要求：

> 读取当前 Game View Preview 会话的 Runtime errors，按来源文件、行号、堆栈和重复次数汇总；先诊断，不修改。

错误捕获覆盖当前会话的 `console.error`、未捕获异常和未处理 Promise rejection。修复后需要在新的 Preview 会话中重新触发原路径，再确认错误没有复现。

## 8. Review / Undo

完成项目写入后，打开 Review 查看本 Turn 记录的文件、资源、Scene、Node 和 Component 变更。Undo 只会尝试撤销受支持且身份、哈希或前置条件仍匹配的内容；若目标后来被人工或其他 Turn 改动，会报告冲突。

Undo 不是版本控制。重要项目仍应使用 Git 或其他备份方式。

## 9. 外部 MCP（可选）

设置 → MCP 服务支持手动添加：

- 本地 stdio 服务：选择脚本或可执行文件；JavaScript 服务会自动查找 Node.js，必要时再手动指定。
- 远程 HTTP 服务：填写服务地址和需要的认证配置。

“目标应用程序”表示 MCP 服务要控制的软件；工作目录、环境变量和附加参数属于高级配置。外部 MCP 的来源、权限与安全性应由用户自行确认。

## 10. 推荐使用方式

- 先检查，再修改；把不能破坏的对象写进请求。
- 对大任务分阶段设定可验证结果，但不要把同一已成功写入反复执行。
- 资源生成、项目导入、场景绑定和 Runtime 验证要分别确认。
- 每个重要 Turn 检查 Artifact、Activity、Review 和 Runtime 证据。
- 发布前始终进行人工试玩和目标平台测试。
