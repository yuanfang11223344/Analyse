# Page 005 - Synthesis Is Path-Based

![Page 5](../assets/pages/page-005.jpg)

## 页面定位

- **页码**：5/112
- **所属阶段**：综合总览：约束驱动、路径驱动和库映射
- **本页角色**：理解路径驱动综合
- **阅读问题**：为什么 DC 要按 timing path 而不是按模块平均优化？
- **前后关系**：先建立全局认知：DC 的输出质量取决于库、约束和路径分析，而不是单纯运行 compile。

## 原文摘录

> Synthesis Is Path-Based
> Design Compiler uses Static Timing Analysis (STA)
> to calculate the timing of the paths in the design.

## 图中内容理解

这页表达的是 path-based synthesis：DC 通过 STA 分析 timing path，再围绕关键路径优化。它代表的电路观点是：性能瓶颈不是平均分布在所有逻辑上，而是落在特定 startpoint 到 endpoint 的路径上。对我们写代码/约束的启示是，优化要看路径报告，而不是只看模块规模或代码行数。

## 原文逐项解读

1. **原文**：`Synthesis Is Path-Based`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
2. **原文**：`Design Compiler uses Static Timing Analysis (STA)`
   **解读**：这是综合优化和映射。DC 会在逻辑结构、目标库单元和时序目标之间做取舍，最终生成门级实现。
3. **原文**：`to calculate the timing of the paths in the design.`
   **解读**：这句话给出本页概念的定义、条件或结论。理解时要把主语、动作和作用对象拆开：谁被设置、什么属性被改变、后续哪类优化或报告会受影响。

## 关键概念拆解

- **相关对象/命令**：`compile`
- **它在流程中的位置**：本页属于“综合总览：约束驱动、路径驱动和库映射”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“理解路径驱动综合”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：STA 是综合结果的判卷过程。每个数字都应放入 arrival time 或 required time 的账本里看；只看 slack 会错过真正原因，必须追踪路径身份、clock model、data path delay 和约束扣减。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：读 timing report 要像查账。先看 Path Type 和 start/end，再看 clock 与 data 分别怎么算，最后才看 slack；这样才能知道该改约束、改逻辑还是改 clock model。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“Synthesis Is Path-Based”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 004](page-004.md)
- 下一页：[Page 006](page-006.md)
