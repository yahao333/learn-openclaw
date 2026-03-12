# 项目：计算器

## 项目目标

本章我们将创建一个命令行计算器程序，实现以下功能：
- 加法
- 减法
- 乘法
- 除法
- 幂运算

## 项目结构

```
calculator/
├── src/
│   └── main.claw    # 主程序
├── tests/
│   └── calculator_test.claw
└── config.json
```

## 代码实现

### 步骤 1：创建项目

```bash
claw new calculator
cd calculator
```

### 步骤 2：编写计算器模块

创建 `src/calculator.claw`：

```claw
// src/calculator.claw

// 加法
func add(a, b) {
    return a + b
}

// 减法
func subtract(a, b) {
    return a - b
}

// 乘法
func multiply(a, b) {
    return a * b
}

// 除法
func divide(a, b) {
    if b == 0 {
        return "错误：除数不能为零"
    }
    return a / b
}

// 幂运算
func power(a, b) {
    return a ** b
}

// 计算器主函数
func calculate(a, operator, b) {
    match operator {
        "+" => return add(a, b)
        "-" => return subtract(a, b)
        "*" => return multiply(a, b)
        "/" => return divide(a, b)
        "**" => return power(a, b)
        _ => return "错误：未知运算符"
    }
}

exports = {
    "add": add,
    "subtract": subtract,
    "multiply": multiply,
    "divide": divide,
    "power": power,
    "calculate": calculate
}
```

### 步骤 3：编写主程序

创建 `src/main.claw`：

```claw
import claw.io
import "./calculator" as calc

print("=================================")
print("       欢迎使用计算器！")
print("=================================")
print("")
print("支持的运算：")
print("  +  加法")
print("  -  减法")
print("  *  乘法")
print("  /  除法")
print("  ** 幂运算")
print("  q  退出程序")
print("")

while true {
    print("")
    print("请输入运算（格式：数字 运算符 数字）：")
    print("例如：10 + 5")

    input = io.input()

    // 检查是否退出
    if input == "q" or input == "quit" {
        print("感谢使用，再见！")
        break
    }

    // 解析输入
    parts = input.split(" ")

    if parts.length != 3 {
        print("错误：请按照格式输入，例如：10 + 5")
        continue
    }

    // 获取数字和运算符
    a = parts[0].toNumber()
    operator = parts[1]
    b = parts[2].toNumber()

    // 检查数字是否有效
    if a == null or b == null {
        print("错误：请输入有效的数字")
        continue
    }

    // 计算结果
    result = calc.calculate(a, operator, b)

    print("结果：" + result)
}
```

### 步骤 4：运行程序

```bash
claw run src/main.claw
```

运行效果：

```
=================================
       欢迎使用计算器！
=================================

支持的运算：
  +  加法
  -  减法
  *  乘法
  /  除法
  ** 幂运算
  q  退出程序

请输入运算（格式：数字 运算符 数字）：
例如：10 + 5
> 10 + 5
结果：15

请输入运算（格式：数字 运算符 数字）：
例如：10 + 5
> 10 - 5
结果：5

请输入运算（格式：数字 运算符 数字）：
例如：10 + 5
> 10 / 0
结果：错误：除数不能为零

请输入运算（格式：数字 运算符 数字）：
例如：10 + 5
> quit
感谢使用，再见！
```

## 代码解释

### 1. 模块化设计

我们将计算逻辑放在单独的 `calculator.claw` 文件中，这样：
- 主程序更简洁
- 容易测试
- 方便复用

### 2. 输入解析

使用 `split(" ")` 将输入按空格分割成数组：

```claw
input = "10 + 5"
parts = input.split(" ")  // ["10", "+", "5"]
```

### 3. 错误处理

检查各种可能的错误情况：
- 输入格式不正确
- 数字无效
- 除数为零

### 4. 循环结构

使用 `while true` 配合 `break` 实现程序循环：

```claw
while true {
    // 获取输入
    // 处理
    if 退出条件 {
        break
    }
}
```

## 扩展练习

你可以尝试添加以下功能：

1. **连续计算**：让用户可以连续进行多次计算
2. **历史记录**：保存计算历史
3. **更多运算**：添加求余、平方根等
4. **界面美化**：添加更多提示信息

### 扩展：添加求余运算

在 `calculator.claw` 中添加：

```claw
// 求余
func modulo(a, b) {
    if b == 0 {
        return "错误：除数不能为零"
    }
    return a % b
}

// 在 calculate 函数中添加：
"%" => return modulo(a, b)
```

## 完整代码

### src/calculator.claw

```claw
// src/calculator.claw

func add(a, b) { return a + b }
func subtract(a, b) { return a - b }
func multiply(a, b) { return a * b }
func divide(a, b) {
    if b == 0 { return "错误：除数不能为零" }
    return a / b
}
func power(a, b) { return a ** b }
func modulo(a, b) {
    if b == 0 { return "错误：除数不能为零" }
    return a % b
}

func calculate(a, operator, b) {
    match operator {
        "+" => return add(a, b)
        "-" => return subtract(a, b)
        "*" => return multiply(a, b)
        "/" => return divide(a, b)
        "**" => return power(a, b)
        "%" => return modulo(a, b)
        _ => return "错误：未知运算符"
    }
}

exports = {
    "add": add,
    "subtract": subtract,
    "multiply": multiply,
    "divide": divide,
    "power": power,
    "modulo": modulo,
    "calculate": calculate
}
```

### src/main.claw

```claw
import claw.io
import "./calculator" as calc

print("=================================")
print("       欢迎使用计算器！")
print("=================================")
print("支持的运算：+ - * / ** %")
print("输入 q 退出程序")

while true {
    print("")
    print("请输入运算：")
    input = io.input()

    if input == "q" { break }

    parts = input.split(" ")

    if parts.length != 3 {
        print("错误：请输入 数字 运算符 数字")
        continue
    }

    a = parts[0].toNumber()
    operator = parts[1]
    b = parts[2].toNumber()

    if a == null or b == null {
        print("错误：请输入有效的数字")
        continue
    }

    result = calc.calculate(a, operator, b)
    print("结果：" + result)
}

print("再见！")
```

## 小结

本章我们完成了：
1. 创建计算器项目
2. 实现加减乘除等运算功能
3. 添加错误处理
4. 实现了交互式界面

通过这个项目，我们学会了：
- 模块化编程
- 用户输入处理
- 基本的错误处理

---

**上一章**：[项目：计算器](./chapter5-calculator.md)
**下一章**：[项目：待办事项应用](./chapter5-todo.md)
