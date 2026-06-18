# Page 086 - Effect of Clock Tree Modeling on Hold

![Page 86](../assets/pages/page-086.jpg)

## 页面定位

- **页码**：86/112
- **所属阶段**：STA 与时序报告：路径、clock model、I/O 约束和 slack
- **本页角色**：建模时钟网络
- **阅读问题**：本页要回答：clock latency/uncertainty 如何影响 setup/hold？
- **前后关系**：这部分回答“如何判断结果是否真的满足时序”：看路径、看 required/arrival、看 slack。

## 原文摘录

> Effect of Clock Tree Modeling on Hold
> Time
> - Assumed library (Flip Flop) hold time requirement = 1ns
> create_clock –period 10 –waveform {0 5} [get_ports TCK]
> set_clock_latency –rise 1 –fall 2 [get_ports TCK]
> set_clock_uncertainty –rise 0.5 –fall 0.8 [get_ports TCK]
> - Hold time check = (clock_edge + edge_delay +uncertainty +
> lib_hold)

## 页面结构与图示分析

本页主要是文字/命令列表结构。阅读顺序应从标题开始，再看项目符号或命令示例：标题给主题，项目符号给定义和限制，命令示例说明如何在 dc_shell 中落地。

## 原文逐项解读

1. **原文**：`Effect of Clock Tree Modeling on Hold`
   **解读**：标题说明本页研究 clock tree model 对 hold 检查的影响。hold 检查关心数据会不会太早变化，破坏当前采样。
2. **原文**：`Time`
   **解读**：这是标题换行，完整意思是 “Effect of Clock Tree Modeling on Hold Time”。重点是 hold required time 如何被 clock latency、uncertainty 和 library hold 改变。
3. **原文**：`- Assumed library (Flip Flop) hold time requirement = 1ns`
   **解读**：这里假设触发器库单元要求数据在采样边沿之后还要保持 1ns。这个库要求会增加 hold 检查的约束强度。
4. **原文**：`create_clock –period 10 –waveform {0 5} [get_ports TCK]`
   **解读**：定义 TCK 的周期和波形，为 hold 检查提供 clock edge 基准。hold 通常比较相邻或同一边沿附近的最小延迟关系。
5. **原文**：`set_clock_latency –rise 1 –fall 2 [get_ports TCK]`
   **解读**：给不同时钟边沿设置 latency。hold 分析非常敏感于 launch/capture clock 到达时间差，因为数据太快到达就可能造成 hold violation。
6. **原文**：`set_clock_uncertainty –rise 0.5 –fall 0.8 [get_ports TCK]`
   **解读**：给时钟加入 uncertainty。和 setup 不同，hold 公式中 uncertainty 以更保守的方向影响要求，会让最小延迟路径更难通过。
7. **原文**：`- Hold time check = (clock_edge + edge_delay +uncertainty +`
   **解读**：hold required time 从 clock edge 和 edge delay 出发，并加上 uncertainty。加号表示为了防止数据过早变化，要求数据保持得更久。
8. **原文**：`lib_hold)`
   **解读**：公式最后加上 library hold time。触发器自身要求数据在采样后保持一段时间，因此 lib_hold 会提高 hold 的 required boundary。

## 关键概念拆解

- **相关对象/命令**：`create_clock`, `set_clock_latency`, `set_clock_uncertainty`
- **它在流程中的位置**：本页属于“STA 与时序报告：路径、clock model、I/O 约束和 slack”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“建模时钟网络”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：hold 与 setup 的直觉相反。setup 怕数据太晚，hold 怕数据太早。clock latency 和 uncertainty 在 hold 中可能把 required time 往更严格方向推，因此一个看似很短、很快的路径反而可能是问题。

这页要和前一页对照读：setup 公式里 uncertainty 和 lib_setup 是减少可用时间；hold 公式里 uncertainty 和 lib_hold 是提高保持要求。

## 对我们的启示

对我们的启示：debug hold violation 时，不要去盲目加快逻辑；恰恰可能需要增加 delay、插 buffer 或调整 clock model。读 report 时必须先确认 `Path Type: min`，否则会用 setup 思维误判问题。

## 本页小结

本页的核心不是“Effect of Clock Tree Modeling on Hold”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 085](page-085.md)
- 下一页：[Page 087](page-087.md)
