# OpenClaw 中文教程

[![stars](https://img.shields.io/github/stars/yahao333/learn-openclaw?style=flat)](https://github.com/yahao333/learn-openclaw/stargazers)
[![forks](https://img.shields.io/github/forks/yahao333/learn-openclaw?style=flat)](https://github.com/yahao333/learn-openclaw/network)
[![license](https://img.shields.io/github/license/yahao333/learn-openclaw?style=flat)](https://github.com/yahao333/learn-openclaw/blob/main/LICENSE)

面向小白的 OpenClaw 入门指南，打造你的私人 AI 助手。

## 什么是 OpenClaw？

OpenClaw 是一款开源的自托管 AI Agent（智能体）框架，被誉为"开源版 JARVIS"或"数字打工人"。

与传统的 AI 聊天机器人不同，OpenClaw 能够根据你的指令**主动执行任务**，比如：
- 早上自动推送日历、天气和新闻摘要
- 自动处理邮件和管理文件
- 编写代码和调试程序
- 24 小时不间断执行任务

## 特性

- **自托管**：数据存储在本地，安全性高
- **多模型支持**：可接入多种 AI 大模型（千问、GPT 等）
- **多平台接入**：支持 Telegram、飞书、WhatsApp、Discord 等
- **真正自动化**：不是被动聊天，而是主动执行任务
- **中文教程**：全简体中文内容，面向零基础小白

## 快速开始

### 1. 安装

```bash
# 克隆项目
git clone https://github.com/openclaw/openclaw.git
cd openclaw

# 安装依赖
pip install -r requirements.txt
```

### 2. 配置

编辑 `config.yaml` 文件，配置你的 AI 模型和平台连接。

### 3. 运行

```bash
python main.py
```

## 教程目录

- [教程大纲](./docs/outline.md)
- [第一章：初识 OpenClaw](./docs/chapter1-what-is-openclaw.md)
- [第二章：环境搭建](./docs/chapter2-installation.md)
- [第三章：基础配置](./docs/chapter3-configuration.md)
- [第四章：接入 AI 模型](./docs/chapter4-ai-models.md)
- [第五章：平台集成](./docs/chapter5-platforms.md)
- [第六章：实战项目](./docs/chapter6-projects.md)

## 学习路线

1. **入门阶段**：了解 OpenClaw 是什么，安装开发环境
2. **配置阶段**：掌握配置文件和基本设置
3. **集成阶段**：学习接入 AI 模型和通讯平台
4. **实践阶段**：打造你的私人 AI 助手

## 适用人群

- 想要拥有私人 AI 助手的用户
- 对 AI Agent 感兴趣的技术爱好者
- 希望自动化日常工作的开发者

## 官方资源

- 官网：[https://openclaw.ai](https://openclaw.ai)
- GitHub：[https://github.com/openclaw/openclaw](https://github.com/openclaw/openclaw)

## 贡献

欢迎提交 Issue 和 Pull Request！

## 许可证

MIT License
