# 接入文心一言

文心一言是百度推出的国产 AI 大模型，在国内使用稳定。

## 前提条件

1. 访问百度智能云：https://cloud.baidu.com/
2. 注册账号并开通千帆大模型平台
3. 获取 API Key 和 Secret Key

## 获取 API Key

1. 访问 https://console.bce.baidu.com/qianfan/overview
2. 点击「应用接入」→「创建应用」
3. 记录 AppID、API Key、Secret Key

## 安装 SDK

```bash
pip install baidu-aip
```

## 配置 config.yaml

```yaml
ai:
  provider: "wenxin"
  model: "ernie-bot-turbo"

  wenxin:
    api_key: "${WENXIN_API_KEY}"
    secret_key: "${WENXIN_SECRET_KEY}"
```

## 设置环境变量

```bash
# Windows
set WENXIN_API_KEY=你的API_Key
set WENXIN_SECRET_KEY=你的Secret_Key

# Mac/Linux
export WENXIN_API_KEY=你的API_Key
export WENXIN_SECRET_KEY=你的Secret_Key
```

## 测试

```bash
python main.py
```

发送消息测试，应该能收到回复。

## 常见问题

### Q: 提示"invalid credential"？

检查 API Key 和 Secret Key 是否正确。

### Q: 免费额度用完了？

需要充值或等待下个月重置免费额度。

---

**上一章**：[接入千问](./chapter4-qwen.md)
**下一章**：[接入 GPT](./chapter4-gpt.md)
