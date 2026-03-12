# 控制流语句

## 什么是控制流？

控制流决定了程序执行的顺序。通过控制流语句，我们可以：
- 根据条件选择执行不同的代码
- 重复执行某段代码
- 提前退出或跳过某些代码

## 条件判断：if 语句

### 基本语法

```claw
// 简单 if
age = 18

if age >= 18 {
    print("你已经成年了！")
}
```

### if-else

```claw
score = 75

if score >= 60 {
    print("及格了！")
} else {
    print("需要继续努力！")
}
```

### if-else if-else

```claw
score = 85

if score >= 90 {
    print("优秀")
} else if score >= 80 {
    print("良好")
} else if score >= 60 {
    print("及格")
} else {
    print("需要努力")
}
```

### 嵌套 if

```claw
age = 25
hasLicense = true

if age >= 18 {
    if hasLicense {
        print("可以开车")
    } else {
        print("需要考驾照")
    }
} else {
    print("年龄不够，不能开车")
}
```

## 多条件判断：match 语句

当有多个条件时，match 语句比 if-else if 更清晰：

```claw
// 简单 match
day = 3

match day {
    1 => print("星期一")
    2 => print("星期二")
    3 => print("星期三")
    4 => print("星期四")
    5 => print("星期五")
    6, 7 => print("周末")
    _ => print("无效的日期")
}
```

### 带条件的 match

```claw
score = 85

match {
    score >= 90 => print("优秀")
    score >= 80 => print("良好")
    score >= 60 => print("及格")
    _ => print("不及格")
}
```

## 循环：for 循环

### 基本 for 循环

```claw
// 打印 1 到 5
for i = 1; i <= 5; i++ {
    print(i)
}
```

解释：
- `i = 1`：初始化计数器
- `i <= 5`：循环条件
- `i++`：每次循环后更新计数器

### 遍历数组

```claw
fruits = ["苹果", "香蕉", "橙子"]

for i = 0; i < fruits.length; i++ {
    print(fruits[i])
}
```

### 简化的 for-in 循环

```claw
fruits = ["苹果", "香蕉", "橙子"]

for fruit in fruits {
    print(fruit)
}
```

## 循环：while 循环

### 基本 while

```claw
count = 1

while count <= 5 {
    print(count)
    count++
}
```

### do-while（保证至少执行一次）

```claw
num = 1

do {
    print(num)
    num++
} while num <= 5
```

## 循环控制：break 和 continue

### break - 提前退出循环

```claw
// 找到第一个能被 3 整除的数
for i = 1; i <= 10; i++ {
    if i % 3 == 0 {
        print("找到：" + i)
        break  // 退出循环
    }
}
```

### continue - 跳过本次循环

```claw
// 打印 1-10 中的偶数
for i = 1; i <= 10; i++ {
    if i % 2 != 0 {
        continue  // 跳过奇数
    }
    print(i)
}
```

## 实战示例

### 示例 1：计算阶乘

```claw
// 计算 5 的阶乘
n = 5
result = 1

for i = 1; i <= n; i++ {
    result = result * i
}

print(n + " 的阶乘是：" + result)
```

### 示例 2：猜数字游戏

```claw
import claw.io

target = 7
guess = 0
attempts = 0

print("猜数字游戏！请猜一个 1-10 之间的数字")

while guess != target {
    print("请输入你的猜测：")
    input = io.input()
    guess = input.toNumber()
    attempts++

    if guess > target {
        print("太大了！")
    } else if guess < target {
        print("太小了！")
    } else {
        print("恭喜你猜对了！")
        print("你用了 " + attempts + " 次猜测")
    }
}
```

### 示例 3：九九乘法表

```claw
for i = 1; i <= 9; i++ {
    line = ""
    for j = 1; j <= i; j++ {
        result = i * j
        line = line + j + "x" + i + "=" + result + " "
    }
    print(line)
}
```

输出：
```
1x1=1
1x2=2 2x2=4
1x3=3 2x3=6 3x3=9
...
```

## 小结

本章我们学习了：
1. if 条件判断语句
2. match 多条件匹配
3. for 循环
4. while 循环
5. break 和 continue 控制循环
6. 综合实战示例

---

**上一章**：[运算符和表达式](./chapter3-operators.md)
**下一章**：[函数的定义和调用](./chapter4-functions.md)
