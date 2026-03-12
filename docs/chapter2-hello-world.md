# 运行第一个程序

## 创建第一个程序

现在让我们创建并运行你的第一个 OpenCLAW 程序！

### 步骤 1：创建文件

在你的项目目录下，创建 `src/main.claw` 文件：

```claw
// 我的第一个 OpenCLAW 程序

// 输出 Hello World
print("Hello World!")
print("你好，欢迎学习 OpenCLAW！")
```

### 步骤 2：运行程序

在终端中运行：

```bash
claw run src/main.claw
```

你应该看到输出：

```
Hello World!
你好，欢迎学习 OpenCLAW！
```

## 代码解析

让我们解释一下这段代码：

### 注释

```claw
// 这是一个单行注释
/* 这是
   多行
   注释 */
```

注释不会影响程序执行，只是用来解释代码。

### print() 函数

`print()` 是 OpenCLAW 的内置函数，用于向终端输出内容。

```claw
print("要输出的内容")
```

你可以输出字符串、数字，甚至是复杂的数据结构。

## 稍微复杂一点的例子

让我们尝试更多输出：

```claw
// 输出字符串
print("===== 我的第一个程序 =====")
print("Hello World!")

// 输出数字
print(123)
print(3.14)

// 输出计算结果
print(1 + 2)
print(10 * 5)

// 输出布尔值
print(true)
print(false)

// 输出数组
print([1, 2, 3, 4, 5])

// 输出字典/对象
print({"name": "张三", "age": 25})
```

运行后输出：

```
===== 我的第一个程序 =====
Hello World!
123
3.14
3
50
true
false
[1, 2, 3, 4, 5]
{"name": "张三", "age": 25}
```

## 使用变量

让我们使用变量来存储数据：

```claw
// 定义变量
name = "张三"
age = 25
isStudent = true

// 使用变量
print("姓名：" + name)
print("年龄：" + age)
print("是学生吗？" + isStudent)
```

输出：

```
姓名：张三
年龄：25
是学生吗？true
```

## 交互式输入

让程序可以接收用户输入：

```claw
import claw.io

// 获取用户输入
print("请输入你的名字：")
name = io.input()

print("你好，" + name + "！")

print("请输入你的年龄：")
age = io.input()

print("你" + age + "岁了！")
```

运行效果：

```
请输入你的名字：
> 张三
你好，张三！
请输入你的年龄：
> 25
你25岁了！
```

## 使用交互模式

除了运行文件，你也可以使用交互模式来测试代码：

```bash
claw repl
```

在交互模式下，你可以直接输入代码并立即看到结果：

```
OpenCLAW REPL 1.0.0
> print("你好")
你好
> 1 + 2
3
> exit()
```

## 常见错误

### 1. 缺少引号

```claw
// 错误
print(Hello World)

// 正确
print("Hello World")
```

### 2. 括号不匹配

```claw
// 错误
print("Hello World"

// 正确
print("Hello World")
```

### 3. 文件路径错误

确保你在正确的目录下运行命令：

```bash
# 切换到项目目录
cd my-project

# 运行程序
claw run src/main.claw
```

## 小结

本章我们学习了：
1. 如何创建和运行第一个 OpenCLAW 程序
2. print() 函数的基本用法
3. 如何使用变量
4. 如何接收用户输入
5. 常见错误及解决方法

现在你已经掌握了 OpenCLAW 的基础知识！下一章我们将学习变量和数据类型。

---

**上一章**：[配置开发环境](./chapter2-setup.md)
**下一章**：[变量和数据类型](./chapter3-variables.md)
