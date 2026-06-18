# Page 106 - This partitioning is recommended due to:

![Page 106](../assets/pages/page-106.jpg)

## 页面定位

- **页码**：106/112
- **所属阶段**：Partitioning：层次划分、glue logic 和工程边界
- **本页角色**：改进设计分区
- **阅读问题**：本页要回答：如何划分 block 才能减少跨层级复杂度？
- **前后关系**：这部分把综合从命令层拉回架构层：分区方式会直接决定脚本复杂度、可测性和可收敛性。

## 原文要点

> This partitioning is recommended due to:
> - Possible technology-dependent ( “black box”) I/O pad cells
> - Possible untestable “Divide By” clock generation
> - Possible technology-dependent JTAG circuitry

## 原文解读

本页解释推荐分区的原因：I/O pad 可能是工艺相关黑盒，分频时钟可能不可测，某些工艺相关单元不应混入普通逻辑。

本页关联的关键对象/命令：`partitioning`

## 我的理解

我的理解是：分区要尊重工艺、测试和时钟结构。不是所有逻辑都适合一起综合。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

对 pad、clock generation、test logic 建立单独处理策略。

## 本页小结

本页的核心收获：This partitioning is recommended due to: 这一页应被理解为“改进设计分区”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 105](page-105.md)
- 下一页：[Page 107](page-107.md)
