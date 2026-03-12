# Docker 安装方式

## 为什么使用 Docker？

Docker 可以让你快速部署 OpenClaw，无需手动安装依赖。容器化部署也方便迁移和管理。

## 前提条件

- 安装了 Docker
- 安装了 Docker Compose（可选）

## 步骤

### 1. 安装 Docker

#### macOS
```bash
# 使用 Homebrew
brew install docker
```

#### Linux (Ubuntu)
```bash
sudo apt-get update
sudo apt-get install docker.io docker-compose
sudo systemctl start docker
sudo systemctl enable docker
```

#### Windows
下载并安装 [Docker Desktop](https://www.docker.com/products/docker-desktop)

### 2. 克隆项目

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
```

### 3. 配置

创建 `config.yaml` 配置文件：

```yaml
# config.yaml
ai:
  provider: "qwen"
  qwen:
    api_key: "your-api-key-here"

platforms:
  telegram:
    enabled: true
    bot_token: "your-bot-token"

server:
  host: "0.0.0.0"
  port: 8080
```

### 4. 使用 Docker Compose 启动

创建 `docker-compose.yml` 文件：

```yaml
version: '3.8'

services:
  openclaw:
    image: openclaw/openclaw:latest
    container_name: openclaw
    ports:
      - "8080:8080"
    volumes:
      - ./config.yaml:/app/config.yaml
      - ./data:/app/data
    environment:
      - TZ=Asia/Shanghai
    restart: unless-stopped
```

启动服务：

```bash
docker-compose up -d
```

### 5. 验证

```bash
# 查看容器状态
docker ps

# 查看日志
docker logs openclaw
```

访问 `http://localhost:8080` 验证服务是否正常。

## 常用命令

```bash
# 启动
docker-compose start

# 停止
docker-compose stop

# 重启
docker-compose restart

# 查看日志
docker-compose logs -f

# 更新镜像
docker-compose pull
docker-compose up -d
```

## 数据持久化

Docker 容器中的数据会在容器删除时丢失。需要将数据目录挂载到主机：

```yaml
volumes:
  - ./config.yaml:/app/config.yaml
  - ./data:/app/data
  - ./logs:/app/logs
```

## 小结

本章我们学习了使用 Docker 部署 OpenClaw 的方法。Docker 方式部署简单快捷，适合生产环境使用。

---

**上一章**：[安装 OpenClaw](./chapter2-installation.md)
**下一章**：[配置文件详解](./chapter3-configuration.md)
