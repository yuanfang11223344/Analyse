# Page 086 - Effect of Clock Tree Modeling on Hold

![Page 86](../assets/pages/page-086.jpg)

## 页面定位

- **页码**：86/112
- **所属阶段**：STA 与时序报告：路径、clock model、I/O 约束和 slack
- **本页角色**：配置综合库
- **阅读问题**：本页要回答：DC 到哪里找库，最终映射到哪个目标库？
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

本页讲库相关设置。`search_path` 决定 DC 到哪里找文件，`link_library` 用来解析已有设计和引用，`target_library` 决定最终映射到哪些工艺单元。

本页关联的关键对象/命令：`create_clock`, `set_clock_latency`, `set_clock_uncertainty`

## 我的理解

我的理解是：库配置不是前置杂项，而是综合的“词典”和“零件仓库”。库配错时，后面 timing 再怎么调都可能是在错误模型上优化。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

检查脚本时先看 `.synopsys_dc.setup`、`target_library`、`link_library`，确认路径、库名和工艺角一致。

## 本页小结

本页的核心收获：Effect of Clock Tree Modeling on Hold 这一页应被理解为“配置综合库”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 085](page-085.md)
- 下一页：[Page 087](page-087.md)
