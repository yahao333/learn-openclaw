# 模块和包

## 什么是模块？

模块是一个包含代码的文件，可以被其他程序引用。使用模块可以让代码更好地组织、复用和共享。

## 使用 import 导入模块

### 导入内置模块

```claw
// 导入 HTTP 模块
import claw.http

// 创建服务器
server = http.Server.new(8080)
server.listen()
```

### 导入标准库

```claw
// 导入 JSON 模块
import claw.json

// 解析 JSON
data = json.parse('{"name": "张三"}')
print(data.name)

// 转为 JSON
str = json.stringify(data)
print(str)

// 导入文件系统模块
import claw.fs

// 读取文件
content = fs.readFile("test.txt")
print(content)

// 写入文件
fs.writeFile("hello.txt", "你好！")
```

### 导入第三方包

```claw
// 安装包
# claw pkg install axios

// 导入
import axios

// 发送 HTTP 请求
response = axios.get("https://api.example.com/data")
print(response.data)
```

## 创建自己的模块

### 步骤 1：创建模块文件

创建文件 `src/utils.claw`：

```claw
// src/utils.claw

// 定义工具函数
func sayHello(name) {
    return "你好，" + name + "！"
}

func add(a, b) {
    return a + b
}

// 导出函数（公开给其他文件使用）
exports = {
    "sayHello": sayHello,
    "add": add
}
```

### 步骤 2：在主程序中使用

```claw
// 导入自定义模块
import "./src/utils" as utils

// 调用模块中的函数
print(utils.sayHello("张三"))  // 你好，张三！
print(utils.add(3, 5))         // 8
```

## 包管理器

### 安装包

```bash
# 安装单个包
claw pkg install axios

# 安装多个包
claw pkg install axios jsonwebtoken express

# 安装到项目
cd my-project
claw pkg install
```

### 查看已安装的包

```bash
claw pkg list
```

### 更新包

```bash
claw pkg update
claw pkg update axios
```

### 卸载包

```bash
claw pkg uninstall axios
```

## 项目结构

一个典型的 OpenCLAW 项目结构：

```
my-project/
├── src/
│   ├── main.claw        # 主程序入口
│   ├── utils/
│   │   ├── math.claw    # 数学工具函数
│   │   └── string.claw  # 字符串处理函数
│   └── models/
│       └── user.claw    # 用户模型
├── tests/               # 测试文件
├── docs/                # 文档
├── config.json          # 项目配置
├── package.json         # 依赖管理
└── README.md            # 项目说明
```

## package.json 配置文件

```json
{
    "name": "my-openclaw-app",
    "version": "1.0.0",
    "description": "我的 OpenCLAW 应用",
    "main": "src/main.claw",
    "dependencies": {
        "express": "^4.0.0",
        "axios": "^1.0.0"
    },
    "scripts": {
        "start": "claw run src/main.claw",
        "test": "claw test",
        "build": "claw build"
    },
    "author": "Your Name",
    "license": "MIT"
}
```

## 模块的加载顺序

```claw
// 1. 内置模块
import claw.fs

// 2. 第三方模块
import express

// 3. 本地模块（相对路径）
import "./utils"
import "../lib/helper"

// 4. 本地模块（绝对路径）
import "/path/to/module"
```

## 常见问题

### Q1：模块找不到？

确保：
1. 包已正确安装
2. 路径正确
3. 模块文件存在

### Q2：循环引用？

尽量避免模块之间相互引用。

### Q3：版本冲突？

在 `package.json` 中指定兼容的版本号。

## 实战：创建工具模块

### 1. 创建 math_utils.claw

```claw
// src/math_utils.claw

// 求和
func sum(numbers) {
    total = 0
    for n in numbers {
        total += n
    }
    return total
}

// 平均值
func average(numbers) {
    if numbers.length == 0 {
        return 0
    }
    return sum(numbers) / numbers.length
}

// 最大值
func max(numbers) {
    if numbers.length == 0 {
        return null
    }
    m = numbers[0]
    for n in numbers {
        if n > m {
            m = n
        }
    }
    return m
}

// 最小值
func min(numbers) {
    if numbers.length == 0 {
        return null
    }
    m = numbers[0]
    for n in numbers {
        if n < m {
            m = n
        }
    }
    return m
}

exports = {
    "sum": sum,
    "average": average,
    "max": max,
    "min": min
}
```

### 2. 在主程序中使用

```claw
import "./src/math_utils" as math

nums = [1, 2, 3, 4, 5]

print("总和：" + math.sum(nums))           // 15
print("平均值：" + math.average(nums))    // 3.0
print("最大值：" + math.max(nums))         // 5
print("最小值：" + math.min(nums))         // 1
```

## 小结

本章我们学习了：
1. 什么是模块
2. 如何导入内置模块和第三方包
3. 如何创建自己的模块
4. 包管理器的使用
5. 项目的目录结构
6. 实战：创建工具模块

---

**上一章**：[函数的定义和调用](./chapter4-functions.md)
**下一章**：[项目：计算器](./chapter5-calculator.md)
