# Page 046 - set_max_transition (ns)

![Page 46](../assets/pages/page-046.jpg)

## 页面定位

- **页码**：46/112
- **所属阶段**：约束建模：设计规则、时序、面积和优先级
- **本页角色**：设置设计规则底线
- **阅读问题**：本页要回答：哪些约束是工艺规则底线，不能为了面积/速度牺牲？
- **前后关系**：这部分回答“工具必须满足什么”：硬性 design rule 与优化目标要分清。

## 原文要点

> set_max_transition (ns)
> - set_max_transition: set the maximum
> transition time for specified clocks, ports, or
> designs.
> set_max_transition 1.5 all_inputs

## 原文解读

本页讲 design rule constraints。max transition、max capacitance、max fanout 这类约束通常来自工艺库限制，优先级高于面积/速度目标。

本页关联的关键对象/命令：`set_max_transition`

## 我的理解

我的理解是：design rule 是“不能违反”的底线，不是优化偏好。DC 会优先修 DRC，即使这让面积变大或局部时序变差。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

报告中若有 transition/cap/fanout violation，先修规则，再讨论 timing/area trade-off。

## 本页小结

本页的核心收获：set_max_transition (ns) 这一页应被理解为“设置设计规则底线”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 045](page-045.md)
- 下一页：[Page 047](page-047.md)
