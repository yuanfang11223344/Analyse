# Page 052 - Optimization Constraints

![Page 52](../assets/pages/page-052.jpg)

## 页面定位

- **页码**：52/112
- **所属阶段**：约束建模：设计规则、时序、面积和优先级
- **本页角色**：理解优化目标和优先级
- **阅读问题**：本页要回答：这个概念/命令在流程中解决什么问题？
- **前后关系**：这部分回答“工具必须满足什么”：硬性 design rule 与优化目标要分清。

## 原文要点

> Optimization Constraints
> The optimization constraints comprise
> -Timing constraints (performance and
> speed)
> -Input and output delays (synchronous paths)
> -Minimum and maximum delay (asynchronous
> paths)
> -Maximum area (number of gates)

## 原文解读

本页讲 area constraint 和约束优先级。DC 优化时会按优先级处理：设计规则约束优先，其次是时序，再到面积等目标。

本页关联的关键对象/命令：本页以概念/图示为主，重点看标题和图中对象关系。

## 我的理解

我的理解是：面积约束不是孤立目标，它总是在 DRC 和 timing 之后被权衡。若时序很紧，面积增长往往是工具换取速度的代价。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

看 compile 结果时，不要只看 area 是否下降，也要同时确认 DRC 和 timing 是否已经满足。

## 本页小结

本页的核心收获：Optimization Constraints 这一页应被理解为“理解优化目标和优先级”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 051](page-051.md)
- 下一页：[Page 053](page-053.md)
