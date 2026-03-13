# OpenClaw 中文教程

[![stars](https://img.shields.io/github/stars/yahao333/learn-openclaw?style=flat)](https://github.com/yahao333/learn-openclaw/stargazers)
[![forks](https://img.shields.io/github/forks/yahao333/learn-openclaw?style=flat)](https://github.com/yahao333/learn-openclaw/network)
[![license](https://img.shields.io/github/license/yahao333/learn-openclaw?style=flat)](https://github.com/yahao333/learn-openclaw/blob/main/LICENSE)

🎯 **面向零基础小白的 OpenClaw 入门指南**，手把手教你打造私人 AI 助手！

## 📚 这是什么？

**OpenClaw** 是一款开源的 AI Agent（智能体）框架，你可以把它理解为一个**24 小时待命的智能助手**。

它能帮你做：
- ⏰ **定时提醒**：早上自动推送天气、日程
- 📧 **自动处理邮件**：自动回复、分类整理
- 📁 **文件管理**：自动整理文件夹
- 💬 **微信/飞书控制**：用微信就能指挥它
- 🔄 **自动化任务**：每天自动执行重复工作

## ✨ 为什么选择 OpenClaw？

| 特点 | 说明 |
|------|------|
| 🏠 **自托管** | 数据存在自己电脑，安全放心 |
| 🤖 **国产模型** | 支持千问、文心等国产 AI |
| 📱 **微信/飞书** | 支持微信、飞书、钉钉接入 |
| 💰 **免费开源** | 不花冤枉钱 |
| 🔒 **隐私保护** | 数据不上传云端 |

## 🚀 快速开始（ Windows/Mac/Linux 都支持）

### 第一步：安装必要软件

**Windows 用户：**
1. 安装 Python：https://www.python.org/downloads/（记得勾选"Add Python to PATH"）
2. 下载 OpenClaw：https://github.com/openclaw/openclaw/archive/refs/heads/main.zip
3. 解压到文件夹

**Mac 用户：**
```bash
# 打开终端，运行：
brew install python3 git
```

**Linux 用户：**
```bash
sudo apt update
sudo apt install python3 python3-pip git
```

### 第二步：运行 OpenClaw

```bash
# 1. 克隆项目（下载代码）
git clone https://github.com/openclaw/openclaw.git
cd openclaw

# 2. 安装依赖（自动安装需要的库）
pip install -r requirements.txt

# 3. 复制配置文件
copy config.example.yaml config.yaml

# 4. 启动！
python main.py
```

> ⚠️ **常见问题**：如果运行报错"pip 不是内部命令"，请重新安装 Python 并勾选 Add to PATH

### 第三步：配置（可选）

首次安装可以直接跳过配置，使用默认设置。后续可以：
- 接入国产 AI（千问、文心一言）
- 连接微信/飞书

详细教程见下方。

## 📖 教程目录

### 🅰️ 基础入门

| 章节 | 内容 | 难度 |
|------|------|------|
| [什么是 OpenClaw？](./docs/chapter1-what-is-openclaw.md) | 了解 AI Agent 是什么 | ⭐ |
| [OpenClaw 能做什么？](./docs/chapter1-applications.md) | 实际应用场景 | ⭐ |
| [安装 OpenClaw](./docs/chapter2-installation.md) | 详细安装步骤 | ⭐⭐ |
| [Docker 安装](./docs/chapter2-docker.md) | 容器化部署 | ⭐⭐ |

### 🅱️ 配置进阶

| 章节 | 内容 | 难度 |
|------|------|------|
| [配置文件详解](./docs/chapter3-configuration.md) | 配置文件怎么改 | ⭐⭐ |
| [环境变量设置](./docs/chapter3-env-vars.md) | 保护你的 API Key | ⭐⭐ |

### 🅾️ AI 模型接入

| 章节 | 内容 | 难度 |
|------|------|------|
| [接入千问](./docs/chapter4-qwen.md) | 阿里免费 AI | ⭐⭐ |
| [接入文心一言](./docs/chapter4-wenxin.md) | 百度免费 AI | ⭐⭐ |
| [接入 GPT](./docs/chapter4-gpt.md) | OpenAI | ⭐⭐⭐ |
| [多模型切换](./docs/chapter4-multi-model.md) | 自由切换 AI | ⭐⭐⭐ |

### 🅾️ 平台接入（重点！）

| 章节 | 内容 | 难度 |
|------|------|------|
| [接入飞书](./docs/chapter5-feishu.md) | 企业微信/飞书 | ⭐⭐⭐ |
| [接入微信](./docs/chapter5-wechat.md) | 微信控制 AI | ⭐⭐⭐⭐ |
| [接入钉钉](./docs/chapter5-dingtalk.md) | 钉钉机器人 | ⭐⭐⭐ |
| [接入 Telegram](./docs/chapter5-telegram.md) | 国际用户 | ⭐⭐⭐ |

### 🆘 实战项目

| 章节 | 内容 |
|------|------|
| [天气推送助手](./docs/chapter6-weather.md) | 每天自动推送天气 |
| [日程管理助手](./docs/chapter6-calendar.md) | 智能日程管理 |
| [文件管理助手](./docs/chapter6-files.md) | 自动整理文件 |

## ❓ 常见问题

### Q: 安装失败怎么办？
**A:** 检查 Python 是否正确安装，打开 CMD 输入 `python --version` 确认

### Q: 打不开 GitHub 下载？
**A:** 可以用 Gitee 镜像：https://gitee.com/openclaw/openclaw

### Q: 需要付费吗？
**A:** OpenClaw 本身免费，但调用 AI 模型可能需要付费（千问有免费额度）

### Q: 中文乱码怎么办？
**A:** 在命令行执行 `chcp 65001` 然后重新运行

## 📞 获取帮助

- 🐛 提交问题：https://github.com/openclaw/openclaw/issues
- 💬 加入社区：添加微信群（详见文档）
- 📖 更多教程：持续更新中...

## 👍  Star 支持

如果这个教程对你有帮助，欢迎点个 Star ⭐ 支持一下！

---

Made with ❤️ for Chinese developers
