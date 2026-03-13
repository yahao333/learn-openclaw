# 接入飞书

飞书是字节跳动推出的企业协作平台，接入飞书后可以用飞书控制 AI。

## 前提条件

1. 飞书账号
2. 创建飞书企业应用

## 创建飞书应用

1. 打开 https://open.feishu.cn/
2. 创建企业应用
3. 添加机器人能力
4. 获取 App ID 和 App Secret

## 配置步骤

### 1. 修改配置文件

打开 `~/.openclaw/openclaw.json`：

```json
{
  "platforms": {
    "feishu": {
      "enabled": true,
      "app_id": "${FEISHU_APP_ID}",
      "app_secret": "${FEISHU_APP_SECRET}"
    }
  }
}
```

### 2. 设置环境变量

**Windows**（CMD）：
```cmd
set FEISHU_APP_ID=your-app-id
set FEISHU_APP_SECRET=your-app-secret
```

**Mac/Linux**（终端）：
```bash
export FEISHU_APP_ID=your-app-id
export FEISHU_APP_SECRET=your-app-secret
```

### 3. 配置事件订阅

在飞书开放平台配置：
- 回调 URL：`你的服务器地址/callback`
- 事件：`im.message.message_created_v1`

## 启动测试

```bash
python main.py
```

在飞书中给机器人发送消息测试。

## 常见问题

### Q: 消息收不到？

检查回调 URL 是否可访问。

### Q: 验证失败？

确认 app_secret 正确。

---

**上一章**：[接入 Telegram](./chapter5-telegram.md)
**下一章**：[接入微信](./chapter5-wechat.md)
