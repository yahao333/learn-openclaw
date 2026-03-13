# 接入微信

微信是国内最常用的通讯工具，接入微信后可以直接用微信控制 AI 助手。

> ⚠️ **重要提示**：微信对机器人限制比较严，推荐使用**企业微信**或**微信机器人框架**（如 Wechaty）

## 方案选择

### 方案一：企业微信（推荐）

企业微信对机器人更友好，接入更稳定。

#### 1. 创建企业微信应用

1. 访问 https://work.weixin.qq.com/
2. 注册企业微信
3. 进入「应用管理」→「创建应用」
4. 获取 AgentId 和 Secret

#### 2. 配置 config.yaml

```yaml
platforms:
  wecom:
    enabled: true
    corp_id: "${WECOM_CORP_ID}"
    agent_id: "${WECOM_AGENT_ID}"
    secret: "${WECOM_SECRET}"
```

#### 3. 设置回调

在企业微信应用设置中：
- 填写服务器接收消息的 URL：`你的服务器地址/wecom/callback`
- 接收消息类型：文字、图片、事件

### 方案二：使用 Wechaty

Wechaty 是一个开源的微信机器人框架。

#### 1. 安装

```bash
npm install wechaty
```

#### 2. 配置

```yaml
platforms:
  wechat:
    enabled: true
    puppeteer: true
```

#### 3. 运行

```bash
python main.py
```

用微信扫码登录即可。

## 环境变量

```bash
# 企业微信
export WECOM_CORP_ID=your-corp-id
export WECOM_AGENT_ID=your-agent-id
export WECOM_SECRET=your-secret

# 微信 (Wechaty)
export WECHATY_TOKEN=your-wechaty-token
```

## 功能测试

1. 启动 OpenClaw
2. 用企业微信/微信发消息给机器人
3. 应该能收到 AI 回复

## 常见问题

### Q: 微信扫码登录失败？

可能是账号风控，建议使用企业微信。

### Q: 消息收不到？

检查回调 URL 是否可访问（需要公网域名或内网穿透）。

### Q: 回复很慢？

检查网络连接，或者更换 AI 模型。

---

**上一章**：[接入飞书](./chapter5-feishu.md)
**下一章**：[接入钉钉](./chapter5-dingtalk.md)
