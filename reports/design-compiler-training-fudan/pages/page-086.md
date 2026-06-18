# Page 086 - Effect of Clock Tree Modeling on Hold

![Page 86](../assets/pages/page-086.jpg)

## 页面定位

- **页码**：86/112
- **所属阶段**：STA 与时序报告：路径、clock model、I/O 约束和 slack
- **本页角色**：建模时钟网络
- **阅读问题**：本页要回答：clock latency/uncertainty 如何影响 setup/hold？
- **前后关系**：这部分回答“如何判断结果是否真的满足时序”：看路径、看 required/arrival、看 slack。

## 原文要点

> Effect of Clock Tree Modeling on Hold
> Time
> - Assumed library (Flip Flop) hold time requirement = 1ns
> create_clock –period 10 –waveform {0 5} [get_ports TCK]
> set_clock_latency –rise 1 –fall 2 [get_ports TCK]
> set_clock_uncertainty –rise 0.5 –fall 0.8 [get_ports TCK]
> - Hold time check = (clock_edge + edge_delay +uncertainty +
> lib_hold)

## 原文解读

本页讲 clock tree modeling 对 hold check 的影响。hold check 关注数据是否过早变化，公式中 uncertainty 和 library hold time 会提高保持要求，因此 hold 分析与 setup 分析的方向不同。

本页关联的关键对象/命令：`create_clock`, `set_clock_latency`, `set_clock_uncertainty`

## 我的理解

我的理解是：hold 分析看的是最小路径，很多时候不是路径太慢，而是数据太快。clock latency 和 uncertainty 的设置会改变 hold required time，所以同一套 clock model 对 setup/hold 的影响不能混为一谈。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

调 hold violation 时先确认 `Path Type: min`，再检查 clock uncertainty、latency 和 library hold requirement；不要用 setup 的直觉去解释 hold。

## 本页小结

本页的核心收获：Effect of Clock Tree Modeling on Hold 这一页应被理解为“建模时钟网络”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 085](page-085.md)
- 下一页：[Page 087](page-087.md)
