# Page 082 - Clock tree modeling transition

![Page 82](../assets/pages/page-082.jpg)

## 页面定位

- **页码**：82/112
- **所属阶段**：STA 与时序报告：路径、clock model、I/O 约束和 slack
- **本页角色**：建模时钟网络
- **阅读问题**：本页要回答：clock latency/uncertainty 如何影响 setup/hold？
- **前后关系**：这部分回答“如何判断结果是否真的满足时序”：看路径、看 required/arrival、看 slack。

## 原文要点

> 本页 OCR 可抽取文本为空或很少，解读主要依据页面标题、页码位置和单页图像。

## 原文解读

这页从 setup/hold 检查转入 clock tree modeling。

本页关联的关键对象/命令：本页以概念/图示为主，重点看标题和图中对象关系。

## 我的理解

理想 clock 只适合早期概念；真实工程必须考虑 clock latency、uncertainty 和 source latency。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

写 `set_clock_latency`、`set_clock_uncertainty` 时要区分 rise/fall、source/network、pre-CTS/post-CTS 语境。

## 本页小结

本页的核心收获：Clock tree modeling transition 这一页应被理解为“建模时钟网络”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 081](page-081.md)
- 下一页：[Page 083](page-083.md)
