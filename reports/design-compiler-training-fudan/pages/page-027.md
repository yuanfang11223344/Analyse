# Page 027 - Set Input Pulling Resistance (khoms)

![Page 27](../assets/pages/page-027.jpg)

## 页面定位

- **页码**：27/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：建模输入驱动
- **阅读问题**：本页要回答：如何用具体库单元描述输入端外部驱动？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文摘录

> Set Input Pulling Resistance (khoms)
> - set_drive
> - set_drive_cell : sets attributes on input or inout
> ports of the current design that specify that a
> library cell or output pin of a library cell drives the
> specified ports.
> - set_driving_cell -lib_cell AND2 {IN1}
> - set_driving_cell -lib_cell INV -pin Z \
> -library tech_lib [all_inputs]
> - set_driving_cell -lib_cell INV -don’t_scale {IN1}
> - set_driving_cell -rise -lib_cell BUF1_TS -pin Z {IN1}
> - set_driving_cell -fall -lib_cell DFF_TS -pin Q {IN1}

## 图中内容理解

这页内容代表设计环境建模。图中或命令表达的是模块外部世界：上游驱动能力、下游电容负载、外部 fanout、PVT 条件或互连 RC 估计。它们会改变 cell delay、transition、buffer 插入和 sizing 选择。

## 原文逐项解读

1. **原文**：`Set Input Pulling Resistance (khoms)`
   **解读**：这是 STA 基础。DC 把设计拆成 timing path，分别计算 arrival time、required time 和 slack。
2. **原文**：`- set_drive`
   **解读**：这是输入驱动建模。它告诉 DC 模块输入端由多强的外部电路驱动，从而影响输入 transition、内部 delay 和设计规则检查。
3. **原文**：`- set_drive_cell : sets attributes on input or inout`
   **解读**：这是输入驱动建模。它告诉 DC 模块输入端由多强的外部电路驱动，从而影响输入 transition、内部 delay 和设计规则检查。
4. **原文**：`ports of the current design that specify that a`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
5. **原文**：`library cell or output pin of a library cell drives the`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
6. **原文**：`specified ports.`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
7. **原文**：`- set_driving_cell -lib_cell AND2 {IN1}`
   **解读**：这是输入驱动建模。它告诉 DC 模块输入端由多强的外部电路驱动，从而影响输入 transition、内部 delay 和设计规则检查。
8. **原文**：`- set_driving_cell -lib_cell INV -pin Z \`
   **解读**：这是输入驱动建模。它告诉 DC 模块输入端由多强的外部电路驱动，从而影响输入 transition、内部 delay 和设计规则检查。
9. **原文**：`-library tech_lib [all_inputs]`
   **解读**：这是标题下的一个子要点，通常在补充定义、适用对象、命令参数或注意事项。读时要把它和本页标题连起来。
10. **原文**：`- set_driving_cell -lib_cell INV -don’t_scale {IN1}`
   **解读**：这是输入驱动建模。它告诉 DC 模块输入端由多强的外部电路驱动，从而影响输入 transition、内部 delay 和设计规则检查。
11. **原文**：`- set_driving_cell -rise -lib_cell BUF1_TS -pin Z {IN1}`
   **解读**：这是输入驱动建模。它告诉 DC 模块输入端由多强的外部电路驱动，从而影响输入 transition、内部 delay 和设计规则检查。
12. **原文**：`- set_driving_cell -fall -lib_cell DFF_TS -pin Q {IN1}`
   **解读**：这是输入驱动建模。它告诉 DC 模块输入端由多强的外部电路驱动，从而影响输入 transition、内部 delay 和设计规则检查。

## 关键概念拆解

- **相关对象/命令**：`set_drive`, `set_driving_cell`
- **它在流程中的位置**：本页属于“设计环境建模：工艺、负载、扇出和线负载”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“建模输入驱动”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：这一页属于 design environment。环境建模不是“外围杂项”，而是在告诉 DC 当前模块外部世界长什么样。输入驱动、输出负载、fanout、wire load 和 PVT 会共同决定 delay、transition、cell sizing 与优化压力。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：模块级综合必须主动补全外部世界。不要默认输入是理想驱动、输出没有负载、互连没有延迟；这些偷懒会让时序结果过于乐观。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“Set Input Pulling Resistance (khoms)”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 026](page-026.md)
- 下一页：[Page 028](page-028.md)
