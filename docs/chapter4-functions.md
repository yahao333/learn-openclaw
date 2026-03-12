# 函数的定义和调用

## 什么是函数？

函数是一段可以重复使用的代码块。它可以：
- 接收输入（参数）
- 处理数据
- 返回结果

使用函数可以让代码更有组织、更容易维护。

## 定义函数

### 基本语法

```claw
// 定义一个简单的函数
func sayHello() {
    print("你好！")
}

// 调用函数
sayHello()
```

### 带参数的函数

```claw
// 带一个参数
func greet(name) {
    print("你好，" + name + "！")
}

greet("张三")  // 输出：你好，张三！
greet("李四")  // 输出：你好，李四！
```

### 带多个参数的函数

```claw
func add(a, b) {
    result = a + b
    print(a + " + " + b + " = " + result)
}

add(3, 5)    // 输出：3 + 5 = 8
add(10, 20)  // 输出：10 + 20 = 30
```

### 带返回值的函数

```claw
func add(a, b) {
    return a + b
}

// 使用返回值
sum = add(3, 5)
print(sum)  // 8

// 直接打印返回值
print(add(10, 20))  // 30
```

## 函数的参数

### 默认参数

```claw
func greet(name, greeting = "你好") {
    print(greeting + "，" + name + "！")
}

greet("张三")           // 你好，张三！
greet("李四", "早上好")  // 早上好，李四！
```

### 可变参数

```claw
func sum(numbers...) {
    total = 0
    for num in numbers {
        total += num
    }
    return total
}

print(sum(1, 2, 3))           // 6
print(sum(1, 2, 3, 4, 5))     // 15
print(sum())                   // 0
```

### 命名参数

```claw
func createUser(name, age, city = "北京") {
    return {
        "name": name,
        "age": age,
        "city": city
    }
}

// 使用命名参数
user = createUser(name = "张三", age = 25)
print(user)
```

## 变量的作用域

### 局部变量

在函数内部定义的变量只在函数内有效：

```claw
func test() {
    localVar = "我是局部变量"
    print(localVar)
}

test()  // 输出：我是局部变量
# print(localVar)  # 错误！无法访问
```

### 全局变量

在函数外部定义的变量全局有效：

```claw
globalVar = "我是全局变量"

func test() {
    print(globalVar)  # 可以访问
}

test()  // 输出：我是全局变量
```

## 函数作为变量

在 OpenCLAW 中，函数可以像变量一样传递：

```claw
func add(a, b) {
    return a + b
}

func multiply(a, b) {
    return a * b
}

// 把函数赋值给变量
operation = add
print(operation(3, 5))  // 8

operation = multiply
print(operation(3, 5))  // 15
```

## 匿名函数

没有名字的函数，常用作回调：

```claw
// 定义匿名函数
double = func(x) {
    return x * 2
}

print(double(5))  // 10

// 作为参数传递
numbers = [1, 2, 3, 4, 5]

result = numbers.map(func(x) {
    return x * 2
})

print(result)  // [2, 4, 6, 8, 10]
```

## 闭包

闭包是指一个函数"记住"了它创建时的环境：

```claw
func createCounter() {
    count = 0

    // 返回一个函数
    return func() {
        count = count + 1
        return count
    }
}

counter1 = createCounter()
counter2 = createCounter()

print(counter1())  // 1
print(counter1())  // 2
print(counter1())  // 3

print(counter2())  // 1
print(counter2())  // 2
```

## 实战示例

### 示例 1：计算器函数

```claw
func calculator(a, b, op) {
    match op {
        "+" => return a + b
        "-" => return a - b
        "*" => return a * b
        "/" => return b != 0 ? a / b : "错误"
        _ => return "未知运算符"
    }
}

print(calculator(10, 5, "+"))  // 15
print(calculator(10, 5, "-"))  // 5
print(calculator(10, 5, "*"))  // 50
print(calculator(10, 5, "/"))  // 2
```

### 示例 2：数组处理函数

```claw
// 找出数组中的最大值
func findMax(numbers) {
    max = numbers[0]
    for num in numbers {
        if num > max {
            max = num
        }
    }
    return max
}

// 过滤数组中的偶数
func filterEven(numbers) {
    result = []
    for num in numbers {
        if num % 2 == 0 {
            result.push(num)
        }
    }
    return result
}

nums = [3, 7, 2, 9, 4, 6]
print(findMax(nums))        // 9
print(filterEven(nums))     // [2, 4, 6]
```

### 示例 3：阶乘函数

```claw
// 递归计算阶乘
func factorial(n) {
    if n <= 1 {
        return 1
    }
    return n * factorial(n - 1)
}

print(factorial(5))   // 120
print(factorial(10))  // 3628800
```

## 小结

本章我们学习了：
1. 函数的定义和调用
2. 函数的参数（默认参数、可变参数、命名参数）
3. 变量的作用域
4. 函数作为变量
5. 匿名函数
6. 闭包
7. 实战示例

---

**上一章**：[控制流语句](./chapter3-control-flow.md)
**下一章**：[模块和包](./chapter4-modules.md)
