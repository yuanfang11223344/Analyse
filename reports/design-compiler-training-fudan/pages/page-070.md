# Page 070 - Sequential Mapping

![Page 70](../assets/pages/page-070.jpg)

## 页面定位

- **页码**：70/112
- **所属阶段**：综合优化：逻辑优化、映射、compile 与报告
- **本页角色**：执行优化和映射
- **阅读问题**：本页要回答：DC 如何从逻辑表达变成目标库门级实现？
- **前后关系**：这部分回答“DC 如何改变电路”：从布尔级、门级到时序驱动优化。

## 原文要点

> Sequential Mapping
> - Optimize the mapping
> to sequential cells
> from technology
> library.
> - Analyze combinational
> surrounding a
> sequential cell to see if
> it can absorb the logic
> attribute with HDL.
> - Try to save speed and
> area by using a more
> complex sequential
> cell.

## 原文解读

本页讲 sequential mapping。DC 会把时序单元周围的组合逻辑与工艺库中的复杂 sequential cell 做匹配，尝试把部分逻辑吸收到触发器或时序单元中，以节省速度和面积。

本页关联的关键对象/命令：`analyze`

## 我的理解

我的理解是：sequential mapping 不是单纯替换触发器，而是在保持功能等价的前提下，利用库里更复杂的时序单元重构局部逻辑。它体现了 compile 在 gate-level optimization 中的局部优化能力。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

如果 sequential mapping 后网表结构变化明显，要用等价性检查和 timing report 确认功能与时序收益，而不是只看 cell 数减少。

## 本页小结

本页的核心收获：Sequential Mapping 这一页应被理解为“执行优化和映射”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 069](page-069.md)
- 下一页：[Page 071](page-071.md)
