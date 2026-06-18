# Page 017 - Example

![Page 17](../assets/pages/page-017.jpg)

## 页面定位

- **页码**：17/112
- **所属阶段**：前端准备：库、读入设计和 DC 对象模型
- **本页角色**：读入并建立设计层次
- **阅读问题**：本页要回答：RTL 如何进入 DC 数据库，设计层次如何建立？
- **前后关系**：这部分回答“DC 如何认识设计”：库在哪里、RTL 如何读入、对象如何被引用。

## 原文要点

> Example
> 1 dc_shell-t> read_verilog top.v
> dc_shell-t> read_verilog sub_design.v
> dc_shell-t> current_design top
> dc_shell-t> link
> 2 dc_shell-t> analyze -f verilog sub_design.v
> dc_shell-t> elaborate sub_design
> dc_shell-t> analyze -f verilog top.v
> dc_shell-t> elaborate top
> dc_shell-t> current_design top
> dc_shell-t> link
> 2 is preferred!

## 原文解读

本页讲 DC 如何读入设计。`read/read_verilog/read_vhdl` 是直接读入文件；`analyze + elaborate` 更强调先分析 HDL，再建立层次和布尔函数。

本页关联的关键对象/命令：`read_verilog`, `analyze`, `elaborate`, `dc_shell`

## 我的理解

我的理解是：读设计不是“打开文件”，而是把 RTL 转换为 DC 内部 design database。复杂工程中，能否清楚地 current_design、link 和定位 instance，取决于这个阶段是否干净。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

读入后应检查 `current_design`、unresolved references 和 hierarchy，避免带着未解析模块进入 compile。

## 本页小结

本页的核心收获：Example 这一页应被理解为“读入并建立设计层次”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 016](page-016.md)
- 下一页：[Page 018](page-018.md)
