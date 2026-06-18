# Page 076 - - Input Paths

![Page 76](../assets/pages/page-076.jpg)

## 页面定位

- **页码**：76/112
- **所属阶段**：STA 与时序报告：路径、clock model、I/O 约束和 slack
- **本页角色**：建立 STA 基本概念
- **阅读问题**：本页要回答：一条 timing path 如何被定义、分组和检查？
- **前后关系**：这部分回答“如何判断结果是否真的满足时序”：看路径、看 required/arrival、看 slack。

## 原文要点

> - Input Paths
> - Output Paths
> - Register-to-Register Paths
> - Combinational Paths

## 原文解读

本页讲 STA 基础概念：路径类型、path group、delay calculation、setup/hold check。STA 把电路拆成 timing arc，分别累加 cell delay 和 net delay。

本页关联的关键对象/命令：本页以概念/图示为主，重点看标题和图中对象关系。

## 我的理解

我的理解是：STA 是综合质量的判卷系统。setup 看最大数据路径能否在下一采样边沿前稳定；hold 看最小数据路径会不会太快破坏当前采样。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

读路径时先标出 startpoint、endpoint、path group、path type，再看 arrival/required/slack。

## 本页小结

本页的核心收获：- Input Paths 这一页应被理解为“建立 STA 基本概念”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 075](page-075.md)
- 下一页：[Page 077](page-077.md)
