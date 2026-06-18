# Page 068 - Gate Level Optimization

![Page 68](../assets/pages/page-068.jpg)

## 页面定位

- **页码**：68/112
- **所属阶段**：综合优化：逻辑优化、映射、compile 与报告
- **本页角色**：设置设计规则底线
- **阅读问题**：本页要回答：哪些约束是工艺规则底线，不能为了面积/速度牺牲？
- **前后关系**：这部分回答“DC 如何改变电路”：从布尔级、门级到时序驱动优化。

## 原文要点

> Gate Level Optimization
> - Select components to meet timing, design rule
> & area goals specified for the circuit.
> - Has a local effect on the area/speed
> characteristic of a design.
> - Strategy: combinational mapping & sequential
> mapping.

## 原文解读

本页讲 design rule constraints。max transition、max capacitance、max fanout 这类约束通常来自工艺库限制，优先级高于面积/速度目标。

本页关联的关键对象/命令：本页以概念/图示为主，重点看标题和图中对象关系。

## 我的理解

我的理解是：design rule 是“不能违反”的底线，不是优化偏好。DC 会优先修 DRC，即使这让面积变大或局部时序变差。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

报告中若有 transition/cap/fanout violation，先修规则，再讨论 timing/area trade-off。

## 本页小结

本页的核心收获：Gate Level Optimization 这一页应被理解为“设置设计规则底线”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 067](page-067.md)
- 下一页：[Page 069](page-069.md)
