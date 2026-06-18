# Page 033 - set_fanout_load V.S. set_max_fanout

![Page 33](../assets/pages/page-033.jpg)

## 页面定位

- **页码**：33/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：区分扇出环境和扇出规则
- **阅读问题**：本页要回答：外部扇出模型和最大扇出规则有什么区别？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文要点

> set_fanout_load V.S. set_max_fanout
> - set_fanout_load is design envoronment;
> set_max_fanout is a design constraint.
> - Design Compiler models fanout restrictions by
> associating a fanout_load attribute with each input pin
> and a max_fanout attribute with each output (driving)
> pin on a cell.
> - Design Compiler tries to ensure that the sum of the
> fanout load on the output port plus the fanout load of
> cells connected to the output port driver is less than
> the maximum fanout limit of the library, library cell, and
> design.

## 原文解读

本页明确区分 `set_fanout_load` 和 `set_max_fanout`：前者是 design environment，用来描述输出端口外部扇出负担；后者是 design constraint，用来限制驱动端允许看到的最大 fanout。DC 会把输出端口外部 fanout load 和所连接 cell 的 fanout load 累加，再与库、cell 或 design 上的 max fanout 限制比较。

本页关联的关键对象/命令：`set_fanout_load`, `set_max_fanout`, `compile`

## 我的理解

我的理解是：这页最重要的是语义区分。`set_fanout_load` 是告诉工具“外面有多少负载”，`set_max_fanout` 是告诉工具“最多允许多少负载”。两者都会影响优化，但一个是环境假设，一个是硬性规则。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

检查 fanout 问题时，先确认 violation 来自外部建模还是 max_fanout 规则，不要用改环境模型来掩盖真实设计规则问题。

## 本页小结

本页的核心收获：set_fanout_load V.S. set_max_fanout 这一页应被理解为“区分扇出环境和扇出规则”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 032](page-032.md)
- 下一页：[Page 034](page-034.md)
