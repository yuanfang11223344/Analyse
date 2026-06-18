# Page 026 - Set Input Pulling Resistance (khoms)

![Page 26](../assets/pages/page-026.jpg)

## 页面定位

- **页码**：26/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：建模输入驱动
- **阅读问题**：本页要回答：输入端外部驱动能力如何建模？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文摘录

> Set Input Pulling Resistance (khoms)
> - set_drive
> - set_drive : Sets the rise_drive or fall_drive
> attributes to specified resistance values on
> specified input and inout ports.
> - set_drive 2 .0 {A B C}; or set_drive 2 .0 “A B C”;
> - set_drive 2 [all_inputs];
> - set_drive -rise 1 [get_ports B];
> - set_drive -rise drive_of(-rise TECH_LIBRARY/INVERTER/OUT) \
> [get_ports C]
>  drive_of : Returns the drive resistance value of the
> specified library cell pin.

## 页面结构与图示分析

本页主要是文字/命令列表结构。阅读顺序应从标题开始，再看项目符号或命令示例：标题给主题，项目符号给定义和限制，命令示例说明如何在 dc_shell 中落地。

## 原文逐项解读

1. **原文**：`Set Input Pulling Resistance (khoms)`
   **解读**：这是 STA 基础。DC 把设计拆成 timing path，分别计算 arrival time、required time 和 slack。
2. **原文**：`- set_drive`
   **解读**：这是输入驱动建模。它告诉 DC 模块输入端由多强的外部电路驱动，从而影响输入 transition、内部 delay 和设计规则检查。
3. **原文**：`- set_drive : Sets the rise_drive or fall_drive`
   **解读**：这是输入驱动建模。它告诉 DC 模块输入端由多强的外部电路驱动，从而影响输入 transition、内部 delay 和设计规则检查。
4. **原文**：`attributes to specified resistance values on`
   **解读**：这是 STA 基础。DC 把设计拆成 timing path，分别计算 arrival time、required time 和 slack。
5. **原文**：`specified input and inout ports.`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
6. **原文**：`- set_drive 2 .0 {A B C}; or set_drive 2 .0 “A B C”;`
   **解读**：这是输入驱动建模。它告诉 DC 模块输入端由多强的外部电路驱动，从而影响输入 transition、内部 delay 和设计规则检查。
7. **原文**：`- set_drive 2 [all_inputs];`
   **解读**：这是输入驱动建模。它告诉 DC 模块输入端由多强的外部电路驱动，从而影响输入 transition、内部 delay 和设计规则检查。
8. **原文**：`- set_drive -rise 1 [get_ports B];`
   **解读**：这是输入驱动建模。它告诉 DC 模块输入端由多强的外部电路驱动，从而影响输入 transition、内部 delay 和设计规则检查。
9. **原文**：`- set_drive -rise drive_of(-rise TECH_LIBRARY/INVERTER/OUT) \`
   **解读**：这是输入驱动建模。它告诉 DC 模块输入端由多强的外部电路驱动，从而影响输入 transition、内部 delay 和设计规则检查。
10. **原文**：`[get_ports C]`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
11. **原文**：` drive_of : Returns the drive resistance value of the`
   **解读**：这是输入驱动建模。它告诉 DC 模块输入端由多强的外部电路驱动，从而影响输入 transition、内部 delay 和设计规则检查。
12. **原文**：`specified library cell pin.`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。

## 关键概念拆解

- **相关对象/命令**：`set_drive`
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

- 上一页：[Page 025](page-025.md)
- 下一页：[Page 027](page-027.md)
