# 接入 Discord

Discord 是国际常用的通讯平台，接入后可以用 Discord 控制 AI。

## 前提条件

1. Discord 账号
2. 创建 Discord 应用

## 创建 Discord 应用

1. 打开 https://discord.com/developers/applications
2. 创建新应用
3. 添加机器人（Bot）
4. 获取 Bot Token

## 配置步骤

### 1. 修改配置文件

打开 `~/.openclaw/openclaw.json`：

```json
{
  "platforms": {
    "discord": {
      "enabled": true,
      "bot_token": "${DISCORD_BOT_TOKEN}"
    }
  }
}
```

### 2. 设置环境变量

**Windows**（CMD）：
```cmd
set DISCORD_BOT_TOKEN=your-bot-token
```

**Mac/Linux**（终端）：
```bash
export DISCORD_BOT_TOKEN=your-bot-token
```

### 3. 邀请机器人

在 Discord 开发者门户生成邀请链接，添加到服务器。

## 启动测试

```bash
python main.py
```

在 Discord 中发送消息测试。

---

**上一章**：[接入钉钉](./chapter5-dingtalk.md)
**下一章**：[天气推送助手](./chapter6-weather.md)
