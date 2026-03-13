# 多模型切换

OpenClaw 支持配置多个 AI 模型，可以根据需求切换。

## 配置多模型

打开 `~/.openclaw/openclaw.json`：

```json
{
  "ai": {
    "provider": "qwen",
    "qwen": {
      "api_key": "${DASHSCOPE_API_KEY}"
    },
    "openai": {
      "api_key": "${OPENAI_API_KEY}"
    }
  }
}
```

## 切换模型

修改 provider 即可切换：

```json
{
  "ai": {
    "provider": "openai",
    "model": "gpt-3.5-turbo"
  }
}
```

## 重启生效

修改配置后需要重启 OpenClaw：

```bash
# 停止服务
Ctrl + C

# 重新启动
python main.py
```

---

**上一章**：[接入 GPT 模型](./chapter4-gpt.md)
**下一章**：[接入 Telegram](./chapter5-telegram.md)
