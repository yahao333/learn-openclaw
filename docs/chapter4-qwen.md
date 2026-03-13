# 接入千问模型

千问是阿里巴巴推出的国产 AI，完全免费，接入简单！

## 为什么选千问？

- ✅ **免费额度**：新用户送大量免费额度
- ✅ **国内访问**：不需要翻墙
- ✅ **中文效果好**：对中文理解能力强
- ✅ **响应速度快**：国内服务器

## 第一步：获取 API Key

1. 打开：https://dashscope.console.aliyun.com/
2. 点击「开通服务」→「立即开通」（免费）
3. 点击「API-KEY 管理」→「创建 API-KEY」
4. 复制保存好你的 API Key

> ⚠️ **注意**：API Key 只显示一次，一定要保存好！

## 第二步：安装 SDK

```bash
pip install dashscope
```

## 第三步：配置 config.yaml

打开 `config.yaml`，修改 AI 配置：

```yaml
ai:
  provider: "qwen"
  model: "qwen-turbo"  # 可选：qwen-turbo（快）、qwen-plus（强）、qwen-max（最强）

  qwen:
    api_key: "${DASHSCOPE_API_KEY}"
```

## 第四步：设置环境变量

**Windows**（CMD 中）：
```cmd
set DASHSCOPE_API_KEY=你的APIKey
```

**Mac/Linux**（终端）：
```bash
export DASHSCOPE_API_KEY=你的APIKey
```

> 💡 **小技巧**：也可以直接写在配置文件中（不推荐，不安全）：
> ```yaml
> qwen:
>   api_key: "sk-xxx"  # 不推荐！
> ```

## 第五步：测试

```bash
python main.py
```

然后尝试发送消息，应该能收到 AI 回复了！

## 模型选择建议

| 模型 | 速度 | 能力 | 推荐场景 |
|------|------|------|----------|
| qwen-turbo | ⚡⚡⚡ | ⭐⭐ | 日常对话，简单任务 |
| qwen-plus | ⚡⚡ | ⭐⭐⭐ | 复杂推理 |
| qwen-max | ⚡ | ⭐⭐⭐⭐ | 高难度任务 |

新手建议先选 `qwen-turbo`，免费额度最多！

## 常见问题

### Q: 提示"没有开通服务"？

去 https://dashscope.console.aliyun.com/ 开通服务

### Q: 额度用完了？

千问有免费额度，用完需要付费或下个月重置

### Q: 回复很慢？

可能是网络问题，或者换成 qwen-turbo 模型

### Q: 如何查看剩余额度？

访问：https://dashscope.console.aliyun.com/ → 查看配额

---

**上一章**：[环境变量设置](./chapter3-env-vars.md)
**下一章**：[接入文心一言](./chapter4-wenxin.md)
