# Page 031 - set_load V.S. set_fanout_load

![Page 31](../assets/pages/page-031.jpg)

## 页面定位

- **页码**：31/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：建模输出负载
- **阅读问题**：本页要回答：输出端外部负载如何建模？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文要点

> set_load V.S. set_fanout_load
> - fanout load is not the same as load.
> - fanout load is a unitless value that represents a
> numerical contribution to the total fanout. Load is a
> capacitance value.
> - Design Compiler uses fanout load primarily to measure
> the fanout presented by each input pin. An input pin
> normally has a fanout load of 1, but it can have a
> higher value.

## 原文解读

本页讲输出负载建模。`set_load` 给端口或 net 设置电容负载，影响输出 cell sizing、transition 和 delay。

本页关联的关键对象/命令：`set_load`, `set_fanout_load`, `compile`

## 我的理解

我的理解是：输出端连接了外部逻辑，DC 必须知道要推动多重的负载；负载估小会得到乐观时序，估大会增加面积和功耗压力。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

对 output port 写约束时，把 pad、下游输入 pin、电容预算分别核清楚。

## 本页小结

本页的核心收获：set_load V.S. set_fanout_load 这一页应被理解为“建模输出负载”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 030](page-030.md)
- 下一页：[Page 032](page-032.md)
