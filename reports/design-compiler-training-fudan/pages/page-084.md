# Page 084 - Clock Tree Modeling Example

![Page 84](../assets/pages/page-084.jpg)

## 页面定位

- **页码**：84/112
- **所属阶段**：STA 与时序报告：路径、clock model、I/O 约束和 slack
- **本页角色**：建模时钟网络
- **阅读问题**：本页要回答：clock latency/uncertainty 如何影响 setup/hold？
- **前后关系**：这部分回答“如何判断结果是否真的满足时序”：看路径、看 required/arrival、看 slack。

## 原文要点

> Clock Tree Modeling Example
> - create_clock –period 10 –waveform {0 5} [get_ports TCK]
> - set_clock_latency –rise 1 –fall 2 [get_ ports TCK]
> - set_clock_uncertainty –rise 0.8 –fall 0.5 [get_ ports TCK]

## 原文解读

本页给出 clock tree modeling 示例：先用 `create_clock` 定义 TCK，再用 `set_clock_latency` 指定 rise/fall clock latency，用 `set_clock_uncertainty` 描述时钟不确定性。它们共同影响 STA 中 clock path 和 required time。

本页关联的关键对象/命令：`create_clock`, `set_clock_latency`, `set_clock_uncertainty`

## 我的理解

我的理解是：这页不是普通 I/O timing constraint，而是在给理想时钟补上更真实的 clock tree 假设。latency 描述时钟到达延迟，uncertainty 描述偏差和裕量。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

写 clock model 时要区分 rise/fall latency 和 uncertainty；这些值会同时影响 setup 与 hold 分析。

## 本页小结

本页的核心收获：Clock Tree Modeling Example 这一页应被理解为“建模时钟网络”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 083](page-083.md)
- 下一页：[Page 085](page-085.md)
