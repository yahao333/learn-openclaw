# 安装 OpenClaw

😎 这可能是你见过最详细的安装教程，手把手教你！

## 系统要求

| 项目 | 要求 |
|------|------|
| 操作系统 | Windows 10+/Mac/Linux |
| 内存 | 2GB 以上 |
| 硬盘 | 1GB 可用空间 |
| 网络 | 能访问国内网络（阿里云/百度） |

---

## ⭐ 方式一：Windows 一键安装（推荐新手）

### 第一步：安装 Python

1. 打开浏览器，访问：https://www.python.org/downloads/
2. 点击「Download Python 3.11.x」（最新稳定版）
3. 运行下载的安装包

**⚠️ 重要：安装时一定要勾选这个选项！**
```
☑ Add Python 3.x to PATH
```

4. 点击「Install Now」等待安装完成
5. 验证安装：打开 CMD（Win+R 输入 cmd），输入：
   ```
   python --version
   ```
   应该显示 Python 版本号

### 第二步：下载 OpenClaw

**方法 A：直接下载（推荐）**
1. 访问：https://github.com/openclaw/openclaw/archive/refs/heads/main.zip
2. 下载并解压到一个文件夹，比如：`D:\openclaw`

**方法 B：Git 克隆**
```cmd
git clone https://github.com/openclaw/openclaw.git
```

### 第三步：安装依赖

1. 打开 CMD
2. 进入文件夹：
   ```
   cd D:\openclaw
   ```
3. 安装依赖：
   ```
   pip install -r requirements.txt
   ```

### 第四步：首次运行

```
python main.py
```

首次运行会自动创建配置文件，默认位置：
- Windows：`C:\Users\你的用户名\.openclaw\openclaw.json`
- Mac/Linux：`~/.openclaw/openclaw.json`

看到类似这样的输出就成功了：
```
🚀 OpenClaw 启动成功！
📡 服务地址：http://localhost:8080
```

---

## 🍎 方式二：Mac 安装

### 第一步：检查 Python

打开「终端」(Terminal)，输入：
```bash
python3 --version
```

如果没有安装，运行：
```bash
brew install python3
```

### 第二步：克隆项目

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
```

### 第三步：安装依赖

```bash
pip3 install -r requirements.txt
```

### 第四步：启动

```bash
python3 main.py
```

---

## 🐧 方式三：Linux 安装

```bash
# 1. 安装依赖
sudo apt update
sudo apt install python3 python3-pip git

# 2. 克隆项目
git clone https://github.com/openclaw/openclaw.git
cd openclaw

# 3. 安装
pip3 install -r requirements.txt

# 4. 运行
python3 main.py
```

---

## 📁 配置文件说明

首次运行后，配置文件会自动创建在：

| 系统 | 配置文件路径 |
|------|-------------|
| Windows | `C:\Users\你的用户名\.openclaw\openclaw.json` |
| Mac | `~/.openclaw/openclaw.json` |
| Linux | `~/.openclaw/openclaw.json` |

### 配置示例

```json
{
  "ai": {
    "provider": "qwen",
    "model": "qwen-turbo",
    "qwen": {
      "api_key": "your-api-key"
    }
  }
}
```

---

## ⚠️ 常见问题

### Q: pip 不是内部或外部命令？

**原因**：Python 没有添加到 PATH

**解决**：
1. 重新安装 Python，勾选「Add Python to PATH」
2. 或者手动添加到环境变量

### Q: 安装依赖很慢？

**解决**：换国内源
```bash
pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
```

### Q: 打开 CMD 中文乱码？

**解决**：在 CMD 中执行
```cmd
chcp 65001
```

### Q: 端口被占用？

**解决**：修改配置文件中的端口

```json
{
  "server": {
    "port": 8081
  }
}
```

### Q: 配置文件在哪里？

首次运行后自动创建在 `~/.openclaw/openclaw.json`

### Q: 想要后台运行？

**Windows**：使用 `start /b python main.py`

**Linux/Mac**：使用 nohup
```bash
nohup python3 main.py &
```

---

## 下一步

安装成功后，你可以：

- 🎯 直接体验：跳过配置，用默认设置玩一下
- 🤖 配置 AI：接入千问/文心一言
- 📱 连接平台：接入飞书/微信

---

**上一章**：[OpenClaw 能做什么？](./chapter1-applications.md)
**下一章**：[Docker 安装](./chapter2-docker.md)
