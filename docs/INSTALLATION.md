# Cocos AI Copilot 0.1.0 安装说明

## 环境要求

- Cocos Creator `3.8.8`，Windows x64。
- 已安装兼容的 Codex 稳定版，最低 `0.160.1`，建议保持最新稳定版。
- 可用的模型账号或凭据：ChatGPT 登录，或 OpenAI / DeepSeek API Key。
- 项目目录具有写入权限，并允许 Creator 加载项目级扩展。

Codex 是外部运行环境，不包含在扩展 ZIP 中。Cocos AI Copilot 会通过 Codex `app-server` 工作，不要求固定在 `0.160.1`。

## 从正式 ZIP 安装

正式文件：`cocos-ai-copilot-0.1.0.zip`

1. 关闭使用该项目的 Cocos Creator。
2. 如果以前安装过本扩展，先完整删除项目中的旧目录：

   ```text
   <项目目录>\extensions\cocos-ai-copilot
   ```

   不要把新文件覆盖合并到旧目录；如有自定义内容，请先单独备份。

3. 解压正式 ZIP。ZIP 内已经包含：

   ```text
   extensions\cocos-ai-copilot
   ```

4. 将上述 `extensions` 目录合并到项目根目录，或把 `cocos-ai-copilot` 文件夹复制到 `<项目目录>\extensions\`。最终应存在：

   ```text
   <项目目录>\extensions\cocos-ai-copilot\package.json
   ```

5. 重新打开项目。通过 Creator 菜单“AI Copilot”打开面板。
6. 打开设置 → Cocos MCP → 查看详情，确认版本显示 `0.1.0`。

## 从 Cocos 扩展市场安装

商店版本上架后，可在 Cocos 扩展市场安装 `Cocos AI Copilot`，然后重新打开对应项目。若从早期手动包升级后出现入口文件或模块缺失，请关闭 Creator，完整移除旧扩展目录，再执行一次干净安装。

## 首次连接 Codex

1. 打开 AI Copilot 设置 → Runtime。
2. 点击检查运行状态，让扩展自动发现兼容的 Codex 安装。
3. 自动发现失败时，选择 Codex 可执行程序本身，然后点击“测试连接并保存”。不要选择 Cocos Creator 或 ChatGPT 的桌面快捷方式。
4. 若 Codex 后续安装到了新位置，可使用“恢复自动检测”，或重新选择新版程序。

连接过程会真实启动 Codex app-server 并检查版本。低于 `0.160.1` 或预发布版本会被拒绝；更高稳定版允许连接并建议优先使用。

## 配置模型服务

打开设置 → 模型服务，选择以下一种方式：

- OpenAI：使用系统 Codex 的 ChatGPT 登录；或
- OpenAI：配置并验证 API Key；或
- DeepSeek：配置并验证 API Key。

密钥、登录状态和网络连接由用户环境提供，不包含在发布包中。

## 验证安装

完成安装后进行轻量检查即可：

1. AI Copilot 面板可以打开。
2. 设置 → Cocos MCP 显示内置 Runtime 已连接，Tools 可用，4 / 4 Skills 已就绪。
3. Runtime 页面显示兼容的 Codex 版本和连接状态。
4. 新建会话并请求“读取当前场景和层级，不做修改”，确认返回当前项目的 Scene / Hierarchy 信息。

## 卸载

关闭 Creator 后删除：

```text
<项目目录>\extensions\cocos-ai-copilot
```

扩展不会随卸载删除项目中已经创建或修改的游戏资源。删除前请使用版本控制或项目备份确认需要保留的内容。

