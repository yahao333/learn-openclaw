# 项目：文件管理助手

本章我们将创建一个文件管理助手，帮助你自动整理文件。

## 功能需求

- 文件分类整理
- 批量重命名
- 过期文件清理

## 配置步骤

### 1. 启用文件工具

在 `~/.openclaw/openclaw.json` 中启用：

```json
{
  "tools": {
    "filesystem": {
      "enabled": true,
      "allowed_paths": ["./data/files"]
    }
  }
}
```

### 2. 重启服务

```bash
python main.py
```

## 使用示例

```
用户：列出下载文件夹
OpenClaw：📄 document.pdf
📄 photo.jpg
📁 videos

用户：整理下载文件夹
OpenClaw：文件整理完成！

用户：搜索 document
OpenClaw：documents/document.pdf
documents/report.docx
```

---

**上一章**：[日程管理助手](./chapter6-calendar.md)
