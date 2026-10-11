# 关于本仓库 / About this repository

> 最后更新：2026-10-11（仓库重命名与远端配置调整后）

## 本仓库 / This repository

- **仓库名**：`Wraindrock/Ian-g-control-center`
  （2026-10-11 由 `Wraindrock/g15-control-center` 重命名而来，GitHub 会自动重定向旧地址；
  GitHub 账号 `Wraindrock` 由早先的 `Grant-Felix` 更名而来，数字 ID 同为 `297345894`，
  因此历史提交中的 `Grant-Felix+297345894@users.noreply.github.com` 仍归属本账号。）
- **上游（upstream）**：**[AndersonDinizDev/g15-control-center](https://github.com/AndersonDinizDev/g15-control-center)**
  —— 面向 Linux 的 Dell G15 原生控制中心（葡萄牙语项目，MIT License）。
- **Fork 关系**：本仓库是通过 GitHub fork 功能建立的原生 fork（`isFork = true`），
  网页上会显示 "forked from AndersonDinizDev/g15-control-center"。

原作者的 **22 个提交与 `v1.0.0` / `v1.0.1` / `v1.0.2` 标签完整保留**在本仓库历史中。
本仓库的改动是在 `0cd889c docs: ajuste na documentacao` 之上叠加的 **6 个提交**：

| 提交 | 说明 |
|---|---|
| `831057e` | 界面汉化 + 暗色/浅色主题 + 只读降级模式 |
| `d39027f` | 新增 FORK.md 说明上游 fork 关系与同步方式 |
| `1db4d87` | 安装脚本指向新仓库并增强健壮性 |
| `751aa43` | 修正安装脚本重复 main 定义 + 增强容器环境健壮性（distrobox 实测） |
| `fdcf365` | 支持一条命令在线安装/卸载（curl \| sudo bash） |
| `bafa5a7` | 补齐 MIT LICENSE（内容与上游 `3cb4170` 逐字节一致） |

所有原始代码的版权与署名归原作者 **Anderson Diniz** 所有（MIT License）。

## 本仓库的改动

| 方面 | 说明 |
|---|---|
| 界面汉化 | 窗口、卡片、标签页、按钮、状态标签、托盘菜单、全部弹窗改为简体中文 |
| 终端与桌面项 | `install.sh` / `uninstall.sh` 提示汉化；`.desktop` 增加 `[zh_CN]` 字段 |
| 暗色/浅色主题 | 新增 `src/g15_theme.py` 集中调色板，默认暗色，可切换并持久化 |
| 只读降级模式 | daemon 未运行时直读 `hwmon`，仍可查看温度/转速，写控件自动禁用 |
| 中文文档 | 新增 [README.zh_CN.md](README.zh_CN.md) |
| MIT 协议 | 补齐 `LICENSE`（与上游正文一致） |

## 远端配置

本仓库已按以下约定配置远端：

- `origin` → `https://github.com/Wraindrock/Ian-g-control-center.git`（新仓库，日常开发主线）
- `upstream` → `https://github.com/AndersonDinizDev/g15-control-center.git`
- `ian-awcc-bazzite` → `https://github.com/Wraindrock/ian-awcc-bazzite.git`（早期独立仓库，仅作备份/对照）

## 与上游同步

```bash
git fetch upstream
git merge upstream/main
```

> 截至 2026-10-11，上游 `main` 已到 `14ceaca`，比本仓库的分叉点 `0cd889c` **领先 2 个提交**
> （`3cb4170 chore: adicionando licenca MIT` 与其合并提交 `14ceaca`）。
> 该提交新增的 `LICENSE` 与本仓库的 `LICENSE` **内容完全一致**，因此合并时不会产生冲突。
> 下次同步上游时直接 `git merge upstream/main` 即可。

## 相关仓库

- [`Wraindrock/ian-awcc-bazzite`](https://github.com/Wraindrock/ian-awcc-bazzite) ——
  文字内容与历次改动相同的**早期独立仓库**（`gh repo create --source=.` 创建，`isFork = false`，
  没有 GitHub 原生的 fork 关联标识）。其代码与本仓库同源，但缺少 LICENSE 提交，
  且不再作为开发主线；日常开发与安装脚本一律以本仓库 `Ian-g-control-center` 为准。

## 为什么改用原生 fork？

早期为避免受 fork 限制（例如 fork 默认不能改可见性、不便独立发版），
项目曾以 `gh repo create --source=.` **独立创建** `ian-awcc-bazzite`，代价是
GitHub 上不显示 "forked from ..." 横幅，上游关联只能靠 description / homepage / 文档说明。

本仓库直接使用 GitHub 原生 fork，此后：

1. 网页上可直观看到上游来源，贡献与同步关系清晰；
2. `git fetch upstream && git merge upstream/main` 的同步路径与 GitHub 的 fork 语义一致；
3. 安装脚本、`pyproject.toml`、两份 README 中的仓库地址已统一指向本仓库。
