# Page 052 - Optimization Constraints

![Page 52](../assets/pages/page-052.jpg)

## 页面定位

- **页码**：52/112
- **所属阶段**：约束建模：设计规则、时序、面积和优先级
- **本页角色**：理解优化目标和优先级
- **阅读问题**：本页要回答：这个概念/命令在流程中解决什么问题？
- **前后关系**：这部分回答“工具必须满足什么”：硬性 design rule 与优化目标要分清。

## 原文摘录

> Optimization Constraints
> The optimization constraints comprise
> -Timing constraints (performance and
> speed)
> -Input and output delays (synchronous paths)
> -Minimum and maximum delay (asynchronous
> paths)
> -Maximum area (number of gates)

## 图中内容理解

这页内容代表约束模型。图中或命令表达的不是电路功能，而是 DC 必须满足的边界条件：哪些是硬性 design rule，哪些是 timing budget，哪些是面积/速度目标。综合时电路结构会围绕这些目标被重写。

## 原文逐项解读

1. **原文**：`Optimization Constraints`
   **解读**：这是优化目标或优先级。它告诉我们 DC 在多个目标冲突时先满足什么、后优化什么。
2. **原文**：`The optimization constraints comprise`
   **解读**：这是优化目标或优先级。它告诉我们 DC 在多个目标冲突时先满足什么、后优化什么。
3. **原文**：`-Timing constraints (performance and`
   **解读**：这是标题下的一个子要点，通常在补充定义、适用对象、命令参数或注意事项。读时要把它和本页标题连起来。
4. **原文**：`speed)`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
5. **原文**：`-Input and output delays (synchronous paths)`
   **解读**：这是输出路径边界约束。它描述当前模块输出后，下游逻辑和接收寄存器还需要预留多少时间。
6. **原文**：`-Minimum and maximum delay (asynchronous`
   **解读**：这是优化目标或优先级。它告诉我们 DC 在多个目标冲突时先满足什么、后优化什么。
7. **原文**：`paths)`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
8. **原文**：`-Maximum area (number of gates)`
   **解读**：这是优化目标或优先级。它告诉我们 DC 在多个目标冲突时先满足什么、后优化什么。

## 关键概念拆解

- **相关对象/命令**：本页以概念、结构或图示关系为主，没有需要死记的单一命令。
- **它在流程中的位置**：本页属于“约束建模：设计规则、时序、面积和优先级”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“理解优化目标和优先级”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：约束是在给 DC 写合同。design rule 是必须满足的底线，timing constraint 是系统预算的分配，area 等目标是优化偏好。脚本写约束时必须分清这些约束的优先级和作用对象。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：约束要能解释来源。每个 clock、delay、load、max rule 都应该能回答“来自系统需求、工艺库、接口协议还是经验假设”。无法解释来源的约束，后期很难 debug。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“Optimization Constraints”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 051](page-051.md)
- 下一页：[Page 053](page-053.md)
