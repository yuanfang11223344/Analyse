# Page 034 - Case Study: fanout_load & max_fanout_load

![Page 34](../assets/pages/page-034.jpg)

## 页面定位

- **页码**：34/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：区分扇出环境和扇出规则
- **阅读问题**：本页要回答：外部扇出模型和最大扇出规则有什么区别？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文要点

> Case Study: fanout_load & max_fanout_load
> >>set_fanout_load 3.0 OUT1
> >>set_max_fanout 8 [get_designs ADDER]

## 原文解读

本页讲 fanout load 与 max fanout。`set_fanout_load` 是环境建模，描述外部扇出贡献；`set_max_fanout` 是设计规则约束，限制可接受的最大扇出。

本页关联的关键对象/命令：`set_fanout_load`, `set_max_fanout`

## 我的理解

我的理解是：前者告诉 DC “外面接了多少负担”，后者告诉 DC “最多允许多大扇出”。二者数值长得像，但语义完全不同。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

debug fanout violation 时先分清是外部模型导致，还是 design rule 限制导致。

## 本页小结

本页的核心收获：Case Study: fanout_load & max_fanout_load 这一页应被理解为“区分扇出环境和扇出规则”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 033](page-033.md)
- 下一页：[Page 035](page-035.md)
