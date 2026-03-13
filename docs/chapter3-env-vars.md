# 环境变量设置

环境变量用于存储敏感信息（如 API Key），避免硬编码在配置文件中。

## 在配置文件中使用环境变量

打开 `~/.openclaw/openclaw.json`，使用 `${ENV_VAR}` 格式引用环境变量：

```json
{
  "ai": {
    "provider": "qwen",
    "qwen": {
      "api_key": "${DASHSCOPE_API_KEY}"
    }
  }
}
```

## 设置环境变量

**Windows**（CMD）：
```cmd
set DASHSCOPE_API_KEY=your-api-key
```

**Mac/Linux**（终端）：
```bash
export DASHSCOPE_API_KEY=your-api-key
```

## 常用环境变量

| 变量名 | 用途 |
|--------|------|
| DASHSCOPE_API_KEY | 千问 API Key |
| OPENAI_API_KEY | OpenAI API Key |
| TELEGRAM_BOT_TOKEN | Telegram Bot Token |
| FEISHU_APP_ID | 飞书 App ID |
| FEISHU_APP_SECRET | 飞书 App Secret |

## 持久化设置（可选）

### Windows

创建 `openclaw.bat` 文件：
```cmd
@echo off
set DASHSCOPE_API_KEY=your-api-key
python main.py
```

### Mac/Linux

在 `~/.bashrc` 或 `~/.zshrc` 中添加：
```bash
export DASHSCOPE_API_KEY=your-api-key
```

然后运行 `source ~/.bashrc` 生效。

---

**上一章**：[配置文件详解](./chapter3-configuration.md)
**下一章**：[接入千问模型](./chapter4-qwen.md)
