# 变量和数据类型

## 什么是变量？

变量就像一个盒子，用来存储数据。我们可以给这个盒子起个名字，方便以后使用。

```claw
// 创建一个名为 "name" 的盒子，放入内容 "张三"
name = "张三"

// 创建一个名为 "age" 的盒子，放入数字 25
age = 25
```

## 变量的命名规则

变量名可以包含：
- 字母（a-z, A-Z）
- 数字（0-9），但不能开头
- 下划线（_）

**正确的命名**：
```claw
name = "张三"
age25 = 25
my_name = "李四"
_name = "王五"
```

**错误的命名**：
```claw
# 不能以数字开头
# 25age = 25  # 错误！

# 不能包含特殊字符
# my-name = "赵六"  # 错误！

# 不能使用保留字
# if = 1  # 错误！
```

**建议的命名方式**：
- 使用有意义的英文单词
- 多个单词用下划线分隔：`student_name`
- 或者用驼峰命名：`studentName`

## 基本数据类型

OpenCLAW 有以下几种基本数据类型：

### 1. 字符串（String）

用双引号或单引号括起来的文本：

```claw
name = "张三"
message = '你好，世界！'

// 字符串拼接
greeting = "你好，" + name
print(greeting)  // 输出：你好，张三
```

### 2. 数字（Number）

整数和浮点数：

```claw
// 整数
count = 100
age = 25

// 浮点数
price = 19.99
pi = 3.14159
```

### 3. 布尔值（Boolean）

表示真或假：

```claw
isStudent = true
isAdult = false
```

### 4. 数组（Array）

存储多个值的有序列表：

```claw
// 创建数组
fruits = ["苹果", "香蕉", "橙子"]

// 访问元素（从 0 开始）
print(fruits[0])  // 苹果
print(fruits[1])  // 香蕉
print(fruits[2])  // 橙子

// 获取数组长度
print(fruits.length)  // 3
```

### 5. 字典（Dictionary）

存储键值对：

```claw
// 创建字典
person = {
    "name": "张三",
    "age": 25,
    "city": "北京"
}

// 访问值
print(person["name"])  // 张三
print(person["age"])   // 25

// 也可以用点语法（部分版本支持）
print(person.name)     // 张三
```

### 6. 空值（Null）

表示没有值：

```claw
nothing = null
print(nothing)  // null
```

## 数据类型转换

有时需要把一种数据类型转换成另一种：

```claw
// 字符串转数字
num = "123".toNumber()
print(num + 1)  // 124

// 数字转字符串
str = 123.toString()
print(str + "abc")  // 123abc

// 转布尔值
bool1 = "true".toBoolean()
bool2 = 0.toBoolean()
print(bool1)  // true
print(bool2)  // false
```

## 查看数据类型

使用 `type()` 函数查看数据类型：

```claw
print(type("你好"))    // string
print(type(123))       // number
print(type(true))     // boolean
print(type([1, 2, 3])) // array
print(type({"a": 1})) // object
print(type(null))     // null
```

## 常量

如果数据不应该被修改，可以使用常量：

```claw
// 定义常量
PI = 3.14159
MAX_SIZE = 100

// 尝试修改常量会报错
# PI = 3.14  // 错误！
```

## 小结

本章我们学习了：
1. 变量的概念和命名规则
2. 六种基本数据类型：字符串、数字、布尔值、数组、字典、空值
3. 数据类型之间的转换
4. 如何查看数据类型

---

**上一章**：[运行第一个程序](./chapter2-hello-world.md)
**下一章**：[运算符和表达式](./chapter3-operators.md)
