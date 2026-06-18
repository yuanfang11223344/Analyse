# Page 110 - How to start DC

![Page 110](../assets/pages/page-110.jpg)

## 页面定位

- **页码**：110/112
- **所属阶段**：工程使用：启动 DC、项目目录和帮助系统
- **本页角色**：建立工程运行习惯
- **阅读问题**：本页要回答：如何把 DC 使用变成可复现、可查询的工程流程？
- **前后关系**：最后几页强调可复现工程习惯：脚本启动、目录组织、查帮助。

## 原文要点

> How to start DC
> 1 unix/linux> dc_shell-t
> dc_shell> source scripts/xx.tcl -e -v
> 2 unix/linux> dc_shell –f scripts/xx.tcl (|tee ./log/run.log)
> 3 unix/linux> design_vision
> design_vision> source scripts/xx.tcl -e -v

## 原文解读

本页讲启动 DC 的两种方式：交互进入 `dc_shell-t` 后 source 脚本，或直接 `dc_shell -f scripts/xx.tcl` 并 tee 日志。

本页关联的关键对象/命令：`dc_shell`

## 我的理解

我的理解是：学习可以交互式试命令，工程运行必须脚本化和日志化，否则结果不可复现。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

推荐固定入口脚本和 log 路径，保留每次 run 的报告。

## 本页小结

本页的核心收获：How to start DC 这一页应被理解为“建立工程运行习惯”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 109](page-109.md)
- 下一页：[Page 111](page-111.md)
