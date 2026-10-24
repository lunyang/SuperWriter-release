# SuperWriter

AI 辅助科研写作桌面应用 · AI-assisted research writing desktop app

本仓库是 SuperWriter 的官方安装包发布仓库，只提供安装包、版本说明和更新元数据。应用源码不在本仓库中公开。

This repository distributes SuperWriter installers and release information. Application source code is not published here.

## 下载 / Download

**当前版本：1.3.10 · macOS Apple Silicon（M 系列芯片）**

- [下载 macOS 安装包（约 415 MB）](https://github.com/lunyang/SuperWriter-release/releases/download/v1.3.10/SuperWriter_1.3.10_aarch64.dmg)
- [查看发布说明和全部附件](https://github.com/lunyang/SuperWriter-release/releases/tag/v1.3.10)
- [查看所有版本](https://github.com/lunyang/SuperWriter-release/releases)

本次仅发布 macOS ARM64 版本，不包含 Intel Mac、Windows 或 Linux 安装包。此版本已在构建机器上通过产物检查；不同 macOS 版本的兼容性仍需实际验证。

## 安装 / Installation

1. 下载 `.dmg` 文件并打开。
2. 将 **SuperWriter.app** 拖到“应用程序 / Applications”。
3. 从“应用程序”启动 SuperWriter。

此安装包使用 **ad-hoc 签名，未经过 Apple Developer ID 签名和公证**。首次打开时 macOS 可能阻止运行。请先确认下载来源和校验值，再按照系统“隐私与安全性”中的提示操作；不要全局关闭 Gatekeeper。

The macOS build is ad-hoc signed and is not Apple-notarized. Verify its origin and checksum before following macOS's security prompts.

## 文件说明 / Release assets

| 文件 | 用途 |
| --- | --- |
| `SuperWriter_1.3.10_aarch64.dmg` | 首次安装或手动升级 |
| `SuperWriter.app.tar.gz` | Tauri 自动更新用的应用归档 |
| `SuperWriter.app.tar.gz.sig` | 更新归档的数字签名 |
| `latest.json` | 版本号、更新包地址和签名清单，目前只含 macOS ARM64 |
| `SHA256SUMS.txt` | 发布文件的 SHA-256 校验值 |

下载要校验的文件及 `SHA256SUMS.txt`，在同一目录执行，例如：

```bash
shasum -a 256 SuperWriter_1.3.10_aarch64.dmg
```

将结果与 `SHA256SUMS.txt` 中该文件的记录比较。更新签名不等于 Apple 公证。

## macOS 安装问题 / macOS installation issues

如果 macOS 提示“无法验证开发者”，请先确认下载来源和 SHA-256 校验值，然后右键（或按住 Control 点按）`SuperWriter.app`，选择“打开”，再确认一次。也可以在“系统设置 → 隐私与安全性”中点击“仍要打开”。

如果明确提示“应用已损坏，无法打开”，请先重新下载 DMG，并确认校验值与 `SHA256SUMS.txt` 完全一致。确认无误后，将应用拖到“应用程序”，在终端执行：

```bash
xattr -dr com.apple.quarantine "/Applications/SuperWriter.app"
open "/Applications/SuperWriter.app"
```

这只移除该下载文件的 quarantine 标记，不会关闭 macOS Gatekeeper。不要对 SHA-256 不匹配的文件执行此操作，也不要使用 `sudo spctl --master-disable` 全局关闭安全保护。

如果仍然无法打开，可检查应用签名：

```bash
codesign --verify --deep --strict --verbose=2 \
  "/Applications/SuperWriter.app"
```

如果签名校验失败，请删除应用并从本仓库重新下载；反馈时请提供 macOS 版本、芯片类型和完整错误提示。当前安装包是 Apple Silicon（M 系列）版本。

## 反馈 / Feedback

可在本仓库 [Issues](https://github.com/lunyang/SuperWriter-release/issues) 反馈安装及下载问题。请提供系统版本、芯片类型、应用版本和已去除隐私信息的错误提示。
