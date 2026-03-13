# 接入 GPT 模型

OpenClaw 也支持接入 OpenAI 的 GPT 模型。

## 前提条件

1. OpenAI 账号：https://platform.openai.com/
2. 获取 API Key

## 配置步骤

### 1. 修改配置文件

打开 `~/.openclaw/openclaw.json`：

```json
{
  "ai": {
    "provider": "openai",
    "model": "gpt-3.5-turbo",
    "openai": {
      "api_key": "${OPENAI_API_KEY}"
    }
  }
}
```

### 2. 设置环境变量

**Windows**（CMD）：
```cmd
set OPENAI_API_KEY=your-api-key
```

**Mac/Linux**（终端）：
```bash
export OPENAI_API_KEY=your-api-key
```

## 模型选择

| 模型 | 特点 | 价格 |
|------|------|------|
| gpt-3.5-turbo | 性价比高 | 便宜 |
| gpt-4 | 能力强 | 较贵 |
| gpt-4-turbo | 最新版 | 中等 |

## 代理设置

如果无法直接访问 OpenAI，需要配置代理：

```json
{
  "ai": {
    "provider": "openai",
    "model": "gpt-3.5-turbo",
    "openai": {
      "api_key": "${OPENAI_API_KEY}",
      "proxy": "http://127.0.0.1:7890"
    }
  }
}
```

## 常见问题

### Q: 无法连接？

检查网络或配置代理。

### Q: API 余额不足？

登录 OpenAI 账户检查余额。

---

**上一章**：[接入千问模型](./chapter4-qwen.md)
**下一章**：[多模型切换](./chapter4-multi-model.md)
