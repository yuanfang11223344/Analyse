# Page 087 - Modeling Source Latency

![Page 87](../assets/pages/page-087.jpg)

## 页面定位

- **页码**：87/112
- **所属阶段**：STA 与时序报告：路径、clock model、I/O 约束和 slack
- **本页角色**：建模时钟网络
- **阅读问题**：本页要回答：source latency 和普通 clock latency 有什么区别？
- **前后关系**：这部分回答“如何判断结果是否真的满足时序”：看路径、看 required/arrival、看 slack。

## 原文摘录

> Modeling Source Latency
> - Source latency is the propagation time from the actual clock
> origin to the clock definition point in the design
> create_clock –period 10 –waveform {0 5} [get_ports TCK]
> set_clock_latency –source 3 [get_clocks TCK]
> set_clock_latency 1 [get_clocks TCK]

## 图中内容理解

这页内容代表 STA 或时序建模。图中或文字中的 clock、data path、latency、uncertainty、arrival、required、slack 都属于同一套时间账本。要理解它，就要判断每个对象是在 launch 侧、capture 侧、data path 侧还是 required time 侧。

## 原文逐项解读

1. **原文**：`Modeling Source Latency`
   **解读**：标题说明本页讨论 source latency，也就是时钟源头到设计中 clock 定义点之前的延迟。
2. **原文**：`- Source latency is the propagation time from the actual clock`
   **解读**：这一句给出定义的前半部分：source latency 是真实 clock origin 出发后的传播时间，不是普通数据路径延迟。
3. **原文**：`origin to the clock definition point in the design`
   **解读**：这一句补全定义：传播终点是设计中定义 clock 的位置。也就是说 source latency 覆盖的是 clock 进入设计或到达定义点之前的那段路径。
4. **原文**：`create_clock –period 10 –waveform {0 5} [get_ports TCK]`
   **解读**：先定义 TCK clock 对象。只有先有 clock object，后面才能对这个 clock 设置 source latency 或 network latency。
5. **原文**：`set_clock_latency –source 3 [get_clocks TCK]`
   **解读**：`-source 3` 表示设置 source latency 为 3。它描述真实时钟源到 TCK clock definition point 之间已经消耗的时间。
6. **原文**：`set_clock_latency 1 [get_clocks TCK]`
   **解读**：不带 `-source` 的 latency 通常表示 clock definition point 之后的 network latency。这里的 1 与前面的 source 3 表示两段不同的时钟延迟。

## 关键概念拆解

- **相关对象/命令**：`create_clock`, `set_clock_latency`
- **它在流程中的位置**：本页属于“STA 与时序报告：路径、clock model、I/O 约束和 slack”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“建模时钟网络”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：source latency 和普通 clock latency 最大区别在边界。source latency 属于 clock 到达定义点之前的系统/源端路径，network latency 更偏向定义点之后的片上 clock network。把二者混在一起会导致时钟延迟重复或漏算。

这页本质上是在教我们把 clock path 分段建模，而不是用一个笼统数字糊住全部时钟延迟。

## 对我们的启示

对我们的启示：做层次化综合或顶层集成时，要问清 clock 是在哪里定义的。若 clock definition point 不同，source latency 和 network latency 的边界也会变，脚本不能机械复用。

## 本页小结

本页的核心不是“Modeling Source Latency”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 086](page-086.md)
- 下一页：[Page 088](page-088.md)
