# 接入钉钉

钉钉是阿里巴巴推出的企业通讯工具，接入简单稳定。

## 前提条件

1. 钉钉账号
2. 创建一个钉钉企业（如没有可以用个人账号测试）

## 配置步骤

### 1. 创建钉钉机器人

1. 打开钉钉电脑版
2. 进入群聊 → 设置 → 智能群助手 → 添加机器人
3. 选择「自定义机器人」
4. 填写机器人名称，获取 Webhook 地址

### 2. 获取安全设置

钉钉提供三种安全验证方式：
- **自定义关键词**：添加一个关键词，消息必须包含该词
- **加签**：使用签名验证
- **IP地址**：限制访问 IP

推荐使用**自定义关键词**，最简单。

### 3. 配置 config.yaml

```yaml
platforms:
  dingtalk:
    enabled: true
    webhook: "${DINGTALK_WEBHOOK}"
    secret: "${DINGTALK_SECRET}"  # 如果启用加签
```

### 4. 设置环境变量

```bash
# Windows
set DINGTALK_WEBHOOK=https://oapi.dingtalk.com/robot/send?access_token=xxx
set DINGTALK_SECRET=xxx

# Mac/Linux
export DINGTALK_WEBHOOK=https://oapi.dingtalk.com/robot/send?access_token=xxx
export DINGTALK_SECRET=xxx
```

## 高级配置

### 接收消息（需要开发者后台）

1. 访问 https://open-dev.dingtalk.com/
2. 创建应用，获取 AppKey 和 AppSecret
3. 配置回调地址

```yaml
platforms:
  dingtalk:
    enabled: true
    app_key: "${DINGTALK_APP_KEY}"
    app_secret: "${DINGTALK_APP_SECRET}"
    callback_url: "https://your-domain.com/dingtalk/callback"
```

## 测试

1. 启动 OpenClaw
2. 在钉钉群发送消息
3. 机器人应该能自动回复

## 常见问题

### Q: 机器人不发消息？

检查 Webhook 地址是否正确，确保群成员数足够。

### Q: 关键词验证失败？

确保消息包含你设置的关键词。

### Q: 加签失败？

检查密钥是否正确，注意加签计算的时区问题。

---

**上一章**：[接入微信](./chapter5-wechat.md)
**下一章**：[接入 Telegram](./chapter5-telegram.md)
