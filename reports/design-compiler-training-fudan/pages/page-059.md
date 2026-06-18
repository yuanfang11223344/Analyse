# Page 059 - Timing Constraints for Sequential

![Page 59](../assets/pages/page-059.jpg)

## 页面定位

- **页码**：59/112
- **所属阶段**：约束建模：设计规则、时序、面积和优先级
- **本页角色**：设置时序预算
- **阅读问题**：本页要回答：时钟和 I/O 时间预算如何写进 DC？
- **前后关系**：这部分回答“工具必须满足什么”：硬性 design rule 与优化目标要分清。

## 原文摘录

> Timing Constraints for Sequential
> Circuit
> - create_clock: define your clock’s waveform &
> respect the set-up time requirements of all
> clocked flip-flops.
> create_clock -period 12.5 -waveform {0 6.25}
> [get_ports clkM]
> - set_dont_touch_network: do not re-bufer the
> clock network.
> - set_dont_touch_network [get_clocks clkM]

## 页面结构与图示分析

本页主要是文字/命令列表结构。阅读顺序应从标题开始，再看项目符号或命令示例：标题给主题，项目符号给定义和限制，命令示例说明如何在 dc_shell 中落地。

## 原文逐项解读

1. **原文**：`Timing Constraints for Sequential`
   **解读**：这句话给出本页概念的定义、条件或结论。理解时要把主语、动作和作用对象拆开：谁被设置、什么属性被改变、后续哪类优化或报告会受影响。
2. **原文**：`Circuit`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
3. **原文**：`- create_clock: define your clock’s waveform &`
   **解读**：`create_clock` 定义 clock 对象、周期和波形。`-period 10` 表示周期为 10，`-waveform {0 5}` 表示上升/下降边沿位置，`[get_ports TCK]` 表示这个 clock 绑定到 TCK 端口。
4. **原文**：`respect the set-up time requirements of all`
   **解读**：这句话给出本页概念的定义、条件或结论。理解时要把主语、动作和作用对象拆开：谁被设置、什么属性被改变、后续哪类优化或报告会受影响。
5. **原文**：`clocked flip-flops.`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
6. **原文**：`create_clock -period 12.5 -waveform {0 6.25}`
   **解读**：`create_clock` 定义 clock 对象、周期和波形。`-period 10` 表示周期为 10，`-waveform {0 5}` 表示上升/下降边沿位置，`[get_ports TCK]` 表示这个 clock 绑定到 TCK 端口。
7. **原文**：`[get_ports clkM]`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
8. **原文**：`- set_dont_touch_network: do not re-bufer the`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
9. **原文**：`clock network.`
   **解读**：这是时钟网络建模。latency 描述时钟到达延迟，uncertainty 描述抖动、偏斜或保守裕量，它们会改变 setup/hold 判断。
10. **原文**：`- set_dont_touch_network [get_clocks clkM]`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。

## 关键概念拆解

- **相关对象/命令**：`create_clock`
- **它在流程中的位置**：本页属于“约束建模：设计规则、时序、面积和优先级”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“设置时序预算”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：约束是在给 DC 写合同。design rule 是必须满足的底线，timing constraint 是系统预算的分配，area 等目标是优化偏好。脚本写约束时必须分清这些约束的优先级和作用对象。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：约束要能解释来源。每个 clock、delay、load、max rule 都应该能回答“来自系统需求、工艺库、接口协议还是经验假设”。无法解释来源的约束，后期很难 debug。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“Timing Constraints for Sequential”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 058](page-058.md)
- 下一页：[Page 060](page-060.md)
