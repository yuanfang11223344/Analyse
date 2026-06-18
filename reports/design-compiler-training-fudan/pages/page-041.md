# Page 041 - - set _wire_load_model -name “10*10” -library my_lib.db

![Page 41](../assets/pages/page-041.jpg)

## 页面定位

- **页码**：41/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：估计互连延迟
- **阅读问题**：本页要回答：没有布局布线时，DC 如何估计 net delay？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文要点

> - set _wire_load_model -name “10*10” -library my_lib.db
> - current_design LOW
> - set_wire_load_model -name “10*10”
> - current_design TOP
> - set_wire_load_mode enclosed
> - set_wire_load_model -name “20*20MIN” -min

## 原文解读

本页展示 `set_wire_load_model` 和 `set_wire_load_mode` 的用法。脚本先对不同层次的 current_design 设置 wire load model，再在 TOP 上设置 enclosed mode，并指定 min 角的 wire load model。重点是：wire load model 可以按设计层次和工艺角分别指定。

本页关联的关键对象/命令：`set_wire_load_model`, `set_wire_load_mode`

## 我的理解

我的理解是：wire load model 是综合阶段对互连 RC 的早期估计。它不是库路径配置，而是影响 net delay 计算的模型选择；层次模式和 min/max 模型选错，会直接改变 timing 的乐观或悲观程度。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

层次化设计里要记录每个 current_design 使用的 wire load model，并确认 top/enclosed/segmented 模式与项目约定一致。

## 本页小结

本页的核心收获：- set _wire_load_model -name “10*10” -library my_lib.db 这一页应被理解为“估计互连延迟”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 040](page-040.md)
- 下一页：[Page 042](page-042.md)
