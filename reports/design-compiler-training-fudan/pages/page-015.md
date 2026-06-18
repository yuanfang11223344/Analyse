# Page 015 - Read Design

![Page 15](../assets/pages/page-015.jpg)

## 页面定位

- **页码**：15/112
- **所属阶段**：前端准备：库、读入设计和 DC 对象模型
- **本页角色**：读入并建立设计层次
- **阅读问题**：本页要回答：RTL 如何进入 DC 数据库，设计层次如何建立？
- **前后关系**：这部分回答“DC 如何认识设计”：库在哪里、RTL 如何读入、对象如何被引用。

## 原文摘录

> Read Design
>  step1: read, read_verilog, read_vhdl
> 或 analyze + elaborate (analyze HDL
> code and establish Boolean functions)
> - Difference?
> - step2: link (resolve design reference)
> - step3: uniquify (removes multiply-instantiated
> hierarchy in the current design by creating
> a unique design for each cell instance)

## 页面结构与图示分析

本页主要是文字/命令列表结构。阅读顺序应从标题开始，再看项目符号或命令示例：标题给主题，项目符号给定义和限制，命令示例说明如何在 dc_shell 中落地。

## 原文逐项解读

1. **原文**：`Read Design`
   **解读**：这是把 RTL 变成 DC 内部设计数据库的步骤。关键不只是读文件，而是建立层次、解析引用，并确认当前操作对象。
2. **原文**：` step1: read, read_verilog, read_vhdl`
   **解读**：这是把 RTL 变成 DC 内部设计数据库的步骤。关键不只是读文件，而是建立层次、解析引用，并确认当前操作对象。
3. **原文**：`或 analyze + elaborate (analyze HDL`
   **解读**：这是把 RTL 变成 DC 内部设计数据库的步骤。关键不只是读文件，而是建立层次、解析引用，并确认当前操作对象。
4. **原文**：`code and establish Boolean functions)`
   **解读**：这是 STA 基础。DC 把设计拆成 timing path，分别计算 arrival time、required time 和 slack。
5. **原文**：`- Difference?`
   **解读**：这是标题下的一个子要点，通常在补充定义、适用对象、命令参数或注意事项。读时要把它和本页标题连起来。
6. **原文**：`- step2: link (resolve design reference)`
   **解读**：这是把 RTL 变成 DC 内部设计数据库的步骤。关键不只是读文件，而是建立层次、解析引用，并确认当前操作对象。
7. **原文**：`- step3: uniquify (removes multiply-instantiated`
   **解读**：这是 STA 基础。DC 把设计拆成 timing path，分别计算 arrival time、required time 和 slack。
8. **原文**：`hierarchy in the current design by creating`
   **解读**：这句话给出本页概念的定义、条件或结论。理解时要把主语、动作和作用对象拆开：谁被设置、什么属性被改变、后续哪类优化或报告会受影响。
9. **原文**：`a unique design for each cell instance)`
   **解读**：这是 STA 基础。DC 把设计拆成 timing path，分别计算 arrival time、required time 和 slack。

## 关键概念拆解

- **相关对象/命令**：`read_verilog`, `analyze`, `elaborate`
- **它在流程中的位置**：本页属于“前端准备：库、读入设计和 DC 对象模型”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“读入并建立设计层次”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：Read Design 不是孤立术语，它在这一章里承担承上启下的作用。读它时要回到 DC 流程：对象是否建立，环境是否真实，约束是否准确，报告能否验证。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：每页都要落到一个工程动作上：检查对象、补充环境、写清约束、运行优化、阅读报告或改进项目组织。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“Read Design”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 014](page-014.md)
- 下一页：[Page 016](page-016.md)
