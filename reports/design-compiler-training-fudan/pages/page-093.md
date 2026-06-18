# Page 093 - Startpoint: ARM7TDMI/debuger/tms_latch_reg/CKN

![Page 93](../assets/pages/page-093.jpg)

## 页面定位

- **页码**：93/112
- **所属阶段**：STA 与时序报告：路径、clock model、I/O 约束和 slack
- **本页角色**：拆解 timing report
- **阅读问题**：本页要回答：timing report 每一段数字从哪里来，slack 如何形成？
- **前后关系**：这部分回答“如何判断结果是否真的满足时序”：看路径、看 required/arrival、看 slack。

## 原文要点

> Startpoint: ARM7TDMI/debuger/tms_latch_reg/CKN
> (internal path startpoint clocked by HCLK)
> Endpoint: ARM7TDMI/debuger/tms_s_reg
> (falling edge-triggered flip-flop clocked by HCLK)
> Path Group: HCLK
> Path Type: min
> Point Incr Path
> ------------------------------------------------------------------------------
> clock HCLK (fall edge) 6.00 6.00
> clock network delay (propagated) 0.87 6.87
> input external delay 0.00 6.87 f
> ARM7TDMI/debuger/tms_latch_reg/CKN (FFDNHD2X) 0.00 6.87 f
> ARM7TDMI/debuger/tms_latch_reg/Q (FFDNHD2X) <- 0.18 & 7.05 r
> ARM7TDMI/debuger/tms_s_reg/D (FFDNHD2X) 0.00 & 7.05 r
> ...

## 原文解读

本页给出完整 timing report 示例。前半段是 data arrival：从 HCLK fall edge、clock network delay、外部 delay，到 startpoint/endpoint 的数据路径；后半段是 data required：同一 clock 边沿、clock network delay、uncertainty、library hold time，最后得到 slack。

本页关联的关键对象/命令：本页以概念/图示为主，重点看标题和图中对象关系。

## 我的理解

我的理解是：这是一个 min/hold 类型路径，slack 为 0.00 且 MET，说明刚好满足 hold 要求。读这页不能把它当作普通文本，而要逐行追踪 arrival 和 required 两条账。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

调试 report_timing 时先看 `Path Type: min/max`，再决定是在分析 hold 还是 setup。

## 本页小结

本页的核心收获：Startpoint: ARM7TDMI/debuger/tms_latch_reg/CKN 这一页应被理解为“拆解 timing report”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 092](page-092.md)
- 下一页：[Page 094](page-094.md)
