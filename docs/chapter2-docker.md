# Docker 安装方式

Docker 可以让你快速部署 OpenClaw，无需手动安装依赖。

## 前提条件

- 安装了 Docker
- 安装了 Docker Compose

## 安装 Docker

### macOS
```bash
brew install docker
```

### Linux (Ubuntu)
```bash
sudo apt-get update
sudo apt-get install docker.io docker-compose
sudo systemctl start docker
```

### Windows
下载并安装 [Docker Desktop](https://www.docker.com/products/docker-desktop)

## 快速开始

### 1. 克隆项目

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
```

### 2. 创建配置文件

```bash
mkdir -p ~/.openclaw
cp config.example.json ~/.openclaw/openclaw.json
```

### 3. 修改配置

编辑 `~/.openclaw/openclaw.json`，配置你的 AI 模型：

```json
{
  "ai": {
    "provider": "qwen",
    "qwen": {
      "api_key": "${DASHSCOPE_API_KEY}"
    }
  }
}
```

### 4. 使用 Docker Compose 启动

```bash
docker-compose up -d
```

## 常用命令

```bash
# 启动
docker-compose start

# 停止
docker-compose stop

# 查看日志
docker-compose logs -f

# 重启
docker-compose restart
```

## 数据持久化

Docker 容器中的数据会在容器删除时丢失。需要将数据目录挂载到主机：

```yaml
# docker-compose.yml
volumes:
  - ~/.openclaw:/root/.openclaw
```

## 常见问题

### Q: Docker 启动失败？

检查 Docker 是否正常运行：`docker ps`

### Q: 端口被占用？

修改 docker-compose.yml 中的端口映射。

---

**上一章**：[安装 OpenClaw](./chapter2-installation.md)
**下一章**：[配置文件详解](./chapter3-configuration.md)
