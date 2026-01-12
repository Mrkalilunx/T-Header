# T-Header 项目文档

## 项目概述

**T-Header** 是一个专为 Android Termux 终端设计的模块化美化和自定义工具。它通过提供 ASCII 艺术标志、自定义标题、ZSH 主题、交互式菜单等功能,将 Termux shell 转换为个性化的命令中心。

### 核心特性

- 🎨 **自定义标志和标题**: 使用 ASCII 艺术标志和 figlet 渲染的标题,支持颜色渐变
- 🧠 **智能 ZSH 设置**: 集成 Oh-My-Zsh,提供插件管理器和主题选择器
- 🧩 **交互式菜单**: 使用 `fzf` 和 `gum` 提供直观的选择界面
- 🛠️ **一键安装**: 几分钟内安装所有依赖项并配置 shell
- 🧾 **别名和增强**: 使用 `eza`、`bat`、`logo-ls` 等工具替换传统的 `ls`、`cat` 命令

### 技术栈

- **Shell**: Bash (主脚本), Zsh (目标 shell)
- **依赖工具**:
  - `fzf` - 模糊查找器,用于交互式菜单
  - `gum` - 美化命令行界面
  - `figlet` - ASCII 艺术字体生成
  - `lolcat` - 颜色渐变效果
  - `boxes` - 文本框架装饰
  - `bat` - 增强的 cat 命令
  - `eza` - 增强的 ls 命令
  - `logo-ls` - 带图标的 ls 命令
  - Oh-My-Zsh - Zsh 框架

### 项目结构

```
T-Header/
├── bin/                    # 可执行文件
│   └── theader            # 主命令行工具
├── lib/                    # 库文件
│   ├── pbanner            # 横幅显示功能
│   ├── progress           # 进度显示功能
│   ├── fmenu              # 交互式菜单功能
│   └── confzsh            # ZSH 配置和插件管理
├── dotfile/               # 配置文件模板
│   ├── .aliases           # 别名配置
│   ├── .profile           # 环境变量配置
│   ├── bash/              # Bash 配置
│   └── fish/              # Fish shell 配置
├── logo/                  # ASCII 艺术标志库
├── tpt/                   # Termux 属性配置文件
├── colors.properties      # 颜色主题配置
├── theader.cfg            # T-Header 配置文件
├── t-header.sh            # 主安装脚本
└── README.md              # 项目说明文档
```

## 构建和运行

### 系统要求

- Android Termux 环境
- 包管理器支持: `pkg` (Termux 包管理器)
- 网络连接(用于下载依赖项)

### 安装步骤

1. **更新系统并安装基础工具**:
   ```bash
   apt update && yes | apt upgrade && apt install git fzf -y
   ```

2. **克隆仓库**:
   ```bash
   git clone https://github.com/remo7777/T-Header.git
   cd T-Header/
   ```

3. **运行安装脚本**:
   ```bash
   bash t-header.sh
   ```

4. **应用更改**:
   - 打开新的 Termux 会话
   - 或运行: `source ~/.zshrc`

### 手动安装依赖项

如果需要手动安装依赖项:

```bash
pkg install curl fd figlet ruby boxes gum bat logo-ls eza zsh timg fzf
gem install lolcat
```

### 使用命令

安装完成后,可以使用以下命令:

| 命令 | 描述 |
|------|------|
| `theader` | 启动交互式设置菜单 |
| `clogo` | 更改标志 |
| `ctitle` | 设置自定义标题 |
| `ctpro` | 切换 termux.properties |
| `cztheme` | 更改 ZSH 主题 |

### 卸载

```bash
rm -rf ~/.config/theader ~/.oh-my-zsh ~/.zshrc ~/.profile ~/.aliases
```

## 开发约定

### 代码风格

- **Shell 脚本**: 使用 Bash (#!/usr/bin/env bash 或 #!/usr/bin/bash)
- **函数命名**: 使用小写字母和下划线 (如 `install_oh_my_zsh`, `fzf_add_plugin`)
- **变量命名**: 使用大写字母表示常量,小写表示局部变量
- **注释**: 使用 `#` 注释,复杂逻辑添加说明

### 文件组织

- **库文件**: 所有可重用函数放在 `lib/` 目录下
- **配置文件**: 模板放在 `dotfile/` 目录
- **资源文件**: ASCII 艺术标志放在 `logo/` 目录
- **配置**: 用户配置存储在 `~/.config/theader/`

### 配置管理

- 主配置文件: `~/.config/theader/theader.cfg`
- 配置格式: INI 风格 (键值对)
- 使用 `grep` 和 `sed` 进行配置读写

### 主题系统

- ZSH 主题位置: `~/.oh-my-zsh/custom/themes/`
- 自定义主题: `theader.zsh-theme`
- 主题配置通过 `ZSH_THEME` 变量控制

### 插件管理

- Oh-My-Zsh 插件存储在 `~/.oh-my-zsh/plugins/`
- 自定义插件存储在 `~/.oh-my-zsh/custom/plugins/`
- 插件通过 `plugins=` 数组在 `.zshrc` 中配置

### 错误处理

- 使用 `set -Eeuo pipefail` 进行严格的错误处理
- 关键操作前检查依赖项和文件存在性
- 使用 `exit 1` 在错误时退出

### 用户交互

- 使用 `fzf` 进行交互式选择
- 使用 `gum` 提供美观的菜单界面
- 支持命令行参数和交互式菜单两种方式

### 颜色和样式

- 使用 ANSI 转义码进行颜色输出
- 从 `~/.termux/colors.properties` 读取主题颜色
- 支持颜色渐变 (通过 `lolcat`)

### Git 工作流

- 主分支: `master`
- 提交信息风格: 简洁明了,描述更改内容
- 版本控制: 使用 Git 进行版本管理

## 故障排除

### Termux 强制关闭问题

如果安装 T-Header 后 Termux 强制关闭:

```bash
cd T-Header/
git pull
bash t-header.sh
```

### 依赖项检查

确保所有必需的包已安装:

```bash
pkg install curl fd figlet ruby boxes gum bat logo-ls eza zsh timg fzf
gem install lolcat
```

### 包数量检查

脚本会检查包数量是否大于 2000,如果不是,会提示更新或更换仓库:

```bash
pkg update && pkg upgrade
```

### fzf 命令未找到

如果提示 `fzf` 命令未找到:

```bash
pkg install fzf -y
```

## 许可证

本项目采用 MIT 许可证。详见 [LICENSE](LICENSE) 文件。

## 贡献

项目由 @Remo773 创建和维护。欢迎贡献和改进建议。

## 相关资源

- [GitHub 仓库](https://github.com/remo7777/T-Header)
- [Wiki 文档](https://github.com/remo7777/T-Header/wiki)