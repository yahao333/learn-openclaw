# 项目：天气推送助手

本章我们将创建一个天气推送助手，自动推送天气预报。

## 功能需求

- 获取天气预报
- 定时推送天气
- 支持多城市查询

## 实现步骤

### 1. 获取天气 API

推荐使用免费天气 API：
- 和风天气：https://qweather.com/
- OpenWeatherMap：https://openweathermap.org/

### 2. 创建天气工具

创建 `tools/weather.py`：

```python
import requests

class WeatherTool:
    def __init__(self, api_key):
        self.api_key = api_key
        self.base_url = "https://api.qweather.com/v7"

    def get_weather(self, location):
        url = f"{self.base_url}/weather/now"
        params = {
            "location": location,
            "key": self.api_key
        }
        response = requests.get(url, params=params)
        data = response.json()

        if data["code"] == "200":
            now = data["now"]
            return f"{location} 天气：{now['text']}，温度：{now['temp']}°C"
        else:
            return "获取天气失败"
```

### 3. 配置定时任务

在 `config.yaml` 中添加：

```yaml
scheduled_tasks:
  - name: "morning_weather"
    cron: "0 7 * * *"  # 每天早上7点
    action: "send_weather"
    cities:
      - "北京"
      - "上海"
```

### 4. 注册工具

在 `main.py` 中注册天气工具：

```python
from tools.weather import WeatherTool

weather_tool = WeatherTool(api_key="your-key")

# 注册到 Agent
agent.register_tool("weather", weather_tool.get_weather)
```

## 测试

运行程序，测试天气查询：

```
用户：北京天气怎么样？
OpenClaw：北京 天气：晴，温度：15°C
```

## 扩展功能

- 添加穿衣建议
- 添加空气质量指数
- 支持语音播报

---

**上一章**：[接入 Discord](./chapter5-discord.md)
**下一章**：[项目：日程管理助手](./chapter6-calendar.md)
