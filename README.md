# Hi Agent 下载 · v0.3.2 免费预览版

**Hi Agent** 是一个桌面 AI 助手：日常事务交给「助手」，写代码交给「编程」，还有能常驻干活的机器人团队。它改文件、跑命令、操作电脑之前都会先问你，记得你教过它什么，花多少钱也一清二楚。

> 这是**免费预览版**，**不开源**：这个仓库只放安装包和说明，不含源代码。软件本身免费；可以用 Hi Agent 订阅（邮箱验证码登录），也可以填你自己的模型账号（例如 DeepSeek）。

## 最新版本：v0.3.2（Mac 应用内更新）

- **Mac 版也能在应用内一键更新了**：有新版本时弹出更新提示，点一下就自动下载对应芯片的安装包、校验、替换并重启；新版本启动不起来会自动退回旧版本
- 强制更新的弹窗在 Mac 上也能一键更新
- 如果应用没法替换自己（例如直接从「下载」文件夹或磁盘映像里打开，或者所在文件夹没有写入权限），会改为打开下载页

**Mac 上的 0.3.0 / 0.3.1 用户需要手动下载安装一次 0.3.2**，之后的版本就能在应用内更新了。Windows 和 Linux（AppImage）用户会在应用内收到更新提示。完整说明见 [v0.3.2 发布页](../../releases/tag/v0.3.2)。

上一版 v0.3.1 是安全与修复更新（订阅安全加固、应用里不再显示服务器地址、机器人默认使用订阅模型）。0.3.0 需要更新后才能继续使用订阅。

## 下载

在 [Releases](../../releases/latest) 页面下载对应文件：

| 系统 | 文件 | 大小 |
| --- | --- | --- |
| Windows 10/11（64 位） | `hi-agent-setup-0.3.2-x64.exe` | 126 MB |
| Linux（x86_64，通用） | `hi-agent-0.3.2-x86_64.AppImage` | 129 MB |
| Debian / Ubuntu | `hi-agent_0.3.2_amd64.deb` | 111 MB |
| macOS（Apple 芯片 M1–M4） | `hi-agent-0.3.2-mac-arm64.zip` | 144 MB |
| macOS（Intel） | `hi-agent-0.3.2-mac-x64.zip` | 150 MB |

`SHA256SUMS.txt` 里是每个文件的校验值，可以用来确认下载没有损坏：
- Linux / macOS：`sha256sum -c SHA256SUMS.txt --ignore-missing`（macOS 用 `shasum -a 256 文件名` 对比）
- Windows（PowerShell）：`Get-FileHash .\hi-agent-setup-0.3.2-x64.exe`，和文件里的值对比。

## 安装

### Windows

1. 双击 `hi-agent-setup-0.3.2-x64.exe`。默认只为当前用户安装，可以自选安装目录。
2. 安装包**没有数字签名**，Windows 可能会弹出“**Windows 已保护你的电脑**”（未知发布者）。确认文件是从本仓库 Releases 下载的、校验值也对得上之后，点 **更多信息** → **仍要运行**。
3. 装好后从开始菜单打开 “Hi Agent”。之后有新版本时，应用内会提示一键更新。

### macOS

1. 按芯片下载对应的 zip（苹果菜单 → 关于本机，看“芯片”是 Apple 还是 Intel）。
2. 解压后把 **Hi Agent** 拖进「应用程序」文件夹（升级时覆盖旧版）。
3. 安装包**未经 Apple 公证**：第一次打开请在「应用程序」里**右键 → 打开**，再点“打开”。如果提示“已损坏”，在终端运行 `xattr -dr com.apple.quarantine "/Applications/Hi Agent.app"` 后再打开。
4. 从 0.3.2 起，macOS 版支持应用内更新：有新版本时会提示，一键下载、校验、替换并重启。请把 Hi Agent 放在「应用程序」文件夹里再打开，否则会改为打开下载页。安装包只做了临时签名（不是 Apple 开发者证书），更新后如果系统再次拦截，按上一步右键 → 打开即可。

