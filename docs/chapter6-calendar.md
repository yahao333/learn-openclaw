# 项目：日程管理助手

本章我们将创建一个日程管理助手，帮助你管理日常事务。

## 功能需求

- 添加日程
- 查看日程
- 日程提醒

## 配置步骤

### 1. 启用日历工具

在 `~/.openclaw/openclaw.json` 中启用：

```json
{
  "tools": {
    "calendar": {
      "enabled": true,
      "storage_path": "./data/calendar.json"
    }
  }
}
```

### 2. 重启服务

```bash
# 停止服务
Ctrl + C

# 重新启动
python main.py
```

## 使用示例

```
用户：帮我安排明天下午3点开会
OpenClaw：已添加日程：开会，时间：明天下午3点

用户：查看今天的日程
OpenClaw：📅 日程列表：
⏳ 1. 开会 - 明天下午3点
```

---

**上一章**：[天气推送助手](./chapter6-weather.md)
**下一章**：[文件管理助手](./chapter6-files.md)
