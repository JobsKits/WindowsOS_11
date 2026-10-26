# WindowsOS_11

![Jobs出品，必属精品](https://picsum.photos/1500/400)

---

## 🔥 <span id="前言">前言</span>

Jobs 维护的 Windows 11 镜像资料子仓。父仓 [WindowsOS](../README.md) 通过 [**Git 子模块**](https://git-scm.com/book/en/v2/Git-Tools-Submodules)管理关联与按需下载，本仓保持独立历史和 `main` 分支。镜像、分卷及工具由 [**GitHub Releases**](https://github.com/JobsKits/WindowsOS_11/releases)提供，Git 克隆只取得已提交文件。

## 一、目录与下载 <a href="#前言" style="font-size:17px; color:green;"><b>🔼</b></a> <a href="#🔚" style="font-size:17px; color:green;"><b>🔽</b></a>

| 路径 | 职责 |
| --- | --- |
| `README.md`、`LICENSE` | 仓库说明与许可证文件。 |
| `Releases/<标签>/` | 父仓下载入口确认后生成的附件目录，通过本仓本地 Git 排除规则忽略。 |
| `Windows11_Client_arm64_zh-cn_26300_9457.iso`、同名分卷目录 | 当前本地发布源文件，未纳入 Git 跟踪；附件在 Release 中提供。 |
| `merge.command`、`split.command` | 当前本地分卷工具原件，同时作为 Release 附件提供；下载后不会自动执行。 |

[Windows 11 ARM64 简体中文 26300.9457](https://github.com/JobsKits/WindowsOS_11/releases/tag/Windows11_Client_arm64_zh-cn_26300_9457) 包含 169 个镜像分卷和两个脚本。通过父仓[克隆与下载入口](../【MacOS】⬆️克隆WindowsOS子仓.command)选择 `WindowsOS_11`；已有子仓时可直接使用 [Release 下载入口](<../【MacOS】⏬按需下载WindowsOS Release.command>)。附件下载与 Git 同步分别选择。

## 二、分卷工具 <a href="#前言" style="font-size:17px; color:green;"><b>🔼</b></a> <a href="#🔚" style="font-size:17px; color:green;"><b>🔽</b></a>

两个脚本在 macOS 终端交互运行，依赖本机已有的 [**fzf**](https://github.com/junegunn/fzf) 和系统命令，只检查依赖，不自动安装或升级。

### [merge.command](./merge.command)

> **目的：** 将同组分卷按数字顺序还原成完整文件。

- 下载全部分卷与脚本到同一目录，在该目录运行 `/bin/zsh ./merge.command`，阅读自述后回车。
- 目标目录回车默认使用脚本目录；选择镜像组时回车勾选、空格确认。
- 校验卷号完整性后在所选目标目录输出 ISO；同名文件拒绝覆盖，完成后回车保留分卷，仅精确输入 `YES` 才删除分卷。

### [split.command](./split.command)

> **目的：** 按上限重新拆分大文件；还原镜像无需运行它。

- 阅读自述后选择目录、分卷上限和文件；支持 50 MiB、100 MiB、1900 MiB 及自定义 MiB。
- 生成分卷并完成大小和 SHA-256 校验后发布到新目录，已有同名目录拒绝覆盖。
- 默认保留源文件，仅精确输入 `YES` 才删除；日志位于系统临时目录中的 `split.log`，合并日志为同目录中的 `merge.log`。

完整 ISO 为 8,852,006,912 字节，SHA-256：

```text
cd573df724862300895d0f5d0836e663756d22cc4e964c752efdc05b4fc09e8b
```

工具原件位于本地仓根；从 Release 取得的副本位于所选下载目录。下载附件不会自动合并、挂载或安装系统。

<a id="🔚" href="#前言" style="font-size:17px; color:green; font-weight:bold;">我是有底线的➤点我回到首页</a>
