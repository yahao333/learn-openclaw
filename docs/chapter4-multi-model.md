# 多模型切换

OpenClaw 支持配置多个 AI 模型，可以根据需求切换。

## 配置多模型

```yaml
ai:
  # 默认模型
  provider: "qwen"

  # 模型配置
  models:
    qwen:
      provider: "qwen"
      model: "qwen-turbo"
      api_key: "${DASHSCOPE_API_KEY}"

    gpt:
      provider: "openai"
      model: "gpt-3.5-turbo"
      api_key: "${OPENAI_API_KEY}"
```

## 切换模型

### 通过命令切换

```
/model qwen
/model gpt
```

### 通过配置切换

```yaml
ai:
  provider: "gpt"
```

## 自动切换

可以设置根据任务类型自动选择模型：

```yaml
ai:
  auto_select:
    - model: "qwen"
      keywords: ["简单", "日常"]
    - model: "gpt"
      keywords: ["复杂", "代码"]
    - model: "qwen-max"
      keywords: ["推理"]
```

---

**上一章**：[接入 GPT 模型](./chapter4-gpt.md)
**下一章**：[接入 Telegram](./chapter5-telegram.md)
