# 运算符和表达式

## 什么是运算符？

运算符是用于执行各种计算和操作的符号。简单来说，就是数学中的加减乘除之类的符号。

## 算术运算符

### 基本算术运算

```claw
// 加法
a = 10 + 5   // 15

// 减法
b = 10 - 5   // 5

// 乘法
c = 10 * 5   // 50

// 除法
d = 10 / 5   // 2

// 取余（求余数）
e = 10 % 3   // 1

// 幂运算
f = 2 ** 3   // 8
```

### 复合赋值运算符

```claw
num = 10

// 加等于
num += 5     // num = 15

// 减等于
num -= 3     // num = 12

// 乘等于
num *= 2     // num = 24

// 除等于
num /= 4     // num = 6
```

### 自增自减

```claw
num = 10

// 自增 1
num++        // num = 11

// 自减 1
num--        // num = 10
```

## 比较运算符

比较运算符返回布尔值（true 或 false）：

```claw
// 等于
print(5 == 5)      // true

// 不等于
print(5 != 3)      // true

// 大于
print(10 > 5)      // true

// 小于
print(3 < 8)       // true

// 大于等于
print(5 >= 5)      // true

// 小于等于
print(4 <= 3)      // false
```

## 逻辑运算符

用于组合多个条件：

```claw
// 并且（AND）
print(true and true)    // true
print(true and false)   // false

// 或者（OR）
print(true or false)    // true
print(false or false)   // false

// 非（NOT）
print(not true)         // false
print(not false)        // true
```

### 组合示例

```claw
age = 20

// 检查年龄是否在 18 到 60 之间
result = age >= 18 and age <= 60
print(result)  // true

// 检查是否是学生或未成年人
isStudent = true
result2 = isStudent or age < 18
print(result2)  // true
```

## 字符串运算符

```claw
name = "Hello"

// 字符串拼接
greeting = name + " World"
print(greeting)  // Hello World

// 重复字符串
repeated = "ha" * 3
print(repeated)  // hahaha
```

## 三元运算符

根据条件选择不同的值：

```claw
age = 20

// 语法：条件 ? 值1 : 值2
status = age >= 18 ? "成年人" : "未成年人"

print(status)  // 成年人
```

## 运算符优先级

当一个表达式中有多个运算符时，需要知道哪个先执行：

```claw
// 优先级从高到低：
// 1. 括号
// 2. 幂运算
// 3. 乘除取余
// 4. 加减
// 5. 比较运算
// 6. 逻辑运算

// 示例
result = 2 + 3 * 4      // 14（先算乘法）
result2 = (2 + 3) * 4   // 20（先算括号）
```

## 表达式练习

让我们综合练习一下：

```claw
// 练习 1：计算圆的面积
radius = 5
pi = 3.14159
area = pi * radius ** 2
print("圆的面积：" + area)

// 练习 2：判断是否及格
score = 75
isPass = score >= 60
print("是否及格：" + isPass)

// 练习 3：计算总价
price = 99.99
quantity = 3
discount = 0.1  // 10% 折扣

total = price * quantity
finalPrice = total * (1 - discount)

print("原价：" + total)
print("折后价：" + finalPrice)

// 练习 4：条件判断
age = 25
isAdult = age >= 18
isStudent = false

canBuyAlcohol = isAdult and not isStudent
print("可以购买酒类：" + canBuyAlcohol)
```

## 小结

本章我们学习了：
1. 算术运算符（加、减、乘、除、取余、幂）
2. 赋值运算符
3. 比较运算符
4. 逻辑运算符
5. 字符串运算符
6. 三元运算符
7. 运算符优先级

---

**上一章**：[变量和数据类型](./chapter3-variables.md)
**下一章**：[控制流语句](./chapter3-control-flow.md)
