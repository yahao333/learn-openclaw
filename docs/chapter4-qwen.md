# 接入千问模型

千问（Qwen）是阿里云推出的大语言模型，接入简单效果好。

## 前提条件

1. 注册阿里云 DashScope：https://dashscope.console.aliyun.com/
2. 获取 API Key

## 配置步骤

### 1. 安装 SDK

```bash
pip install dashscope
```

### 2. 配置 config.yaml

```yaml
ai:
  provider: "qwen"
  model: "qwen-turbo"  # 可选：qwen-turbo, qwen-plus, qwen-max

  qwen:
    api_key: "${DASHSCOPE_API_KEY}"
    base_url: "https://dashscope.aliyuncs.com/api/v1"
```

### 3. 设置环境变量

```bash
export DASHSCOPE_API_KEY="your-api-key"
```

## 模型选择

| 模型 | 特点 | 适用场景 |
|------|------|----------|
| qwen-turbo | 速度快，便宜 | 日常对话，简单任务 |
| qwen-plus | 能力更强 | 复杂推理 |
| qwen-max | 最强能力 | 高难度任务 |

## 测试

启动 OpenClaw 并发送消息测试：

```bash
python main.py
```

发送消息给机器人，应该能收到回复。

## 常见问题

### Q1：API Key 无效？

确认 API Key 已正确设置，且账户有余额。

### Q2：请求超时？

检查网络连接，或者切换到更快的模型如 qwen-turbo。

### Q3：回复内容不好？

调整 temperature 参数，或换用更强的模型。

---

**上一章**：[环境变量设置](./chapter3-env-vars.md)
**下一章**：[接入 GPT 模型](./chapter4-gpt.md)
