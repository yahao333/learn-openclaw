# 配置文件详解

OpenClaw 的配置文件位于 `~/.openclaw/openclaw.json`（Mac/Linux）或 `C:\Users\你的用户名\.openclaw\openclaw.json`（Windows）。

## 配置文件位置

```bash
# 查看配置文件
# Mac/Linux
cat ~/.openclaw/openclaw.json

# Windows
type C:\Users\你的用户名\.openclaw\openclaw.json
```

## 配置结构

### 完整配置示例

```json
{
  "server": {
    "host": "0.0.0.0",
    "port": 8080
  },
  "ai": {
    "provider": "qwen",
    "model": "qwen-turbo",
    "qwen": {
      "api_key": "your-api-key"
    }
  },
  "platforms": {
    "telegram": {
      "enabled": false,
      "bot_token": ""
    },
    "feishu": {
      "enabled": false,
      "app_id": "",
      "app_secret": ""
    }
  },
  "tools": {
    "enabled": ["browser", "filesystem", "execute", "http"]
  }
}
```

## 配置说明

### server（服务器配置）

| 配置项 | 说明 | 默认值 |
|--------|------|--------|
| host | 监听地址 | 0.0.0.0 |
| port | 监听端口 | 8080 |

### ai（AI 模型配置）

| 配置项 | 说明 |
|--------|------|
| provider | AI 提供商：`qwen`、`openai`、`anthropic` |
| model | 模型名称 |
| qwen.api_key | 千问 API Key |

### platforms（平台配置）

| 平台 | 配置项 |
|------|--------|
| telegram | bot_token |
| feishu | app_id, app_secret |
| discord | bot_token |

### tools（工具配置）

```json
{
  "tools": {
    "enabled": ["browser", "filesystem", "execute", "http"]
  }
}
```

- browser：浏览器自动化
- filesystem：文件系统操作
- execute：执行命令
- http：HTTP 请求

## 环境变量

推荐使用环境变量：

```json
{
  "ai": {
    "qwen": {
      "api_key": "${DASHSCOPE_API_KEY}"
    }
  }
}
```

然后设置环境变量：

```bash
# Mac/Linux
export DASHSCOPE_API_KEY=your-key

# Windows
set DASHSCOPE_API_KEY=your-key
```

## 常见问题

### Q: 配置文件不存在？

首次运行时会自动创建默认配置文件。

### Q: 修改配置不生效？

修改后需要重启 OpenClaw：

```bash
# 停止服务
Ctrl + C

# 重新启动
python main.py
```

### Q: 如何开启调试模式？

```json
{
  "server": {
    "debug": true
  }
}
```

---

**上一章**：[Docker 安装](./chapter2-docker.md)
**下一章**：[环境变量设置](./chapter3-env-vars.md)
