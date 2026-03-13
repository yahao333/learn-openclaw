# 接入 Telegram

Telegram 是国际常用的通讯平台，接入后可以用 Telegram 控制 AI。

## 前提条件

1. Telegram 账号
2. 创建 Telegram Bot

## 创建 Bot

1. 打开 Telegram
2. 搜索 @BotFather
3. 发送 /newbot
4. 按照提示设置机器人名称和用户名
5. 获取 Bot Token

## 配置步骤

### 1. 修改配置文件

打开 `~/.openclaw/openclaw.json`：

```json
{
  "platforms": {
    "telegram": {
      "enabled": true,
      "bot_token": "${TELEGRAM_BOT_TOKEN}"
    }
  }
}
```

### 2. 设置环境变量

**Windows**（CMD）：
```cmd
set TELEGRAM_BOT_TOKEN=your-bot-token
```

**Mac/Linux**（终端）：
```bash
export TELEGRAM_BOT_TOKEN=your-bot-token
```

## 启动测试

```bash
python main.py
```

在 Telegram 中搜索你的机器人，发送 /start 开始使用。

## 常见问题

### Q: 机器人不回消息？

检查 bot_token 是否正确，网络是否正常。

### Q: 如何开启调试？

```json
{
  "server": {
    "debug": true
  }
}
```

---

**上一章**：[多模型切换](./chapter4-multi-model.md)
**下一章**：[接入飞书](./chapter5-feishu.md)
