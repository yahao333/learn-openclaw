# 接入钉钉

钉钉是阿里巴巴推出的企业通讯工具，接入简单稳定。

## 前提条件

1. 钉钉账号
2. 创建一个钉钉群（如没有可以用群聊测试）

## 创建钉钉机器人

1. 打开钉钉电脑版
2. 进入群聊 → 设置 → 智能群助手 → 添加机器人
3. 选择「自定义机器人」
4. 填写机器人名称，获取 Webhook 地址

## 配置步骤

### 1. 修改配置文件

打开 `~/.openclaw/openclaw.json`：

```json
{
  "platforms": {
    "dingtalk": {
      "enabled": true,
      "webhook": "${DINGTALK_WEBHOOK}"
    }
  }
}
```

### 2. 设置环境变量

**Windows**（CMD）：
```cmd
set DINGTALK_WEBHOOK=https://oapi.dingtalk.com/robot/send?access_token=xxx
```

**Mac/Linux**（终端）：
```bash
export DINGTALK_WEBHOOK=https://oapi.dingtalk.com/robot/send?access_token=xxx
```

## 启动测试

```bash
python main.py
```

在钉钉群发送消息测试。

## 常见问题

### Q: 机器人不发消息？

检查 Webhook 地址是否正确。

### Q: 安全验证失败？

确保消息包含设置的关键词。

---

**上一章**：[接入微信](./chapter5-wechat.md)
**下一章**：[接入 Discord](./chapter5-discord.md)
