# 第3部分：解释器核心

> 本部分共4章，带你深入CPython的大脑——从.py源文件到字节码执行，理解Python代码是如何被编译和运行的。

---

## 📑 章节导航

| 章节 | 标题 | 你将学到 |
|------|------|---------|
| [第9章](./ch09-bytecode-compiler.md) | 字节码与编译器 | .py → AST → 符号表 → 字节码的完整编译流水线 |
| [第10章](./ch10-ceval-loop.md) | 解释器主循环 | ceval.c的computed goto、Tier 2优化器、计算栈帧 |
| [第11章](./ch11-function-frame.md) | 函数调用与栈帧 | PyFrameObject结构体、调用约定、参数传递、闭包实现 |
| [第12章](./ch12-exception.md) | 异常处理机制 | 异常表、try/except字节码、traceback生成与链式异常 |

---

## 🎯 学习目标

完成本部分后，你将能够：

1. ✅ 使用 `dis` 模块阅读和理解Python字节码
2. ✅ 解释 `ceval.c` 主循环如何分派和执行每条字节码指令
3. ✅ 理解函数调用的栈帧创建和销毁全过程
4. ✅ 掌握Python异常如何在C层面被捕获、匹配和传播

---

## 📐 知识地图

```mermaid
flowchart TD
    SRC[".py 源文件"] --> TOK["词法分析<br/>tokenize.c"]
    TOK --> PARSE["语法分析<br/>Parser/pegen"]
    PARSE --> AST["AST 抽象语法树<br/>Python/ast.c"]
    AST --> SYM["符号表分析<br/>Python/symtable.c"]
    SYM --> COMPILE["代码生成<br/>Python/compile.c"]
    COMPILE --> CODE["PyCodeObject<br/>字节码"]

    CODE --> CEVAL["解释器主循环<br/>Python/ceval.c"]
    CEVAL --> FRAME["PyFrameObject<br/>Python/frameobject.c"]
    FRAME --> EVAL["执行结果"]

    CEVAL --> EXC{"异常?"}
    EXC -->|"是"| EXCH["异常处理<br/>Python/errors.c"]
    EXCH -->|"未捕获"| UNWIND["栈展开<br/>traceback生成"]
    EXCH -->|"已捕获"| CEVAL

    style COMPILE fill:#306998,color:#fff
    style CEVAL fill:#FFD43B,color:#222
    style FRAME fill:#4d8bc9,color:#fff
    style EXC fill:#e74c3c,color:#fff
```

---

## 🔑 Part 3 核心概念速览

| 概念 | C源码位置 | 关键数据结构 |
|------|----------|-------------|
| 字节码 | `Python/compile.c` | `PyCodeObject`, `_Py_CODEUNIT` |
| 主循环 | `Python/ceval.c` | `_PyInterpreterFrame`, `tstate` |
| 栈帧 | `Include/cpython/frameobject.h` | `_PyInterpreterFrame` |
| 异常 | `Python/errors.c` | `PyExceptionTable`, `tstate->curexc_*` |

---

准备好了吗？从 [第9章 · 字节码与编译器](./ch09-bytecode-compiler.md) 开始吧！
