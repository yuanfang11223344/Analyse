# Page 089 - Constraining the Input Paths

![Page 89](../assets/pages/page-089.jpg)

## 页面定位

- **页码**：89/112
- **所属阶段**：STA 与时序报告：路径、clock model、I/O 约束和 slack
- **本页角色**：约束模块 I/O 路径
- **阅读问题**：本页要回答：模块边界外部时间预算如何折算成 I/O delay？
- **前后关系**：这部分回答“如何判断结果是否真的满足时序”：看路径、看 required/arrival、看 slack。

## 原文要点

> Constraining the Input Paths

## 原文解读

本页继续输入路径约束，通常会把图中的时间预算落到具体 `set_input_delay` 命令。

本页关联的关键对象/命令：本页以概念/图示为主，重点看标题和图中对象关系。

## 我的理解

我的理解是：同一输入端口可能同时需要 max 和 min；max 用于 setup，min 用于 hold，二者不能互相替代。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

检查输入 delay 时，不要只写 max 而漏掉 min。

## 本页小结

本页的核心收获：Constraining the Input Paths 这一页应被理解为“约束模块 I/O 路径”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 088](page-088.md)
- 下一页：[Page 090](page-090.md)
