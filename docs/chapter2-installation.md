# 安装 OpenClaw

⭐ **只需 3 步，小白也能学会！**

---

## 第一步：安装 Python

> 如果你电脑已经安装了 Python，跳过这步！

### Windows

1. 下载 Python：https://www.python.org/downloads/
2. 运行安装包
3. **一定要勾选** `☑ Add Python to PATH`
4. 点「Install Now」完成

### Mac

通常已经预装了，打开「终端」输入 `python3 --version` 确认一下

### Linux

```bash
sudo apt install python3 python3-pip
```

---

## 第二步：下载 OpenClaw

### 方法 A：直接下载（推荐）

1. 打开：https://github.com/openclaw/openclaw/archive/refs/heads/main.zip
2. 解压到一个文件夹，比如：`D:\openclaw`

### 方法 B：用 Git（需要安装 Git）

```bash
git clone https://github.com/openclaw/openclaw.git
```

---

## 第三步：运行！

```bash
# 进入文件夹
cd openclaw

# 运行！
python main.py
```

> 首次运行会自动创建配置文件

看到下面这些就是成功了 🎉

```
🚀 OpenClaw 启动成功！
📡 服务地址：http://localhost:8080
```

---

## 配置文件在哪？

首次运行后会自动创建：
- Windows：`C:\Users\你的用户名\.openclaw\openclaw.json`
- Mac/Linux：`~/.openclaw/openclaw.json`

---

## ⚠️ 常见问题

### 💥 运行报错"pip 不是内部命令"

重新安装 Python，**一定要勾选 Add to PATH**

### 🐢 安装很慢

```bash
pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
```

### 📝 中文乱码

在 CMD 运行：`chcp 65001`

---

## 下一步

配置 AI 模型，开始使用！

- [接入千问模型](./chapter4-qwen.md)
- [接入飞书](./chapter5-feishu.md)
