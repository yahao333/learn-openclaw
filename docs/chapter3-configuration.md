# 配置文件详解

## 配置文件位置

OpenClaw 的配置文件位于项目根目录，默认为 `config.yaml`。

## 配置结构

### 完整配置示例

```yaml
# 服务器配置
server:
  host: "0.0.0.0"
  port: 8080
  debug: false

# AI 模型配置
ai:
  provider: "qwen"  # qwen, openai, anthropic
  model: "qwen-turbo"

  # 千问配置
  qwen:
    api_key: "${DASHSCOPE_API_KEY}"
    base_url: "https://dashscope.aliyuncs.com/api/v1"

  # OpenAI 配置（备选）
  openai:
    api_key: "${OPENAI_API_KEY}"
    base_url: "https://api.openai.com/v1"

  # 模型参数
  temperature: 0.7
  max_tokens: 2000

# 平台配置
platforms:
  telegram:
    enabled: true
    bot_token: "${TELEGRAM_BOT_TOKEN}"
    api_id: "${TELEGRAM_API_ID}"
    api_hash: "${TELEGRAM_API_HASH}"

  feishu:
    enabled: false
    app_id: "${FEISHU_APP_ID}"
    app_secret: "${FEISHU_APP_SECRET}"
    verification_token: "${FEISHU_VERIFICATION_TOKEN}"

  discord:
    enabled: false
    bot_token: "${DISCORD_BOT_TOKEN}"

# 工具配置
tools:
  enabled:
    - browser
    - filesystem
    - execute
    - http

  # 浏览器配置
  browser:
    headless: true
    user_data_dir: "./data/browser"

  # 文件系统配置
  filesystem:
    allowed_paths:
      - "./data"
      - "/tmp"

  # 执行命令配置
  execute:
    allowed_commands:
      - "python"
      - "node"
      - "bash"

# 日志配置
logging:
  level: "INFO"
  file: "./logs/openclaw.log"
  max_size: 10485760  # 10MB
  backup_count: 5

# 定时任务
scheduled_tasks:
  - name: "morning_summary"
    cron: "0 7 * * *"
    action: "send_daily_summary"
```

## 配置说明

### server

| 配置项 | 说明 | 默认值 |
|--------|------|--------|
| host | 监听地址 | 0.0.0.0 |
| port | 监听端口 | 8080 |
| debug | 调试模式 | false |

### ai

| 配置项 | 说明 |
|--------|------|
| provider | AI 提供商：qwen, openai, anthropic |
| model | 模型名称 |
| api_key | API 密钥（支持环境变量） |
| temperature | 生成随机性，0-2 之间 |
| max_tokens | 最大生成 token 数 |

### platforms

各平台的配置选项：
- **telegram**: bot_token, api_id, api_hash
- **feishu**: app_id, app_secret, verification_token
- **discord**: bot_token

### tools

启用的工具列表及配置：
- browser: 浏览器自动化
- filesystem: 文件系统操作
- execute: 执行命令
- http: HTTP 请求

### scheduled_tasks

定时任务配置，使用 cron 表达式。

## 环境变量

推荐使用环境变量存储敏感信息：

```yaml
ai:
  qwen:
    api_key: "${DASHSCOPE_API_KEY}"

platforms:
  telegram:
    bot_token: "${TELEGRAM_BOT_TOKEN}"
```

然后在 `.env` 文件中设置：

```bash
# .env
DASHSCOPE_API_KEY=your-key-here
TELEGRAM_BOT_TOKEN=your-token-here
```

## 常见问题

### Q1：配置不生效？

检查配置文件格式是否正确，YAML 对缩进敏感。

### Q2：如何开启调试模式？

```yaml
server:
  debug: true
```

### Q3：如何限制文件操作范围？

```yaml
tools:
  filesystem:
    allowed_paths:
      - "./data"
      - "/tmp/openclaw"
```

---

**上一章**：[Docker 安装方式](./chapter2-docker.md)
**下一章**：[环境变量设置](./chapter3-env-vars.md)
