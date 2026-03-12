# 环境变量设置

## 为什么要使用环境变量？

环境变量用于存储敏感信息（如 API Key），避免硬编码在配置文件中。

## 创建 .env 文件

在项目根目录创建 `.env` 文件：

```bash
# AI 模型
DASHSCOPE_API_KEY=your-qwen-api-key
OPENAI_API_KEY=your-openai-api-key

# Telegram
TELEGRAM_BOT_TOKEN=your-bot-token
TELEGRAM_API_ID=your-api-id
TELEGRAM_API_HASH=your-api-hash

# 飞书
FEISHU_APP_ID=your-app-id
FELEISHU_APP_SECRET=your-app-secret
FEISHU_VERIFICATION_TOKEN=your-verification-token

# Discord
DISCORD_BOT_TOKEN=your-discord-token
```

## 加载环境变量

### 方式 1：使用 python-dotenv

```python
from dotenv import load_dotenv
load_dotenv()
```

### 方式 2：Docker 环境变量

```yaml
# docker-compose.yml
services:
  openclaw:
    environment:
      - DASHSCOPE_API_KEY=${DASHSCOPE_API_KEY}
      - TELEGRAM_BOT_TOKEN=${TELEGRAM_BOT_TOKEN}
```

## 获取 API Key

### 千问（DashScope）

1. 访问 https://dashscope.console.aliyun.com/
2. 注册/登录账号
3. 创建 API Key

### Telegram Bot

1. 打开 Telegram
2. 搜索 @BotFather
3. 发送 /newbot 创建机器人
4. 获取 Bot Token

### 飞书应用

1. 打开 https://open.feishu.cn/
2. 创建企业应用
3. 获取 App ID 和 App Secret

## 小结

本章学习了如何设置和管理环境变量。正确使用环境变量可以保护你的敏感信息不被泄露。

---

**上一章**：[配置文件详解](./chapter3-configuration.md)
**下一章**：[接入千问模型](./chapter4-qwen.md)
