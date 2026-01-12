---

# ✨ T-Header: Termux 高级终端美化工具

---

使用 **T-Header** 将您的 Termux shell 转换为个性化的、美观的命令中心 —— 一个包含自定义标题、ZSH 主题、ASCII 艺术标志和交互式菜单的模块化设置。

[English Version](README_EN.md)

## 🚀 特性

- 🎨 **自定义标志和标题**: 显示 ASCII 艺术标志和 figlet 渲染的标题,支持颜色渐变。
- 🧠 **智能 ZSH 设置**: 集成 Oh-My-Zsh,提供插件管理器和主题选择器。
- 🧩 **交互式菜单**: 使用 `fzf` 和 `gum` 提供直观的选择界面。
- 🛠️ **一键安装**: 几分钟内安装所有依赖项并配置您的 shell。
- 🧾 **别名和增强**: 使用 `eza`、`bat`、`logo-ls` 等工具替换传统的 `ls`、`cat` 命令。

## 安装完成后的预览
![项目横幅](doc/theader.jpg)

---

## 📦 系统要求

确保已安装以下软件包:

```bash
pkg install curl fd figlet ruby boxes gum bat logo-ls eza zsh timg fzf
gem install lolcat
```

## 🧑‍💻 安装步骤

1. `apt update && yes | apt upgrade && apt update && apt install git fzf -y`
2. `git clone https://github.com/remo7777/T-Header.git`
3. `cd T-Header/`
4. `ls`
5. `bash t-header.sh`
6. 完成所有处理后,只需 --打开新会话-- 或运行 `source ~/.zshrc`

此脚本将:

- 安装所需的软件包
- 设置 ZSH 和 Oh-My-Zsh
- 应用自定义字体和主题
- 配置 `.zshrc`、`.profile` 和 `.aliases`

## 🛠️ 故障排除

**Termux 强制关闭问题**  
如果在安装 T-Header 后遇到 Termux 强制关闭的问题:

> 🔧 **修复方法**:  
导航到项目根目录并运行:
```bash
git pull
bash t-header.sh
```
这将更新文件并重新运行安装程序,以解决任何兼容性问题。

## 🧭 使用方法

安装完成后,使用以下命令:

| 命令      | 描述                      |
|----------|--------------------------|
| `theader` | 启动交互式设置            |
| `clogo`   | 更改标志                  |
| `ctitle`  | 设置自定义标题            |
| `ctpro`   | 切换 `termux.properties`  |
| `cztheme` | 更改 ZSH 主题             |

## 🖼️ 预览

```bash
figlet -f pixelfont "T-Header" | lolcat
```

![演示预览](https://user-images.githubusercontent.com/demo-placeholder.png) <!-- 如有实际截图请替换 -->

## 🧙‍♂️ 自定义

- 标志存储在 `~/.config/theader/logo`
- 主题在 `~/.oh-my-zsh/custom/themes`
- 配置文件: `~/.config/theader/theader.cfg`

您可以手动编辑这些文件,或使用交互式菜单。

### 快捷键 (ZSH)
- `Alt+T`: 插入文件路径
- `Alt+C`: 更改目录
- `Ctrl+R`: 搜索历史记录

## 🧼 卸载

```bash
rm -rf ~/.config/theader ~/.oh-my-zsh ~/.zshrc ~/.profile ~/.aliases
```

## 📜 许可证

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## T-Header Wiki

[![Wiki](https://img.shields.io/badge/wiki-home-green.svg)](https://github.com/remo7777/T-Header/wiki)

---