# 项目：文件管理助手

本章我们将创建一个文件管理助手，帮助你自动整理文件。

## 功能需求

- 文件分类整理
- 批量重命名
- 过期文件清理
- 文件搜索

## 实现步骤

### 1. 创建文件管理工具

```python
import os
import shutil
from pathlib import Path

class FileManager:
    def __init__(self, base_path="./data/files"):
        self.base_path = Path(base_path)
        self.base_path.mkdir(parents=True, exist_ok=True)

    def list_files(self, path="."):
        full_path = self.base_path / path
        if not full_path.exists():
            return "路径不存在"

        files = []
        for f in full_path.iterdir():
            files.append(f"{f.name} ({'📁 目录' if f.is_dir() else '📄 文件'})")

        return "\n".join(files) if files else "目录为空"

    def organize(self, folder):
        """按文件类型整理"""
        folder_path = self.base_path / folder
        if not folder_path.exists():
            return "文件夹不存在"

        categories = {
            "images": [".jpg", ".png", ".gif", ".bmp"],
            "documents": [".pdf", ".doc", ".docx", ".txt"],
            "videos": [".mp4", ".avi", ".mov"],
            "archives": [".zip", ".rar", ".7z"]
        }

        for category, extensions in categories.items():
            cat_path = folder_path / category
            cat_path.mkdir(exist_ok=True)

            for file in folder_path.iterdir():
                if file.is_file() and file.suffix.lower() in extensions:
                    shutil.move(str(file), str(cat_path / file.name))

        return "文件整理完成！"

    def search(self, keyword):
        """搜索文件"""
        results = []
        for file in self.base_path.rglob("*"):
            if file.is_file() and keyword.lower() in file.name.lower():
                results.append(str(file.relative_to(self.base_path)))

        return "\n".join(results) if results else "未找到匹配文件"

    def cleanup(self, days=30):
        """清理过期文件"""
        import time
        cutoff = time.time() - (days * 86400)
        count = 0

        for file in self.base_path.rglob("*"):
            if file.is_file():
                if file.stat().st_mtime < cutoff:
                    file.unlink()
                    count += 1

        return f"已清理 {count} 个过期文件"
```

### 2. 注册工具

```python
file_manager = FileManager()

agent.register_tool("file_list", file_manager.list_files)
agent.register_tool("file_organize", file_manager.organize)
agent.register_tool("file_search", file_manager.search)
agent.register_tool("file_cleanup", file_manager.cleanup)
```

### 3. 配置允许路径

```yaml
tools:
  filesystem:
    allowed_paths:
      - "./data/files"
      - "/tmp/openclaw"
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

**上一章**：[项目：日程管理助手](./chapter6-calendar.md)
