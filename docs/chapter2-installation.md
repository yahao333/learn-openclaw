# 安装 OpenCLAW

## 系统要求

在安装 OpenCLAW 之前，请确保你的计算机满足以下要求：

- **操作系统**：Windows、macOS 或 Linux
- **内存**：至少 2GB RAM
- **磁盘空间**：至少 500MB 可用空间
- **网络**：用于下载依赖包

## 安装方式

### 方式一：使用安装包（推荐）

#### Windows

1. 访问 [OpenCLAW 官网](https://openclaw.example.com) 下载安装包
2. 双击运行 `openclaw-x.x.x-setup.exe`
3. 按照安装向导完成安装
4. 打开命令提示符，输入 `claw --version`，如果显示版本号则安装成功

#### macOS

```bash
# 使用 Homebrew 安装
brew install openclaw

# 验证安装
claw --version
```

#### Linux

```bash
# Debian/Ubuntu
sudo apt-get install openclaw

# 或者使用 snap
sudo snap install openclaw

# 验证安装
claw --version
```

### 方式二：手动安装

如果你无法使用包管理器，可以手动下载预编译的二进制文件：

1. 从 GitHub releases 页面下载对应平台的压缩包
2. 解压到任意目录
3. 将解压后的目录添加到系统 PATH 环境变量

#### Windows 示例

```powershell
# 下载并解压
Invoke-WebRequest -Uri "https://github.com/openclaw/openclaw/releases/latest/download/openclaw-windows-x64.zip" -OutFile openclaw.zip
Expand-Archive -Path openclaw.zip -DestinationPath C:\OpenCLAW

# 添加到 PATH
$env:PATH += ";C:\OpenCLAW\bin"

# 验证
claw --version
```

#### macOS / Linux 示例

```bash
# 下载并解压
wget https://github.com/openclaw/openclaw/releases/latest/download/openclaw-linux-x64.tar.gz
tar -xzf openclaw-linux-x64.tar.gz
sudo mv openclaw /usr/local/

# 添加到 PATH（添加到 ~/.bashrc 或 ~/.zshrc）
export PATH=$PATH:/usr/local/openclaw/bin

# 验证
claw --version
```

### 方式三：从源码编译

如果你想使用最新功能，可以从源码编译：

```bash
# 克隆仓库
git clone https://github.com/openclaw/openclaw.git
cd openclaw

# 安装依赖
make deps

# 编译
make build

# 安装
sudo make install

# 验证
claw --version
```

## 常见问题

### Q1：安装后无法运行？

**解决方法**：
1. 检查是否正确添加到 PATH
2. 重新打开终端
3. 尝试使用完整路径运行：`/usr/local/bin/claw --version`

### Q2：权限不足？

**解决方法**：
- Linux/macOS：使用 `sudo` 提权
- Windows：以管理员身份运行

### Q3：版本不兼容？

**解决方法**：
确保你的操作系统版本在支持列表内。如果遇到兼容性问题，可以尝试使用 Docker 运行。

## 验证安装

安装完成后，打开终端运行以下命令验证：

```bash
claw --version
```

如果成功，应该看到类似输出：

```
OpenCLAW version 1.0.0
License: MIT
Home: https://github.com/openclaw/openclaw
```

## 配置镜像源（可选）

如果在国内访问官方源较慢，可以配置国内镜像：

```bash
claw config set mirror https://mirror.example.com/openclaw
```

## 小结

本章我们学习了 OpenCLAW 的多种安装方式。在下一章中，我们将学习如何配置开发环境，以便更好地开始编程。

---

**上一章**：[什么是 OpenCLAW？](./chapter1-what-is-openclaw.md)
**下一章**：[配置开发环境](./chapter2-setup.md)
