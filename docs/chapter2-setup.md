# 配置开发环境

## 选择代码编辑器

好的开发环境可以大大提高编码效率。以下是几个常用的代码编辑器推荐：

### 1. VS Code（推荐）

Visual Studio Code 是免费开源的代码编辑器，跨平台支持，有丰富的插件生态。

**安装步骤**：

1. 访问 [VS Code 官网](https://code.visualstudio.com/) 下载安装
2. 打开 VS Code
3. 按 `Ctrl + P`（Windows/Linux）或 `Cmd + P`（macOS）打开命令面板
4. 输入 `ext install openclaw.openclaw-lang` 安装 OpenCLAW 插件

**插件功能**：
- 语法高亮
- 代码补全
- 错误提示
- 代码格式化

### 2. Sublime Text

轻量级编辑器，打开速度快。

**安装 OpenCLAW 包**：

1. 按 `Ctrl + Shift + P` 打开命令面板
2. 输入 `Package Control: Install Package`
3. 搜索 `OpenCLAW` 并安装

### 3. Vim / Neovim

适合习惯使用终端的开发者。

在 `.vimrc` 中添加：

```vim
" OpenCLAW 语法高亮
au BufNewFile,BufRead *.claw set filetype=claw
```

## 安装 OpenCLAW SDK

OpenCLAW SDK 包含了开发所需的所有工具和库。

```bash
# 安装 SDK
claw sdk install

# 或者指定版本
claw sdk install 1.0.0
```

验证 SDK 安装：

```bash
claw sdk list
```

应该看到类似输出：

```
Installed packages:
- openclaw/std: 1.0.0
- openclaw/http: 1.0.0
- openclaw/json: 1.0.0
- openclaw/fs: 1.0.0
```

## 创建项目

使用命令行工具创建新项目：

```bash
# 创建新项目
claw new my-project

# 进入项目目录
cd my-project
```

项目结构如下：

```
my-project/
├── src/
│   └── main.claw      # 主程序文件
├── tests/             # 测试文件
├── config.json        # 项目配置
└── README.md          # 项目说明
```

## 配置项目

编辑 `config.json` 文件：

```json
{
    "name": "my-project",
    "version": "1.0.0",
    "main": "src/main.claw",
    "dependencies": {
        "http": "^1.0.0",
        "json": "^1.0.0"
    },
    "scripts": {
        "start": "claw run src/main.claw",
        "test": "claw test"
    }
}
```

## 运行程序

### 方式一：使用命令行

```bash
claw run src/main.claw
```

### 方式二：使用 npm 脚本

```bash
npm start
```

### 方式三：使用调试模式

```bash
claw run --debug src/main.claw
```

## 配置代理（可选）

如果需要通过代理访问网络：

```bash
claw config set proxy http://proxy.example.com:8080
```

## IDE 集成配置

### VS Code 配置

创建 `.vscode/settings.json`：

```json
{
    "openclaw.languageServer": {
        "enable": true,
        "trace": false
    },
    "editor.formatOnSave": true,
    "editor.tabSize": 4
}
```

### 使用 Debugger

在 VS Code 中添加调试配置 `.vscode/launch.json`：

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "OpenCLAW Debug",
            "type": "openclaw",
            "request": "launch",
            "program": "${workspaceFolder}/src/main.claw",
            "stopOnEntry": true
        }
    ]
}
```

## 小结

本章我们学习了如何配置 OpenCLAW 开发环境，包括选择代码编辑器、安装 SDK、创建项目和运行程序。现在你已经准备好开始编写 OpenCLAW 代码了！

在下一章中，我们将学习如何运行第一个 OpenCLAW 程序。

---

**上一章**：[安装 OpenCLAW](./chapter2-installation.md)
**下一章**：[运行第一个程序](./chapter2-hello-world.md)
