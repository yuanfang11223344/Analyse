# Page 030 - set_fanout_load

![Page 30](../assets/pages/page-030.jpg)

## 页面定位

- **页码**：30/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：配置综合库
- **阅读问题**：本页要回答：DC 到哪里找库，最终映射到哪个目标库？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文要点

> set_fanout_load
> - You can model the external fanout effects by
> specifying the expected fanout load values on output
> ports with the set_fanout_load command.
> - set_fanout_load 4 {out1}
> - Design Compiler tries to ensure that the sum of the
> fanout load on the output port plus the fanout load of
> cells connected to the output port driver is less than
> the maximum fanout limit of the library, library cell, and
> design.

## 原文解读

本页讲库相关设置。`search_path` 决定 DC 到哪里找文件，`link_library` 用来解析已有设计和引用，`target_library` 决定最终映射到哪些工艺单元。

本页关联的关键对象/命令：`set_fanout_load`, `compile`

## 我的理解

我的理解是：库配置不是前置杂项，而是综合的“词典”和“零件仓库”。库配错时，后面 timing 再怎么调都可能是在错误模型上优化。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

检查脚本时先看 `.synopsys_dc.setup`、`target_library`、`link_library`，确认路径、库名和工艺角一致。

## 本页小结

本页的核心收获：set_fanout_load 这一页应被理解为“配置综合库”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 029](page-029.md)
- 下一页：[Page 031](page-031.md)
