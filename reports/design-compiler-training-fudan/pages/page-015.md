# Page 015 - Read Design

![Page 15](../assets/pages/page-015.jpg)

## 页面定位

- **页码**：15/112
- **所属阶段**：前端准备：库、读入设计和 DC 对象模型
- **本页角色**：读入并建立设计层次
- **阅读问题**：本页要回答：RTL 如何进入 DC 数据库，设计层次如何建立？
- **前后关系**：这部分回答“DC 如何认识设计”：库在哪里、RTL 如何读入、对象如何被引用。

## 原文要点

> Read Design
>  step1: read, read_verilog, read_vhdl
> 或 analyze + elaborate (analyze HDL
> code and establish Boolean functions)
> - Difference?
> - step2: link (resolve design reference)
> - step3: uniquify (removes multiply-instantiated
> hierarchy in the current design by creating
> a unique design for each cell instance)

## 原文解读

本页讲 DC 如何读入设计。`read/read_verilog/read_vhdl` 是直接读入文件；`analyze + elaborate` 更强调先分析 HDL，再建立层次和布尔函数。

本页关联的关键对象/命令：`read_verilog`, `analyze`, `elaborate`

## 我的理解

我的理解是：读设计不是“打开文件”，而是把 RTL 转换为 DC 内部 design database。复杂工程中，能否清楚地 current_design、link 和定位 instance，取决于这个阶段是否干净。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

读入后应检查 `current_design`、unresolved references 和 hierarchy，避免带着未解析模块进入 compile。

## 本页小结

本页的核心收获：Read Design 这一页应被理解为“读入并建立设计层次”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 014](page-014.md)
- 下一页：[Page 016](page-016.md)
