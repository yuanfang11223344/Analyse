# Page 020 - Design Objects: Schematic Perspective

![Page 20](../assets/pages/page-020.jpg)

## 页面定位

- **页码**：20/112
- **所属阶段**：前端准备：库、读入设计和 DC 对象模型
- **本页角色**：理解 DC 对象模型
- **阅读问题**：本页要回答：DC 命令操作的对象到底是什么？
- **前后关系**：这部分回答“DC 如何认识设计”：库在哪里、RTL 如何读入、对象如何被引用。

## 原文要点

> Design Objects: Schematic Perspective

## 原文解读

本页讲 DC 中的设计对象。Verilog 里的 module、port、net、cell 到 DC 里会变成可查询、可设置属性的对象。

本页关联的关键对象/命令：本页以概念/图示为主，重点看标题和图中对象关系。

## 我的理解

我的理解是：DC 命令的难点不在命令名，而在对象选择。`get_ports`、`get_pins`、`get_cells`、`get_designs` 选错，约束就会落到错误对象上。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

写脚本时每个约束后面都要能回答：这个命令作用于 design、port、pin、net、clock 还是 cell？

## 本页小结

本页的核心收获：Design Objects: Schematic Perspective 这一页应被理解为“理解 DC 对象模型”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 019](page-019.md)
- 下一页：[Page 021](page-021.md)
