# 项目：天气推送助手

本章我们将创建一个天气推送助手，自动推送天气预报。

## 功能需求

- 获取天气预报
- 定时推送天气
- 支持多城市查询

## 实现步骤

### 1. 获取天气 API

推荐使用和风天气：https://qweather.com/

### 2. 配置天气工具

在 `~/.openclaw/openclaw.json` 中添加工具配置：

```json
{
  "tools": {
    "weather": {
      "provider": "qweather",
      "api_key": "${QWEATHER_API_KEY}"
    }
  }
}
```

### 3. 设置定时任务

```json
{
  "scheduled_tasks": [
    {
      "name": "morning_weather",
      "cron": "0 7 * * *",
      "action": "send_weather",
      "cities": ["北京", "上海"]
    }
  ]
}
```

### 4. 启动测试

```bash
python main.py
```

## 测试

```
用户：北京天气怎么样？
OpenClaw：北京 天气：晴，温度：15°C
```

---

**上一章**：[接入 Discord](./chapter5-discord.md)
**下一章**：[日程管理助手](./chapter6-calendar.md)
