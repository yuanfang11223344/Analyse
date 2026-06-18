# Page 085 - Effect of Clock Tree Modeling on Setup

![Page 85](../assets/pages/page-085.jpg)

## 页面定位

- **页码**：85/112
- **所属阶段**：STA 与时序报告：路径、clock model、I/O 约束和 slack
- **本页角色**：建模时钟网络
- **阅读问题**：本页要回答：clock latency/uncertainty 如何影响 setup/hold？
- **前后关系**：这部分回答“如何判断结果是否真的满足时序”：看路径、看 required/arrival、看 slack。

## 原文要点

> Effect of Clock Tree Modeling on Setup
> Time
> - Assumed library (Flip Flop) setup time requirement = 1ns
> create_clock –period 10 –waveform {0 5} [get_ports TCK]
> set_clock_latency –rise 1–fall 2 [get_ ports TCK]
> set_clock_uncertainty –rise 0.5 –fall 0.7 [get_ ports TCK]
> - Setup time check = (clock_edge + edge_delay -uncertainty –
> lib_setup)

## 原文解读

本页讲 clock tree modeling 对 setup check 的影响。setup required time 通常会从 capture clock edge 出发，加入 edge delay/latency，再扣除 clock uncertainty 和 library setup time。uncertainty 越大，可用 setup 时间越少。

本页关联的关键对象/命令：`create_clock`, `set_clock_latency`, `set_clock_uncertainty`

## 我的理解

我的理解是：setup 分析关心数据最晚能什么时候到。clock latency、uncertainty 和 library setup requirement 都会改变 required time；因此 clock model 写得越保守，setup 收敛压力越大。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

调 setup violation 时，不只看 data path，也要检查 clock latency、uncertainty 和 library setup 是否按当前阶段合理建模。

## 本页小结

本页的核心收获：Effect of Clock Tree Modeling on Setup 这一页应被理解为“建模时钟网络”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 084](page-084.md)
- 下一页：[Page 086](page-086.md)