### Linux（AppImage）

```bash
chmod +x hi-agent-0.3.2-x86_64.AppImage
./hi-agent-0.3.2-x86_64.AppImage
```

不需要安装 libfuse2，Ubuntu 22.04+、Fedora 都能直接运行。如果系统不支持 FUSE（例如某些容器），可以用 `APPIMAGE_EXTRACT_AND_RUN=1 ./hi-agent-0.3.2-x86_64.AppImage`。AppImage 支持应用内更新。

### Debian / Ubuntu（deb）

```bash
sudo apt install ./hi-agent_0.3.2_amd64.deb
```

然后从应用菜单打开 “Hi Agent”。deb 版新版本请回到这里下载覆盖安装。

## 第一次使用

1. 打开后会有 4 步欢迎引导：选语言和主题 → 连接模型（用邮箱登录 Hi Agent 订阅，或填你自己的 API 密钥，也可以先用离线演示模型） → 了解你怎么掌控它 → 数据隐私说明。
2. 「助手」直接用中文说要做什么；「编程」先选一个项目文件夹。它要改文件、跑命令或操作电脑时会先问你。
3. 在“用量”里可以设置每日花费上限。

## 数据和隐私

- 对话、记忆、经验、设置保存在你电脑上的 `~/.agent/` 文件夹；桌面应用数据在 Linux `~/.config/Hi Agent`、Windows `%APPDATA%\Hi Agent`、macOS `~/Library/Application Support/Hi Agent`。
- 崩溃报告只存在本机，不会上传。反馈也是保存成本地文件。
- 你和模型之间的对话内容会发送给你选择的模型服务（Hi Agent 订阅或你自己的模型服务商）。
- 卸载不会删除上面的数据文件夹，想彻底清除请手动删除。

## 已知限制

- 安装包没有签名（Windows 无数字签名，macOS 未公证）。
- deb 版暂不支持应用内更新。macOS 0.3.0 / 0.3.1 需要手动装一次 0.3.2，之后才能应用内更新。
- 预览版功能还会变化，欢迎提 Issue 反馈问题和想法。

---

## English

**Hi Agent** is a desktop AI agent: an Assistant for everyday tasks, a Coding space bound to a project, and a team of bots that keep working. It asks before editing files, running commands or controlling the computer, remembers what you taught it, and shows what you spend.

This is a **free, closed-source preview**: this repo only hosts installers and docs, no source code. Use the Hi Agent subscription (email sign-in) or your own model provider key (e.g. DeepSeek).

**Latest: v0.3.2** — macOS now gets one-click in-app updates (download for your CPU, verify, swap in place, restart, automatic rollback if the new version fails to start; ad-hoc signed). **Mac users on 0.3.0/0.3.1 must install 0.3.2 manually once**; after that updates arrive in-app. v0.3.1 was the security & fix update; **0.3.0 users must update** to keep using the subscription.

**Install**
- **Windows**: run `hi-agent-setup-0.3.2-x64.exe`. It is unsigned, so SmartScreen may say "Windows protected your PC". If you downloaded it from this repo and the SHA256 matches, click **More info → Run anyway**. Updates arrive in-app.
- **macOS**: download the arm64 (Apple silicon) or x64 (Intel) zip, unzip, drag **Hi Agent** to Applications, then right-click → **Open** the first time (not notarized). If macOS says it is damaged, run `xattr -dr com.apple.quarantine "/Applications/Hi Agent.app"`. From 0.3.2 on, updates arrive in-app (keep the app in Applications).
- **Linux AppImage**: `chmod +x hi-agent-0.3.2-x86_64.AppImage && ./hi-agent-0.3.2-x86_64.AppImage` (no libfuse2 needed; without FUSE use `APPIMAGE_EXTRACT_AND_RUN=1`). Updates arrive in-app.
- **Debian/Ubuntu**: `sudo apt install ./hi-agent_0.3.2_amd64.deb`.

Verify downloads with `SHA256SUMS.txt`. Data stays on your computer (`~/.agent/`); crash reports are never uploaded.
