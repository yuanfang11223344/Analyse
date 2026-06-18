# Page 004 - Synthesis Is Constraint-Driven

![Page 4](../assets/pages/page-004.jpg)

## 页面定位

- **页码**：4/112
- **所属阶段**：综合总览：约束驱动、路径驱动和库映射
- **本页角色**：执行优化和映射
- **阅读问题**：本页要回答：DC 如何从逻辑表达变成目标库门级实现？
- **前后关系**：先建立全局认知：DC 的输出质量取决于库、约束和路径分析，而不是单纯运行 compile。

## 原文要点

> Synthesis Is Constraint-Driven
> You set the goals (through constraints)
> Design Compiler optimizes the design to meet your goals

## 原文解读

本页直接给出综合的约束驱动本质：用户通过 constraints 设置目标，DC 围绕这些目标优化设计。

本页关联的关键对象/命令：`compile`

## 我的理解

我的理解是：DC 不会自动知道“好设计”是什么，设计者必须用约束把性能、面积、规则边界说清楚。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

约束不清楚时，compile 的结果也没有可评价的标准。

## 本页小结

本页的核心收获：Synthesis Is Constraint-Driven 这一页应被理解为“执行优化和映射”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 003](page-003.md)
- 下一页：[Page 005](page-005.md)
