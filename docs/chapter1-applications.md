# OpenCLAW 的应用场景

## Web 开发

OpenCLAW 可以快速构建 Web 服务器和 API 接口。

### 示例：一个简单的 Web 服务器

```claw
import claw.http

// 创建 HTTP 服务器
server = http.Server.new(8080)

// 处理 GET 请求
server.get("/", func(req, res) {
    res.send("你好，欢迎学习 OpenCLAW！")
})

// 启动服务器
server.listen()
```

运行上面的代码，你就可以在浏览器访问 `http://localhost:8080`，看到"你好，欢迎学习 OpenCLAW！"的响应。

## 自动化脚本

OpenCLAW 非常适合编写自动化脚本，帮你完成重复性的工作。

### 示例：批量重命名文件

```claw
import claw.fs

// 获取当前目录下所有 .txt 文件
files = fs.listDir(".", "*.txt")

// 批量重命名
files.each(func(file) {
    newName = "backup_" + file
    fs.rename(file, newName)
    print("已将 " + file + " 重命名为 " + newName)
})
```

## 数据处理

OpenCLAW 内置强大的数据处理功能，适合处理 JSON、CSV 等格式的数据。

### 示例：处理 JSON 数据

```claw
import claw.json

// 解析 JSON
data = json.parse('{"name": "张三", "age": 25}')

// 访问数据
print("姓名：" + data.name)
print("年龄：" + data.age)

// 转换为 JSON 字符串
output = json.stringify(data)
print(output)
```

## 命令行工具

使用 OpenCLAW 可以快速开发命令行工具。

### 示例：计算器

```claw
import claw.cli

// 获取命令行参数
args = cli.args()

if args.length < 3 {
    print("用法：calc <数字1> <运算符> <数字2>")
    exit(1)
}

num1 = args[0].toNumber()
op = args[1]
num2 = args[2].toNumber()

result = match op {
    "+" => num1 + num2,
    "-" => num1 - num2,
    "*" => num1 * num2,
    "/" => num2 != 0 ? num1 / num2 : "错误：除数不能为零",
    _ => "未知运算符"
}

print("结果：" + result)
```

## 微服务开发

OpenCLAW 的轻量级和高性能特性使其非常适合开发微服务。

```claw
import claw.http

// 创建微服务
app = http.Server.new(3000)

// 用户服务
app.get("/api/users", func(req, res) {
    users = [
        {"id": 1, "name": "张三"},
        {"id": 2, "name": "李四"}
    ]
    res.json(users)
})

// 订单服务
app.get("/api/orders", func(req, res) {
    orders = [
        {"id": 101, "user_id": 1, "amount": 100},
        {"id": 102, "user_id": 2, "amount": 200}
    ]
    res.json(orders)
})

app.listen()
```

## 小结

本章我们介绍了 OpenCLAW 的主要应用场景，包括 Web 开发、自动化脚本、数据处理、命令行工具和微服务开发。这些示例展示了 OpenCLAW 的 versatility（多用途性）。

在后续章节中，我们将逐步深入学习每个应用场景的具体实现方法。

---

**上一章**：[什么是 OpenCLAW？](./chapter1-what-is-openclaw.md)
**下一章**：[安装 OpenCLAW](./chapter2-installation.md)
