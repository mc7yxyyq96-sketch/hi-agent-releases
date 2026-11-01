# Hi Agent 下载 · v0.2.0 免费预览版

**Hi Agent** 是一个桌面 AI 编程助手：它能帮你读代码、改代码、跑命令，但每一步都先问你，记得你教过它什么，花多少钱也一清二楚。

> 这是**免费预览版**，**不开源**：这个仓库只放安装包和说明，不含源代码。软件本身免费，模型费用由你自己的模型账号（例如 DeepSeek）按实际用量付费。

## 三个卖点

1. **便宜，花费可控**：支持 DeepSeek（也支持 OpenAI、Anthropic、Gemini、通义千问、智谱 GLM、Kimi、Ollama 等）。“用量”页面能看到每次对话花了多少钱，还能设每日花费上限，超出时提醒，也可以选择到限额就自动停止。
2. **记忆和经验看得见、能撤销**：它记住的习惯、从做过的事里总结的经验，都能在“记忆、指令与经验”页面查看、编辑、撤销；不管用的经验会自动停用。
3. **动手前先问你，做错了能回退**：改文件、跑命令之前都要你点“允许”；用“回退”可以把对话退回到任意一条消息之前，改过的文件一起还原。

还有：手机网页可以看进度、批准操作；数据都存在你自己的电脑上。

## 下载

在 [Releases](../../releases/latest) 页面下载对应文件：

| 系统 | 文件 | 大小 |
| --- | --- | --- |
| Windows 10/11（64 位） | `hi-agent-setup-0.2.0-x64.exe` | 126 MB |
| Linux（x86_64，通用） | `hi-agent-0.2.0-x86_64.AppImage` | 129 MB |
| Debian / Ubuntu | `hi-agent_0.2.0_amd64.deb` | 111 MB |
| macOS | 暂未提供，后续补上 | — |

`SHA256SUMS.txt` 里是每个文件的校验值，可以用来确认下载没有损坏：
- Linux：`sha256sum -c SHA256SUMS.txt --ignore-missing`
- Windows（PowerShell）：`Get-FileHash .\hi-agent-setup-0.2.0-x64.exe`，和文件里的值对比。

## 安装

### Windows

1. 双击 `hi-agent-setup-0.2.0-x64.exe`。默认只为当前用户安装，可以自选安装目录。
2. 安装包**没有数字签名**，所以 Windows 可能会弹出蓝色的“**Windows 已保护你的电脑**”（未知发布者）提示。确认文件是从本仓库 Releases 下载的、校验值也对得上之后，点 **更多信息** → **仍要运行**。
3. 如果浏览器提示“此文件不常被下载”，选择 **保留** / **仍然保留**。
4. 装好后从开始菜单打开 “Hi Agent”。

> Windows 版是在 Linux 上打包的，还没有在大量 Windows 电脑上测试过。遇到问题欢迎反馈。

### Linux（AppImage）

```bash
chmod +x hi-agent-0.2.0-x86_64.AppImage
./hi-agent-0.2.0-x86_64.AppImage
```

也可以在文件管理器里右键 → 属性 → 勾选“允许作为程序执行”，然后双击打开。不需要安装 libfuse2，Ubuntu 22.04+、Fedora 都能直接运行。如果系统不支持 FUSE（例如某些容器），可以用 `APPIMAGE_EXTRACT_AND_RUN=1 ./hi-agent-0.2.0-x86_64.AppImage`。

### Debian / Ubuntu（deb）

```bash
sudo apt install ./hi-agent_0.2.0_amd64.deb
```

然后从应用菜单打开 “Hi Agent”。

## 第一次使用

1. 打开后会有 4 步欢迎引导：选语言和主题 → 连接模型（填你自己的 API 密钥，也可以先用离线的免费演示模型） → 了解你怎么掌控它 → 数据隐私说明。
2. 打开一个项目文件夹，直接用中文告诉它要做什么。它要改文件或跑命令时会先问你。
3. 在“用量”里设置每日花费上限。

密钥保存在系统钥匙串里；如果 Linux 上没有钥匙串服务，会退回到本地文件并提示你。

## 数据和隐私

- 对话、记忆、经验、设置都保存在你电脑上的 `~/.agent/` 文件夹，桌面应用数据在 `~/.config/@agent/desktop`（Windows：`%APPDATA%\@agent\desktop`）。
- 崩溃报告默认关闭，打开后也只存在本机，不会上传。反馈也是保存成本地文件。
- 你和模型之间的对话内容会发送给你选择的模型服务商（例如 DeepSeek）。
- 卸载不会删除上面的数据文件夹，想彻底清除请手动删除。

## 已知限制

- 暂无 macOS 版。
- 安装包没有签名；也没有自动更新，新版本请回到这里下载后覆盖安装。
- 预览版功能还会变化，欢迎提 Issue 反馈问题和想法。

---

## English

**Hi Agent** is a desktop AI coding agent. It reads and edits code and runs commands, but asks before every action, remembers what you taught it, and shows what you spend.

This is a **free, closed-source preview**: this repo only hosts installers and docs, no source code. The app is free; you pay your model provider (e.g. DeepSeek) for usage.

**Highlights**
- **Cheap, with a spending cap**: DeepSeek (and OpenAI, Anthropic, Gemini, Qwen, GLM, Kimi, Ollama…). The Usage page shows cost per chat; set a daily cap that warns, or optionally hard-stops.
- **Memory and lessons you can see and undo**: view, edit, or undo anything it remembered or learned; lessons that don't help are retired automatically.
- **Approval before every action, plus Rewind**: file edits and commands wait for your OK; Rewind returns the chat to any earlier message and restores the files.

**Install**
- **Windows**: run `hi-agent-setup-0.2.0-x64.exe`. It is unsigned, so SmartScreen may say "Windows protected your PC" (unknown publisher). If you downloaded it from this repo's Releases and the SHA256 matches, click **More info → Run anyway**.
- **Linux AppImage**: `chmod +x hi-agent-0.2.0-x86_64.AppImage && ./hi-agent-0.2.0-x86_64.AppImage` (no libfuse2 needed; without FUSE use `APPIMAGE_EXTRACT_AND_RUN=1`).
- **Debian/Ubuntu**: `sudo apt install ./hi-agent_0.2.0_amd64.deb`.
- **macOS**: not available yet.

Verify downloads with `SHA256SUMS.txt`. Data stays on your computer (`~/.agent/`); crash reports are off by default and never uploaded. No auto-update yet.
