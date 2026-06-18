# Page 085 - Effect of Clock Tree Modeling on Setup

![Page 85](../assets/pages/page-085.jpg)

## 页面定位

- **页码**：85/112
- **所属阶段**：STA 与时序报告：路径、clock model、I/O 约束和 slack
- **本页角色**：建模时钟网络
- **阅读问题**：本页要回答：clock latency/uncertainty 如何影响 setup/hold？
- **前后关系**：这部分回答“如何判断结果是否真的满足时序”：看路径、看 required/arrival、看 slack。

## 原文摘录

> Effect of Clock Tree Modeling on Setup
> Time
> - Assumed library (Flip Flop) setup time requirement = 1ns
> create_clock –period 10 –waveform {0 5} [get_ports TCK]
> set_clock_latency –rise 1–fall 2 [get_ ports TCK]
> set_clock_uncertainty –rise 0.5 –fall 0.7 [get_ ports TCK]
> - Setup time check = (clock_edge + edge_delay -uncertainty –
> lib_setup)

## 页面结构与图示分析

本页主要是文字/命令列表结构。阅读顺序应从标题开始，再看项目符号或命令示例：标题给主题，项目符号给定义和限制，命令示例说明如何在 dc_shell 中落地。

## 原文逐项解读

1. **原文**：`Effect of Clock Tree Modeling on Setup`
   **解读**：标题说明本页研究 clock tree model 对 setup 检查的影响。setup 检查关心数据最晚能否在捕获边沿之前稳定。
2. **原文**：`Time`
   **解读**：这是上一行标题的换行，完整标题应读作 “Effect of Clock Tree Modeling on Setup Time”。重点是 setup required time 如何被 clock latency、uncertainty 和 library setup 改变。
3. **原文**：`- Assumed library (Flip Flop) setup time requirement = 1ns`
   **解读**：这里假设触发器库单元的 setup requirement 是 1ns。也就是说，数据必须在捕获 clock 边沿到来前至少提前 1ns 稳定。
4. **原文**：`create_clock –period 10 –waveform {0 5} [get_ports TCK]`
   **解读**：定义 TCK 时钟，周期为 10，波形边沿在 0 和 5。它提供了 setup 检查的理想时钟基准。
5. **原文**：`set_clock_latency –rise 1–fall 2 [get_ ports TCK]`
   **解读**：给 TCK 的上升沿和下降沿设置不同 latency。setup 检查里的 capture edge 会受到对应 edge delay 影响，因此 clock tree 模型会改变 required time。
6. **原文**：`set_clock_uncertainty –rise 0.5 –fall 0.7 [get_ ports TCK]`
   **解读**：给时钟加入不确定性。setup 分析中 uncertainty 通常会从可用时间中扣掉，因为它代表 jitter/skew/裕量，要求数据更早稳定。
7. **原文**：`- Setup time check = (clock_edge + edge_delay -uncertainty –`
   **解读**：这是 setup required time 的计算框架：从捕获 clock edge 出发，加上 clock tree 延迟，再扣掉 uncertainty。扣掉 uncertainty 表示把时序要求收紧。
8. **原文**：`lib_setup)`
   **解读**：公式最后还要扣掉 library setup time。因为触发器需要在采样边沿之前提前看到稳定数据，所以 lib_setup 也会减少数据路径可用时间。

## 关键概念拆解

- **相关对象/命令**：`create_clock`, `set_clock_latency`, `set_clock_uncertainty`
- **它在流程中的位置**：本页属于“STA 与时序报告：路径、clock model、I/O 约束和 slack”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“建模时钟网络”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：setup 分析的核心是“数据最晚什么时候必须到”。clock tree latency 会移动捕获边沿，uncertainty 和 library setup 会收紧 required time。也就是说，clock model 不是报告里的装饰项，而是直接决定 setup slack 的一部分。

这页尤其提醒我：如果只写 `create_clock` 而不考虑 latency/uncertainty，早期综合报告会偏理想；但如果 uncertainty 给得过大，又可能导致 DC 过度优化、面积上升。

## 对我们的启示

对我们的启示：setup violation 不一定只由 data path 太慢导致，也可能来自 clock uncertainty 过大、clock latency 假设变化或 library setup 要求。debug setup 时要同时看 data path 和 clock/required path。

真实项目里，pre-CTS 的 latency/uncertainty 应该来自项目约定或后端估计；不要随便填一个好看的数字。

## 本页小结

本页的核心不是“Effect of Clock Tree Modeling on Setup”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 084](page-084.md)
- 下一页：[Page 086](page-086.md)
