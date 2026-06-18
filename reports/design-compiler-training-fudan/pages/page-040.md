# Page 040 - Hierarchical Wire Load Models

![Page 40](../assets/pages/page-040.jpg)

## 页面定位

- **页码**：40/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：估计互连延迟
- **阅读问题**：本页要回答：没有布局布线时，DC 如何估计 net delay？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文摘录

> Hierarchical Wire Load Models
> - Enclose: DC uses the wire load model of the smallest design that
> fully encloseds the net. If the design enclosing the net has no wire load
> model, the tool traverses the design hierearchy upward until it finds a wire
> load model. Enclosed mode is more accurate than top mode when cells in
> the same design are placed in a contiguous region during layout.
> - Segmented: DC determines the wire load models of each segment of
> a net by the design encompassing the segment. Nets crossing hierarchical
> boundaries are divided into segments.

## 图中内容理解

这页内容代表设计环境建模。图中或命令表达的是模块外部世界：上游驱动能力、下游电容负载、外部 fanout、PVT 条件或互连 RC 估计。它们会改变 cell delay、transition、buffer 插入和 sizing 选择。

## 原文逐项解读

1. **原文**：`Hierarchical Wire Load Models`
   **解读**：这是综合阶段对互连 RC 的估计。布局布线前没有真实寄生参数，DC 只能用 wire load model 和层次模式来估 net delay。
2. **原文**：`- Enclose: DC uses the wire load model of the smallest design that`
   **解读**：这是综合阶段对互连 RC 的估计。布局布线前没有真实寄生参数，DC 只能用 wire load model 和层次模式来估 net delay。
3. **原文**：`fully encloseds the net. If the design enclosing the net has no wire load`
   **解读**：这是综合阶段对互连 RC 的估计。布局布线前没有真实寄生参数，DC 只能用 wire load model 和层次模式来估 net delay。
4. **原文**：`model, the tool traverses the design hierearchy upward until it finds a wire`
   **解读**：这句话给出本页概念的定义、条件或结论。理解时要把主语、动作和作用对象拆开：谁被设置、什么属性被改变、后续哪类优化或报告会受影响。
5. **原文**：`load model. Enclosed mode is more accurate than top mode when cells in`
   **解读**：这是综合阶段对互连 RC 的估计。布局布线前没有真实寄生参数，DC 只能用 wire load model 和层次模式来估 net delay。
6. **原文**：`the same design are placed in a contiguous region during layout.`
   **解读**：这句话给出本页概念的定义、条件或结论。理解时要把主语、动作和作用对象拆开：谁被设置、什么属性被改变、后续哪类优化或报告会受影响。
7. **原文**：`- Segmented: DC determines the wire load models of each segment of`
   **解读**：这是综合阶段对互连 RC 的估计。布局布线前没有真实寄生参数，DC 只能用 wire load model 和层次模式来估 net delay。
8. **原文**：`a net by the design encompassing the segment. Nets crossing hierarchical`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
9. **原文**：`boundaries are divided into segments.`
   **解读**：这句话给出本页概念的定义、条件或结论。理解时要把主语、动作和作用对象拆开：谁被设置、什么属性被改变、后续哪类优化或报告会受影响。

## 关键概念拆解

- **相关对象/命令**：本页以概念、结构或图示关系为主，没有需要死记的单一命令。
- **它在流程中的位置**：本页属于“设计环境建模：工艺、负载、扇出和线负载”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“估计互连延迟”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：这一页属于 design environment。环境建模不是“外围杂项”，而是在告诉 DC 当前模块外部世界长什么样。输入驱动、输出负载、fanout、wire load 和 PVT 会共同决定 delay、transition、cell sizing 与优化压力。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：模块级综合必须主动补全外部世界。不要默认输入是理想驱动、输出没有负载、互连没有延迟；这些偷懒会让时序结果过于乐观。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“Hierarchical Wire Load Models”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 039](page-039.md)
- 下一页：[Page 041](page-041.md)
