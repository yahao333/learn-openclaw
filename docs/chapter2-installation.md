# 安装 OpenClaw

⭐ **只需 2 步，小白也能学会！**

---

## 第一步：安装 Node.js

> 如果你电脑已经安装了 Node.js，跳过这步！

### Windows / Mac

1. 下载 Node.js：https://nodejs.org/
2. 运行安装包，完成！

### Mac（用终端）

```bash
brew install node
```

### Linux

```bash
# Ubuntu/Debian
sudo apt update
sudo apt install nodejs npm
```

---

## 第二步：安装 OpenClaw

```bash
npm install -g openclaw
```

---

## 运行！

```bash
openclaw
```

首次运行会显示配置文件位置：

```
配置文件位置：~/openclaw/openclaw.json
```

---

## ⚠️ 常见问题

### 💥 报错"npm 不是内部命令"

重新安装 Node.js

### 💥 报错"权限被拒绝"

```bash
# Mac/Linux
sudo npm install -g openclaw
```

---

## 下一步

配置 AI 模型，开始使用！

- [接入千问模型](./chapter4-qwen.md)
- [接入飞书](./chapter5-feishu.md)
