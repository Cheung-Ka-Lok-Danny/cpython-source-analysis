# 关于本项目

> 深度剖析CPython · 从源码层面彻底掌握Python

---

## 项目简介

《Python源码解析》是一本开源的CPython源码分析教程，旨在帮助Python开发者**从C源码层面**理解Python的内部工作原理。

我们不仅解释"Python怎么做"，更深入探究"CPython为什么这样做"。

---

## 为什么读CPython源码？

1. **写出更高效的Python代码** — 理解int/list/dict的内存布局，避免性能陷阱
2. **驾驭高级特性** — 元类、协程、GIL不再是黑魔法
3. **提升工程能力** — 学习大型C项目的架构设计和编码风格
4. **参与开源贡献** — 为CPython贡献代码的必备知识

---

## 源码版本

本书基于 **CPython 3.12.x** 进行源码分析。CPython 3.12是Python的重要版本，引入了多项优化：

- PEP 684: Per-Interpreter GIL
- PEP 669: 低开销监控
- PEP 701: f-string语法改进
- Tier 2 优化器（ specializing adaptive interpreter）

---

## 目标读者

- 有2年以上Python开发经验的工程师
- 想要深入理解Python内部机制的中高级开发者
- 准备为CPython贡献代码的开源爱好者
- 对编程语言实现感兴趣的学生和研究者

**前置知识**：熟悉Python语法、了解C语言基础。

---

## 内容结构

| Part | 章节 | 主题 |
|------|------|------|
| 第1部分 | 第1-3章 | CPython基础：概述、源码结构、对象模型 |
| 第2部分 | 第4-8章 | 核心对象：PyObject、int、list、dict、str |
| 第3部分 | 第9-12章 | 解释器核心：字节码、ceval、栈帧、异常 |
| 第4部分 | 第13-15章 | 内存管理：pymalloc、GIL、GC |
| 第5部分 | 第16-18章 | 高级主题：import、类型系统、协程 |

---

## 贡献指南

欢迎通过以下方式贡献：

- **报告问题**: 发现错误或不清楚的地方，提交Issue
- **改进内容**: 提交PR修正错误或补充内容
- **新增章节**: 提出你感兴趣的新主题

---

## 开源许可

本项目采用 [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) 许可。

---

## 致谢

本项目深受以下资源的启发：
- [CPython官方源码](https://github.com/python/cpython)
- [Python官方文档](https://docs.python.org/3/)
- [Fluent Python (2nd Edition)](https://www.oreilly.com/library/view/fluent-python-2nd/9781492056348/)
- [CPython Internals](https://realpython.com/products/cpython-internals-book/)
