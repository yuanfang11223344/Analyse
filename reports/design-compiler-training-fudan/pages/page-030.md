# Page 030 - set_fanout_load

![Page 30](../assets/pages/page-030.jpg)

## 页面定位

- **页码**：30/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：区分扇出环境和扇出规则
- **阅读问题**：本页要回答：外部 fanout load 如何影响 max fanout 判断？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文要点

> set_fanout_load
> - You can model the external fanout effects by
> specifying the expected fanout load values on output
> ports with the set_fanout_load command.
> - set_fanout_load 4 {out1}
> - Design Compiler tries to ensure that the sum of the
> fanout load on the output port plus the fanout load of
> cells connected to the output port driver is less than
> the maximum fanout limit of the library, library cell, and
> design.

## 原文解读

本页讲 `set_fanout_load`，用于在 output port 上建模外部 fanout 效应。DC 会把端口上的外部 fanout load 与实际连接 cell 的 fanout load 相加，再和 library/cell/design 上的最大 fanout 限制比较。

本页关联的关键对象/命令：`set_fanout_load`, `compile`

## 我的理解

我的理解是：`set_fanout_load` 不等于电容负载，它是无单位的 fanout 贡献值。它让模块级综合时也能考虑模块外部的扇出压力。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

如果 report 中出现 max fanout 问题，要同时检查外部 `set_fanout_load` 和内部连接 cell 的 fanout load。

## 本页小结

本页的核心收获：set_fanout_load 这一页应被理解为“区分扇出环境和扇出规则”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 029](page-029.md)
- 下一页：[Page 031](page-031.md)
