# Page 001 - Design Compiler

![Page 1](../assets/pages/page-001.jpg)

## 页面定位

- **页码**：1/112
- **所属阶段**：综合总览：约束驱动、路径驱动和库映射
- **本页角色**：执行优化和映射
- **阅读问题**：本页要回答：DC 如何从逻辑表达变成目标库门级实现？
- **前后关系**：先建立全局认知：DC 的输出质量取决于库、约束和路径分析，而不是单纯运行 compile。

## 原文要点

> Design Compiler
> JoyShockley
> School of Microelectronics
> Fudan University

## 原文解读

本页讲综合优化与映射。逻辑级优化处理布尔结构，gate-level optimization 在目标库单元中选择实现；structure/flatten 会改变中间层次和表达形式。

本页关联的关键对象/命令：`compile`

## 我的理解

我的理解是：compile 是 DC 把约束转化为电路结构变化的核心步骤。`map_effort` 越高，可能带来更长运行时间和更激进的关键路径重综合。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

改 compile 选项前先读 timing/area/report_design，确认瓶颈是在逻辑结构、门级映射还是约束本身。

## 本页小结

本页的核心收获：Design Compiler 这一页应被理解为“执行优化和映射”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：无
- 下一页：[Page 002](page-002.md)
