# Page 031 - set_load V.S. set_fanout_load

![Page 31](../assets/pages/page-031.jpg)

## 页面定位

- **页码**：31/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：区分扇出环境和电容负载
- **阅读问题**：本页要回答：`set_load` 和 `set_fanout_load` 为什么不是一回事？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文摘录

> set_load V.S. set_fanout_load
> - fanout load is not the same as load.
> - fanout load is a unitless value that represents a
> numerical contribution to the total fanout. Load is a
> capacitance value.
> - Design Compiler uses fanout load primarily to measure
> the fanout presented by each input pin. An input pin
> normally has a fanout load of 1, but it can have a
> higher value.

## 图中内容理解

这页内容代表设计环境建模。图中或命令表达的是模块外部世界：上游驱动能力、下游电容负载、外部 fanout、PVT 条件或互连 RC 估计。它们会改变 cell delay、transition、buffer 插入和 sizing 选择。

## 原文逐项解读

1. **原文**：`set_load V.S. set_fanout_load`
   **解读**：这是输出负载建模。它告诉 DC 输出端要推动多大的电容负载，直接影响输出 cell sizing、transition、delay、面积和功耗。
2. **原文**：`- fanout load is not the same as load.`
   **解读**：这是外部 fanout 环境建模。它不是电容，而是无单位的扇出贡献值，用来补充模块外部的扇出压力。
3. **原文**：`- fanout load is a unitless value that represents a`
   **解读**：这是外部 fanout 环境建模。它不是电容，而是无单位的扇出贡献值，用来补充模块外部的扇出压力。
4. **原文**：`numerical contribution to the total fanout. Load is a`
   **解读**：这句话给出本页概念的定义、条件或结论。理解时要把主语、动作和作用对象拆开：谁被设置、什么属性被改变、后续哪类优化或报告会受影响。
5. **原文**：`capacitance value.`
   **解读**：这是输出负载建模。它告诉 DC 输出端要推动多大的电容负载，直接影响输出 cell sizing、transition、delay、面积和功耗。
6. **原文**：`- Design Compiler uses fanout load primarily to measure`
   **解读**：这是外部 fanout 环境建模。它不是电容，而是无单位的扇出贡献值，用来补充模块外部的扇出压力。
7. **原文**：`the fanout presented by each input pin. An input pin`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
8. **原文**：`normally has a fanout load of 1, but it can have a`
   **解读**：这是外部 fanout 环境建模。它不是电容，而是无单位的扇出贡献值，用来补充模块外部的扇出压力。
9. **原文**：`higher value.`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。

## 关键概念拆解

- **相关对象/命令**：`set_load`, `set_fanout_load`, `compile`
- **它在流程中的位置**：本页属于“设计环境建模：工艺、负载、扇出和线负载”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“区分扇出环境和电容负载”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：这一页属于 design environment。环境建模不是“外围杂项”，而是在告诉 DC 当前模块外部世界长什么样。输入驱动、输出负载、fanout、wire load 和 PVT 会共同决定 delay、transition、cell sizing 与优化压力。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：模块级综合必须主动补全外部世界。不要默认输入是理想驱动、输出没有负载、互连没有延迟；这些偷懒会让时序结果过于乐观。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“set_load V.S. set_fanout_load”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 030](page-030.md)
- 下一页：[Page 032](page-032.md)
