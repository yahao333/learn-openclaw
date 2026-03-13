# Docker 安装（进阶）

> 推荐有 Docker 经验的用户使用，新手建议用 [普通安装](./chapter2-installation.md)

## 什么是 Docker？

Docker 可以把 OpenClaw 打包成一个"容器"，在哪里都能运行。

## 前置要求

- 安装了 Docker Desktop：https://www.docker.com/products/docker-desktop/

## 安装步骤

### 1. 克隆项目

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
```

### 2. 创建配置

```bash
mkdir -p ~/.openclaw
cp config.example.json ~/.openclaw/openclaw.json
```

### 3. 启动

```bash
docker-compose up -d
```

### 4. 停止

```bash
docker-compose down
```

---

## 常见问题

### Q: Docker 启动失败？

检查 Docker 是否正常运行：`docker ps`

---

**上一章**：[安装 OpenClaw](./chapter2-installation.md)
**下一章**：[配置文件详解](./chapter3-configuration.md)
