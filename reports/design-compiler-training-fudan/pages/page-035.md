# Page 035 - Case Study

![Page 35](../assets/pages/page-035.jpg)

## 页面定位

- **页码**：35/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：区分扇出环境和扇出规则
- **阅读问题**：本页要回答：外部扇出模型和最大扇出规则有什么区别？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文要点

> Case Study
> - An input pin normally has a fanout load of 1, but it can
> have a higher value.
> - The fanout load imposed by a driven cell (U3) is not
> necessarily 1.0. Library developers can assign higher
> fanout loads (for example, 2.0) to model internal cell
> fanout effects.
> - You can also set a fanout load on an output port (OUT1)
> to model external fanout effects.

## 原文解读

本页通过 case study 说明 fanout load 不一定等于连接数量。普通 input pin 的 fanout load 常见为 1，但库开发者可以把某些 cell 的输入 fanout load 设为更高值，用来反映内部电路负担；设计者也可以在 output port 上设置 fanout load 来模拟外部负载。

本页关联的关键对象/命令：本页以概念/图示为主，重点看标题和图中对象关系。

## 我的理解

我的理解是：fanout load 是抽象负载权重，不是简单数引脚。一个输入 pin 可能等价于 2 个或更多单位负载，因此 DC 计算 fanout 时会结合库属性和用户设置。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

做模块级综合时，要把外部 fanout load 和库 cell 自带 fanout load 分开理解；否则会误判为什么某个输出很快超过 max_fanout。

## 本页小结

本页的核心收获：Case Study 这一页应被理解为“区分扇出环境和扇出规则”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 034](page-034.md)
- 下一页：[Page 036](page-036.md)
