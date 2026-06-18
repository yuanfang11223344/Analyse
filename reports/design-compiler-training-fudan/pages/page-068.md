# Page 068 - Gate Level Optimization

![Page 68](../assets/pages/page-068.jpg)

## 页面定位

- **页码**：68/112
- **所属阶段**：综合优化：逻辑优化、映射、compile 与报告
- **本页角色**：设置设计规则底线
- **阅读问题**：本页要回答：哪些约束是工艺规则底线，不能为了面积/速度牺牲？
- **前后关系**：这部分回答“DC 如何改变电路”：从布尔级、门级到时序驱动优化。

## 原文摘录

> Gate Level Optimization
> - Select components to meet timing, design rule
> & area goals specified for the circuit.
> - Has a local effect on the area/speed
> characteristic of a design.
> - Strategy: combinational mapping & sequential
> mapping.

## 图中内容理解

这页内容代表约束模型。图中或命令表达的不是电路功能，而是 DC 必须满足的边界条件：哪些是硬性 design rule，哪些是 timing budget，哪些是面积/速度目标。综合时电路结构会围绕这些目标被重写。

## 原文逐项解读

1. **原文**：`Gate Level Optimization`
   **解读**：这是综合优化和映射。DC 会在逻辑结构、目标库单元和时序目标之间做取舍，最终生成门级实现。
2. **原文**：`- Select components to meet timing, design rule`
   **解读**：这是工艺/库给出的硬性规则。DC 通常会优先修复这些 violation，即使面积或局部时序因此变差。
3. **原文**：`& area goals specified for the circuit.`
   **解读**：这是优化目标或优先级。它告诉我们 DC 在多个目标冲突时先满足什么、后优化什么。
4. **原文**：`- Has a local effect on the area/speed`
   **解读**：这是优化目标或优先级。它告诉我们 DC 在多个目标冲突时先满足什么、后优化什么。
5. **原文**：`characteristic of a design.`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
6. **原文**：`- Strategy: combinational mapping & sequential`
   **解读**：这是综合优化和映射。DC 会在逻辑结构、目标库单元和时序目标之间做取舍，最终生成门级实现。
7. **原文**：`mapping.`
   **解读**：这是综合优化和映射。DC 会在逻辑结构、目标库单元和时序目标之间做取舍，最终生成门级实现。

## 关键概念拆解

- **相关对象/命令**：本页以概念、结构或图示关系为主，没有需要死记的单一命令。
- **它在流程中的位置**：本页属于“综合优化：逻辑优化、映射、compile 与报告”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“设置设计规则底线”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：约束是在给 DC 写合同。design rule 是必须满足的底线，timing constraint 是系统预算的分配，area 等目标是优化偏好。脚本写约束时必须分清这些约束的优先级和作用对象。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：约束要能解释来源。每个 clock、delay、load、max rule 都应该能回答“来自系统需求、工艺库、接口协议还是经验假设”。无法解释来源的约束，后期很难 debug。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“Gate Level Optimization”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 067](page-067.md)
- 下一页：[Page 069](page-069.md)
