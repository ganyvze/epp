---
title: PureEnglish 使用说明
published: 2026-01-02
description: "如何使用 PureEnglish 编写程序"
image: "./cover.jpeg"
tags: ["语法规则"]
category: 说明
draft: false
---

欢迎使用 PureEnglish！这份文档将帮助你学习如何使用这种简单、直观的编程语言。

## 目录
- [快速开始](#快速开始)
- [基础语法](#基础语法)
- [数据类型](#数据类型)
- [运算符](#运算符)
- [控制流](#控制流)
- [函数](#函数)
- [标准库函数](#标准库函数)
- [完整示例](#完整示例)

## 快速开始

### 运行你的第一个程序

1. 确保你已经按照 [构建指南](build.md) 成功构建了 PureEnglish 解释器
2. 创建一个新文件 `hello.epp`，内容如下：

```pureenglish
print "Hello, World!"
```

3. 编译程序：

```bash
pe hello.epp
```

4. 运行程序：

```bash
hello.exe
```

恭喜！你已经运行了第一个 PureEnglish 程序！

## 基础语法

### 注释

使用 `//` 开头添加注释，注释会被解释器忽略：

```pureenglish
// 这是一个注释
print "Hello"  // 这也是注释
```

### 变量

PureEnglish 使用动态类型，变量在第一次赋值时自动创建：

```pureenglish
name = "Alice"
age = 25
price = 19.99
is_student = true
```

变量可以随时改变类型：

```pureenglish
x = 10       note: 整数
x = "hello"  note: 现在是字符串
```

## 数据类型

PureEnglish 支持以下数据类型：

### 整数 (int)
```pureenglish
count = 42
score = -10
```

### 浮点数 (float)
```pureenglish
pi = 3.14159
temperature = -5.5
```

### 字符串 (string)
```pureenglish
greeting = "Hello, World!"
empty = ""
```

### 字符 (char)
```pureenglish
letter = 'A'
digit = '7'
```

### 布尔值 (bool)
```pureenglish
is_active = true
is_done = false
```

## 运算符

### 算术运算符

```pureenglish
a = 10
b = 3

sum = a + b        note: 加法，结果 13
diff = a - b       note: 减法，结果 7
product = a * b    note: 乘法，结果 30
quotient = a / b   note: 除法，结果 3.333...
remainder = a % b  note: 取模，结果 1
```

### 比较运算符

```pureenglish
x = 10
y = 20

x = y              note: 等于（注意：用单等号）
x != y             note: 不等于
x > y              note: 大于
x < y              note: 小于
x >= y             note: 大于等于
x <= y             note: 小于等于
```

### 逻辑运算符

```pureenglish
a = true
b = false

a and b            note: 与，结果 false
a or b             note: 或，结果 true
not a              note: 非，结果 false
```

## 控制流

### if 语句

```pureenglish
age = 18

if age >= 18 then
    print "You are an adult"
end if
```

带 else 的 if 语句：

```pureenglish
score = 85

if score >= 90 then
    print "Grade: A"
else if score >= 80 then
    print "Grade: B"
else if score >= 70 then
    print "Grade: C"
else
    print "Grade: F"
end if
```

### while 循环

```pureenglish
i = 1

while i <= 5 do
    print "Count:", i
    i = i + 1
end while
```

### repeat 循环

重复指定次数：

```pureenglish
repeat 3 times
    print "Hello!"
end repeat
```

### for 循环

范围循环：

```pureenglish
for i from 1 to 5
    print i
end for
```

带步长的 for 循环：

```pureenglish
note: 从 10 倒数到 1
for i from 10 to 1 step -1
    print i
end for
```

## 函数

### 定义函数

使用 `function` 关键字定义函数，`takes` 后面跟参数列表：

```pureenglish
function greet takes name
    print "Hello,", name
end function

function add takes a, b
    return a + b
end function
```

### 调用函数

```pureenglish
greet("Alice")

result = add(5, 3)
print result  note: 输出 8
```

### 完整的函数示例

```pureenglish
function factorial takes n
    if n <= 1 then
        return 1
    else
        return n * factorial(n - 1)
    end if
end function

print factorial(5)  note: 输出 120
```

## 标准库函数

### print

输出内容到控制台：

```pureenglish
print "Hello"
print "The answer is", 42
print 1, 2, 3, 4, 5
```

### input

从控制台获取用户输入：

```pureenglish
input "What's your name?" into name
print "Hello,", name
```

### length

获取字符串长度：

```pureenglish
text = "Hello"
len = length(text)
print len  note: 输出 5
```

### to_number

将字符串转换为数字：

```pureenglish
str = "123"
num = to_number(str)
print num + 1  note: 输出 124
```

### to_string

将数字转换为字符串：

```pureenglish
num = 42
str = to_string(num)
print "Number: " + str
```

### random

生成指定范围内的随机整数：

```pureenglish
note: 生成 1 到 10 之间的随机数
dice = random(1, 10)
print "Random number:", dice
```

### sleep

暂停程序执行指定秒数：

```pureenglish
print "Waiting..."
sleep(2)  note: 等待 2 秒
print "Done!"
```

### exit

退出程序，可指定退出代码：

```pureenglish
exit(0)  note: 正常退出
exit(1)  note: 错误退出
```

## 完整示例

### 示例 1: 简单计算器

```pureenglish
note: 简单的计算器程序

print "PureEnglish Calculator"
print "----------------------"

input "Enter first number: " into a_str
input "Enter operator (+, -, *, /): " into op
input "Enter second number: " into b_str

a = to_number(a_str)
b = to_number(b_str)

if op = "+" then
    result = a + b
else if op = "-" then
    result = a - b
else if op = "*" then
    result = a * b
else if op = "/" then
    result = a / b
else
    print "Unknown operator!"
    exit(1)
end if

print "Result:", result
```

### 示例 2: 猜数字游戏

```pureenglish
note: 猜数字游戏

print "Welcome to Guess the Number!"
print "I'm thinking of a number between 1 and 100"

secret = random(1, 100)
attempts = 0

while true do
    input "Take a guess: " into guess_str
    guess = to_number(guess_str)
    attempts = attempts + 1

    if guess < secret then
        print "Too low!"
    else if guess > secret then
        print "Too high!"
    else
        print "Congratulations! You guessed it in", attempts, "attempts!"
        exit(0)
    end if
end while
```

### 示例 3: 斐波那契数列

```pureenglish
note: 计算斐波那契数列

function fib takes n
    if n <= 1 then
        return n
    else
        return fib(n - 1) + fib(n - 2)
    end if
end function

print "Fibonacci sequence:"
for i from 0 to 10
    print "fib(", i, ") =", fib(i)
end for
```

### 示例 4: 冒泡排序

```pureenglish
note: 冒泡排序算法（使用数组模拟）

print "Bubble Sort Demo"
print "----------------"

note: 我们将使用多个变量来模拟数组
a0 = 64
a1 = 34
a2 = 25
a3 = 12
a4 = 22
a5 = 11
a6 = 90

print "Original array:"
print a0, a1, a2, a3, a4, a5, a6

note: 简化的冒泡排序演示
print "Note: Full array operations require extended features"
print "See examples directory for more complex programs"
```

## 更多示例

下载的源代码包中包含了 10 个完整的示例程序，位于 `examples/` 目录：

1. `01_hello.epp` - Hello World
2. `02_variables.epp` - 变量和数据类型
3. `03_conditionals.epp` - 条件语句
4. `04_loops.epp` - 循环结构
5. `05_functions.epp` - 函数定义和使用
6. `06_calculator.epp` - 简单计算器
7. `07_guess_number.epp` - 猜数字游戏
8. `08_fibonacci.epp` - 斐波那契数列
9. `09_bubble_sort.epp` - 冒泡排序
10. `10_standard_library.epp` - 标准库函数演示

## 下一步

现在你已经了解了 PureEnglish 的基础知识！尝试：
1. 运行 `examples/` 目录下的示例程序
2. 修改示例程序，加入你自己的想法
3. 创建全新的程序！

祝您编程愉快！
