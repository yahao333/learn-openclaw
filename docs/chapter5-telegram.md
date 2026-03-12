# 接入 Telegram

Telegram 是最常用的 OpenClaw 接入平台之一。

## 前提条件

1. Telegram 账号
2. 创建 Telegram Bot（见上一章）

## 配置步骤

### 1. 配置 config.yaml

```yaml
platforms:
  telegram:
    enabled: true
    bot_token: "${TELEGRAM_BOT_TOKEN}"
    # 可选配置
    api_id: "${TELEGRAM_API_ID}"
    api_hash: "${TELEGRAM_API_HASH}"
    allowed_users:
      - "user_id_1"
      - "user_id_2"
```

### 2. 设置环境变量

```bash
export TELEGRAM_BOT_TOKEN="your-bot-token"
export TELEGRAM_API_ID="your-api-id"
export TELEGRAM_API_HASH="your-api-hash"
```

### 3. 启动

```bash
python main.py
```

### 4. 绑定 Bot

1. 在 Telegram 中搜索你的 Bot 用户名
2. 发送 `/start` 开始对话
3. 根据配置，可能需要验证用户

## 功能测试

发送消息给 Bot 测试：
- 发送 "你好"
- 发送 "帮我查一下天气"

## 高级配置

### 用户白名单

```yaml
platforms:
  telegram:
    allowed_users:
      - 123456789  # 用户 ID
```

### 自动回复

```yaml
platforms:
  telegram:
    auto_reply: true
    reply_keywords:
      - "hello"
      - "help"
```

---

**上一章**：[多模型切换](./chapter4-multi-model.md)
**下一章**：[接入飞书](./chapter5-feishu.md)
