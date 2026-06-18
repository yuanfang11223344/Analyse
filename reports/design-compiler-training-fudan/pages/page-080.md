# Page 080 - Path Delay Calculation

![Page 80](../assets/pages/page-080.jpg)

## 页面定位

- **页码**：80/112
- **所属阶段**：STA 与时序报告：路径、clock model、I/O 约束和 slack
- **本页角色**：估计互连延迟
- **阅读问题**：本页要回答：没有布局布线时，DC 如何估计 net delay？
- **前后关系**：这部分回答“如何判断结果是否真的满足时序”：看路径、看 required/arrival、看 slack。

## 原文要点

> Path Delay Calculation
> - To calculate total delay, each path is broken into timing arcs.
> - Each timing arc contributes either a net delay or cell delay
> - All the net and cell timing arcs along the path are added
> together.

## 原文解读

本页讲 wire load/net delay。早期综合没有真实布局布线，只能用 wire load model 按 fanout 和层次估计互连 RC。

本页关联的关键对象/命令：本页以概念/图示为主，重点看标题和图中对象关系。

## 我的理解

我的理解是：线延迟是综合阶段最大的近似之一。top/enclosed/segmented 模式不同，会改变跨层级 net 采用哪个 wire load model。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

层次设计里要特别检查跨 boundary net；wire load mode 选择会影响时序乐观/悲观程度。

## 本页小结

本页的核心收获：Path Delay Calculation 这一页应被理解为“估计互连延迟”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 079](page-079.md)
- 下一页：[Page 081](page-081.md)
