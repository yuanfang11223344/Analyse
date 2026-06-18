# Page 084 - Clock Tree Modeling Example

![Page 84](../assets/pages/page-084.jpg)

## 页面定位

- **页码**：84/112
- **所属阶段**：STA 与时序报告：路径、clock model、I/O 约束和 slack
- **本页角色**：建模时钟网络
- **阅读问题**：本页要回答：clock latency/uncertainty 如何影响 setup/hold？
- **前后关系**：这部分回答“如何判断结果是否真的满足时序”：看路径、看 required/arrival、看 slack。

## 原文摘录

> Clock Tree Modeling Example
> - create_clock –period 10 –waveform {0 5} [get_ports TCK]
> - set_clock_latency –rise 1 –fall 2 [get_ ports TCK]
> - set_clock_uncertainty –rise 0.8 –fall 0.5 [get_ ports TCK]

## 页面结构与图示分析

本页主要是文字/命令列表结构。阅读顺序应从标题开始，再看项目符号或命令示例：标题给主题，项目符号给定义和限制，命令示例说明如何在 dc_shell 中落地。

## 原文逐项解读

1. **原文**：`Clock Tree Modeling Example`
   **解读**：标题说明本页不是普通 clock 定义，而是在演示如何给时钟网络加入 latency 和 uncertainty 模型。
2. **原文**：`- create_clock –period 10 –waveform {0 5} [get_ports TCK]`
   **解读**：`create_clock` 定义 clock 对象、周期和波形。`-period 10` 表示周期为 10，`-waveform {0 5}` 表示上升/下降边沿位置，`[get_ports TCK]` 表示这个 clock 绑定到 TCK 端口。
3. **原文**：`- set_clock_latency –rise 1 –fall 2 [get_ ports TCK]`
   **解读**：`set_clock_latency` 给时钟到达时间加上延迟模型。这里 rise latency 为 1、fall latency 为 2，说明不同边沿可以有不同的时钟网络延迟，STA 会用它们调整 launch/capture clock 的时间。
4. **原文**：`- set_clock_uncertainty –rise 0.8 –fall 0.5 [get_ ports TCK]`
   **解读**：`set_clock_uncertainty` 建模 clock skew、jitter 或保守裕量。uncertainty 会收紧时序要求，因此数值越大，timing 越难满足。

## 关键概念拆解

- **相关对象/命令**：`create_clock`, `set_clock_latency`, `set_clock_uncertainty`
- **它在流程中的位置**：本页属于“STA 与时序报告：路径、clock model、I/O 约束和 slack”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“建模时钟网络”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：这页把 clock 从理想边沿变成更接近真实的 clock tree 模型。`create_clock` 只定义了理想周期，`set_clock_latency` 和 `set_clock_uncertainty` 才把时钟到达延迟和不确定性引入 STA。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：pre-CTS 阶段也要有合理 clock model。latency 和 uncertainty 设得过小会过度乐观，设得过大则可能造成过度优化；数值应来自项目约定或后端估计。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“Clock Tree Modeling Example”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 083](page-083.md)
- 下一页：[Page 085](page-085.md)
