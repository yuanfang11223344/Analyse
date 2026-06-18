# Page 045 - Design Rule Constraints

![Page 45](../assets/pages/page-045.jpg)

## 页面定位

- **页码**：45/112
- **所属阶段**：约束建模：设计规则、时序、面积和优先级
- **本页角色**：建模输出负载
- **阅读问题**：本页要回答：输出端外部负载如何建模？
- **前后关系**：这部分回答“工具必须满足什么”：硬性 design rule 与优化目标要分清。

## 原文要点

> Design Rule Constraints
> - Design rules can not be violated at any cost, even if it
> will violate the timing and area goal.
> - Rule Constraints Demand:
> - set_max_transition
> - set_max_fanout (explained in last chapter)
> - set_max_capacitance
> - set_cell_degradation
> - set_min_capacitance

## 原文解读

本页讲输出负载建模。`set_load` 给端口或 net 设置电容负载，影响输出 cell sizing、transition 和 delay。

本页关联的关键对象/命令：`set_max_fanout`, `set_max_transition`, `set_max_capacitance`

## 我的理解

我的理解是：输出端连接了外部逻辑，DC 必须知道要推动多重的负载；负载估小会得到乐观时序，估大会增加面积和功耗压力。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

对 output port 写约束时，把 pad、下游输入 pin、电容预算分别核清楚。

## 本页小结

本页的核心收获：Design Rule Constraints 这一页应被理解为“建模输出负载”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 044](page-044.md)
- 下一页：[Page 046](page-046.md)
