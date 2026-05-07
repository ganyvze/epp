---
title: PureEnglish 构建指南
published: 2026-01-01
description: "如何构建 PureEnglish 源代码"
image: "./cover.jpeg"
tags: ["构建"]
category: 指南
draft: false
---

# PureEnglish 构建指南

本指南将帮助你从源代码构建 PureEnglish 解释器。

## 前置要求

在开始之前，请确保你的系统满足以下要求：

- **操作系统**：Windows（推荐）、Linux 或 macOS
- **C++ 编译器**：支持 C++17 标准的编译器
  - Windows：MinGW、MSVC 或 Clang
  - Linux：GCC 7+ 或 Clang 5+
  - macOS：Xcode Command Line Tools
- **CMake**（可选）：用于使用 CMake 构建系统

## 项目结构

PureEnglish 项目结构如下：

```
epp/
├── include/          # 头文件
│   ├── Token.h      # 词法单元定义
│   ├── Lexer.h      # 词法分析器
│   ├── AST.h        # 抽象语法树
│   ├── Parser.h     # 语法分析器
│   └── Interpreter.h# 解释器
├── src/
│   └── main.cpp     # 主程序入口
├── examples/        # 示例程序
├── CMakeLists.txt   # CMake 配置文件
└── build.bat        # Windows 构建脚本
```

## 构建方法

### 方法一：使用 Windows 批处理脚本（最简单）

如果你在 Windows 上，可以直接使用提供的 `build.bat` 脚本：

1. 打开命令提示符（cmd）或 PowerShell
2. 导航到项目目录
3. 运行构建脚本：

```bash
build.bat
```

这将自动编译项目并生成 `pe.exe` 可执行文件。

### 方法二：使用 g++ 直接编译

使用 g++ 编译器直接编译源文件：

```bash
g++ -std=c++17 -I include -o pe.exe src/main.cpp
```

参数说明：
- `-std=c++17`：使用 C++17 标准
- `-I include`：添加 `include` 目录到头文件搜索路径
- `-o pe.exe`：指定输出文件名为 `pe.exe`
- `src/main.cpp`：源文件

### 方法三：使用 CMake 构建

如果你想使用 CMake 构建系统：

1. 创建构建目录：
```bash
mkdir build
cd build
```

2. 生成构建文件：
```bash
cmake ..
```

3. 编译项目：
```bash
cmake --build .
```

## 验证安装

构建完成后，你可以通过运行示例程序来验证：

```bash
pe.exe examples/01_hello.epp
```

如果看到输出 "Hello, World!"，说明构建成功！

## 常见问题

### Q: 编译时找不到头文件怎么办？
A: 确保你在正确的目录中运行命令，并且使用了 `-I include` 参数。

### Q: 提示 "g++ 不是内部或外部命令"？
A: 你需要安装 MinGW 或其他 C++ 编译器，并将其添加到系统 PATH 环境变量中。

### Q: 如何在 Linux/macOS 上构建？
A: 在 Linux/macOS 上，你可以使用相同的 g++ 命令，但输出文件名可能需要改为 `./pe` 而不是 `pe.exe`。

## 下一步

构建完成后，请查看 [使用说明](usage.md) 学习如何编写和运行 PureEnglish 程序。
