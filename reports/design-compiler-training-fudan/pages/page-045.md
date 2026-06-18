# Page 045 - Design Rule Constraints

![Page 45](../assets/pages/page-045.jpg)

## 页面定位

- **页码**：45/112
- **所属阶段**：约束建模：设计规则、时序、面积和优先级
- **本页角色**：建模输出负载
- **阅读问题**：本页要回答：输出端外部负载如何建模？
- **前后关系**：这部分回答“工具必须满足什么”：硬性 design rule 与优化目标要分清。

## 原文摘录

> Design Rule Constraints
> - Design rules can not be violated at any cost, even if it
> will violate the timing and area goal.
> - Rule Constraints Demand:
> - set_max_transition
> - set_max_fanout (explained in last chapter)
> - set_max_capacitance
> - set_cell_degradation
> - set_min_capacitance

## 页面结构与图示分析

本页主要是文字/命令列表结构。阅读顺序应从标题开始，再看项目符号或命令示例：标题给主题，项目符号给定义和限制，命令示例说明如何在 dc_shell 中落地。

## 原文逐项解读

1. **原文**：`Design Rule Constraints`
   **解读**：这是工艺/库给出的硬性规则。DC 通常会优先修复这些 violation，即使面积或局部时序因此变差。
2. **原文**：`- Design rules can not be violated at any cost, even if it`
   **解读**：这是工艺/库给出的硬性规则。DC 通常会优先修复这些 violation，即使面积或局部时序因此变差。
3. **原文**：`will violate the timing and area goal.`
   **解读**：这是优化目标或优先级。它告诉我们 DC 在多个目标冲突时先满足什么、后优化什么。
4. **原文**：`- Rule Constraints Demand:`
   **解读**：这是标题下的一个子要点，通常在补充定义、适用对象、命令参数或注意事项。读时要把它和本页标题连起来。
5. **原文**：`- set_max_transition`
   **解读**：这是工艺/库给出的硬性规则。DC 通常会优先修复这些 violation，即使面积或局部时序因此变差。
6. **原文**：`- set_max_fanout (explained in last chapter)`
   **解读**：这是设计规则约束。它规定一个驱动点最多能承受多少 fanout，属于 DC 需要优先满足的底线。
7. **原文**：`- set_max_capacitance`
   **解读**：这是输出负载建模。它告诉 DC 输出端要推动多大的电容负载，直接影响输出 cell sizing、transition、delay、面积和功耗。
8. **原文**：`- set_cell_degradation`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
9. **原文**：`- set_min_capacitance`
   **解读**：这是输出负载建模。它告诉 DC 输出端要推动多大的电容负载，直接影响输出 cell sizing、transition、delay、面积和功耗。

## 关键概念拆解

- **相关对象/命令**：`set_max_fanout`, `set_max_transition`, `set_max_capacitance`
- **它在流程中的位置**：本页属于“约束建模：设计规则、时序、面积和优先级”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“建模输出负载”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：这一页属于 design environment。环境建模不是“外围杂项”，而是在告诉 DC 当前模块外部世界长什么样。输入驱动、输出负载、fanout、wire load 和 PVT 会共同决定 delay、transition、cell sizing 与优化压力。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：模块级综合必须主动补全外部世界。不要默认输入是理想驱动、输出没有负载、互连没有延迟；这些偷懒会让时序结果过于乐观。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“Design Rule Constraints”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 044](page-044.md)
- 下一页：[Page 046](page-046.md)
