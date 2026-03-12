# 接入飞书

飞书是字节跳动推出的企业协作平台，OpenClaw 支持接入飞书机器人。

## 前提条件

1. 飞书账号
2. 创建飞书企业应用：https://open.feishu.cn/

## 配置步骤

### 1. 创建飞书应用

1. 打开飞书开放平台
2. 创建企业应用
3. 添加机器人能力
4. 获取 App ID 和 App Secret

### 2. 配置 config.yaml

```yaml
platforms:
  feishu:
    enabled: true
    app_id: "${FEISHU_APP_ID}"
    app_secret: "${FEISHU_APP_SECRET}"
    verification_token: "${FEISHU_VERIFICATION_TOKEN}"
```

### 3. 设置环境变量

```bash
export FEISHU_APP_ID="your-app-id"
export FEISHU_APP_SECRET="your-app-secret"
export FEISHU_VERIFICATION_TOKEN="your-verification-token"
```

### 4. 配置事件订阅

在飞书开放平台配置事件订阅：
- `im.message.message_created_v1` - 消息接收

## 启动

```bash
python main.py
```

## 常见问题

### Q1：消息收不到？

检查是否正确配置了事件订阅和回调地址。

### Q2：验证失败？

确认 verification_token 与飞书配置一致。

---

**上一章**：[接入 Telegram](./chapter5-telegram.md)
**下一章**：[接入 Discord](./chapter5-discord.md)
