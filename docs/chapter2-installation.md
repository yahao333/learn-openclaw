# 安装 OpenClaw

## 系统要求

在安装 OpenClaw 之前，请确保你的计算机满足以下要求：

- **操作系统**：Linux、macOS 或 Windows（WSL）
- **内存**：至少 2GB RAM
- **磁盘空间**：至少 1GB 可用空间
- **网络**：需要访问 AI 模型 API

## 安装方式

### 方式一：直接安装（推荐）

#### 1. 克隆项目

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
```

#### 2. 创建虚拟环境（可选但推荐）

```bash
# Python 3.8+ required
python3 -m venv venv

# 激活虚拟环境
# Linux/macOS:
source venv/bin/activate

# Windows:
venv\Scripts\activate
```

#### 3. 安装依赖

```bash
pip install -r requirements.txt
```

#### 4. 复制配置文件

```bash
cp config.example.yaml config.yaml
```

#### 5. 启动服务

```bash
python main.py
```

### 方式二：Docker 安装

如果你熟悉 Docker，可以使用 Docker 快速部署：

```bash
# 克隆项目
git clone https://github.com/openclaw/openclaw.git
cd openclaw

# 构建镜像
docker build -t openclaw .

# 运行容器
docker run -d -p 8080:8080 \
  -v ./config.yaml:/app/config.yaml \
  -v ./data:/app/data \
  --name openclaw \
  openclaw
```

详细 Docker 配置请见 [Docker 安装方式](./chapter2-docker.md)

### 方式三：Docker Compose（推荐）

更简单的 Docker 部署方式：

```bash
# 克隆项目
git clone https://github.com/openclaw/openclaw.git
cd openclaw

# 启动服务
docker-compose up -d
```

## 验证安装

安装完成后，打开浏览器访问 `http://localhost:8080`，应该能看到 OpenClaw 的欢迎页面。

你也可以在终端查看日志：

```bash
# 查看运行日志
docker logs openclaw

# 或者直接运行
python main.py
```

## 常见问题

### Q1：启动报错 "ModuleNotFoundError"？

**解决方法**：
```bash
pip install -r requirements.txt
```

### Q2：端口被占用？

**解决方法**：修改 `config.yaml` 中的端口配置：

```yaml
server:
  host: "0.0.0.0"
  port: 8081  # 改为其他端口
```

### Q3：无法连接 AI 模型？

**解决方法**：检查 API Key 配置，确保已正确设置。详见 [接入 AI 模型](./chapter4-qwen.md)

## 下一步

安装完成后，你需要：
1. 配置 AI 模型（详见 [接入千问模型](./chapter4-qwen.md)）
2. 连接通讯平台（详见 [接入 Telegram](./chapter5-telegram.md)）

---

**上一章**：[OpenClaw 的应用场景](./chapter1-applications.md)
**下一章**：[Docker 安装方式](./chapter2-docker.md)
