# 接入微信

微信是国内最常用的通讯工具，接入微信后可以直接用微信控制 AI 助手。

> ⚠️ **重要提示**：微信对机器人限制比较严，推荐使用**企业微信**

## 方案选择

### 方案一：企业微信（推荐）

企业微信对机器人更友好，接入更稳定。

#### 1. 创建企业微信应用

1. 访问 https://work.weixin.qq.com/
2. 注册企业微信
3. 进入「应用管理」→「创建应用」
4. 获取 AgentId 和 Secret

#### 2. 配置 openclaw.json

打开 `~/.openclaw/openclaw.json`：

```json
{
  "platforms": {
    "wecom": {
      "enabled": true,
      "corp_id": "${WECOM_CORP_ID}",
      "agent_id": "${WECOM_AGENT_ID}",
      "secret": "${WECOM_SECRET}"
    }
  }
}
```

#### 3. 设置环境变量

**Windows**（CMD）：
```cmd
set WECOM_CORP_ID=your-corp-id
set WECOM_AGENT_ID=your-agent-id
set WECOM_SECRET=your-secret
```

**Mac/Linux**（终端）：
```bash
export WECOM_CORP_ID=your-corp-id
export WECOM_AGENT_ID=your-agent-id
export WECOM_SECRET=your-secret
```

### 方案二：使用 Wechaty

Wechaty 是一个开源的微信机器人框架。

```bash
npm install wechaty
```

## 启动测试

```bash
python main.py
```

用企业微信扫描登录即可。

## 常见问题

### Q: 扫码登录失败？

可能是账号风控，建议使用企业微信。

### Q: 消息收不到？

检查回调 URL 是否可访问（需要公网域名或内网穿透）。

---

**上一章**：[接入飞书](./chapter5-feishu.md)
**下一章**：[接入钉钉](./chapter5-dingtalk.md)
