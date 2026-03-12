# 项目：日程管理助手

本章我们将创建一个日程管理助手，帮助你管理日常事务。

## 功能需求

- 添加日程
- 查看日程
- 日程提醒
- 自动生成日程摘要

## 实现步骤

### 1. 创建日程存储

使用本地文件或数据库存储日程：

```python
import json
from datetime import datetime

class Calendar:
    def __init__(self, storage_path="./data/calendar.json"):
        self.storage_path = storage_path
        self.events = self._load()

    def _load(self):
        try:
            with open(self.storage_path, "r") as f:
                return json.load(f)
        except:
            return []

    def _save(self):
        with open(self.storage_path, "w") as f:
            json.dump(self.events, f, ensure_ascii=False)

    def add(self, title, time, description=""):
        event = {
            "id": len(self.events) + 1,
            "title": title,
            "time": time,
            "description": description,
            "completed": False
        }
        self.events.append(event)
        self._save()
        return f"已添加日程：{title}，时间：{time}"

    def list(self):
        if not self.events:
            return "暂无日程"
        result = "📅 日程列表：\n"
        for e in self.events:
            status = "✅" if e["completed"] else "⏳"
            result += f"{status} {e['id']}. {e['title']} - {e['time']}\n"
        return result

    def complete(self, event_id):
        for e in self.events:
            if e["id"] == event_id:
                e["completed"] = True
                self._save()
                return f"已完成：{e['title']}"
        return "未找到该日程"
```

### 2. 注册工具

```python
calendar = Calendar()

# 注册到 Agent
agent.register_tool("calendar_add", calendar.add)
agent.register_tool("calendar_list", calendar.list)
agent.register_tool("calendar_complete", calendar.complete)
```

### 3. 设置提醒

使用 cron 定时检查并提醒：

```yaml
scheduled_tasks:
  - name: "event_reminder"
    cron: "*/30 * * * *"  # 每30分钟检查
    action: "check_reminders"
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

**上一章**：[项目：天气推送助手](./chapter6-weather.md)
**下一章**：[项目：文件管理助手](./chapter6-files.md)
