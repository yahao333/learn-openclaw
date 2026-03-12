# 接入 Discord

Discord 是游戏社区常用的通讯平台，OpenClaw 也支持接入。

## 前提条件

1. Discord 账号
2. 创建 Discord 应用：https://discord.com/developers/applications

## 配置步骤

### 1. 创建 Discord 应用

1. 打开 Discord 开发者门户
2. 创建新应用
3. 添加机器人（Bot）
4. 获取 Bot Token

### 2. 配置权限

选择以下权限：
- Send Messages
- Read Message History

### 3. 配置 config.yaml

```yaml
platforms:
  discord:
    enabled: true
    bot_token: "${DISCORD_BOT_TOKEN}"
    allowed_guilds:
      - "guild_id_1"
    allowed_channels:
      - "channel_id_1"
```

### 4. 设置环境变量

```bash
export DISCORD_BOT_TOKEN="your-bot-token"
```

### 5. 邀请机器人

生成邀请链接并添加到服务器。

## 启动

```bash
python main.py
```

---

**上一章**：[接入飞书](./chapter5-feishu.md)
**下一章**：[项目：天气推送助手](./chapter6-weather.md)
