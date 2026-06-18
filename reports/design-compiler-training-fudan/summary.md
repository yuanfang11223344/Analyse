# Design Compiler Training Fudan - 总结（逐页读书笔记版）

## 本次重构说明

上一版按 20 页分块并使用 contact sheet，适合快速概览，但不适合逐页学习。这一版改为 112 个单页读书笔记：每页都保留原始截图，并按“页面定位、原文要点、原文解读、我的理解、实操提醒、本页小结”组织。

## 全书主线

这份课件的核心不是命令罗列，而是 Design Compiler 的完整综合闭环：先配置库并读入设计，再描述外部环境和约束，随后 compile/map/optimize，最后用 STA 和各类 report 验证结果。前半部分回答“DC 如何认识设计和环境”，中段回答“我们如何告诉 DC 目标和底线”，后半部分回答“如何判断综合结果是否满足时序”，最后落到 partitioning 和工程目录组织。

## 重点理解

1. **库决定可实现空间**：`target_library` 决定最终能映射到哪些标准单元，`link_library` 决定引用如何解析。库配置错误时，后续优化没有可靠基础。
2. **约束是系统预算的表达**：`create_clock`、`set_input_delay`、`set_output_delay`、`set_max_delay`、`set_min_delay` 都是在把系统级时间关系写入模块级综合。
3. **设计规则优先于优化目标**：max transition、max capacitance、max fanout 等规则是底线，DC 会优先修复这些问题。
4. **STA 是综合结果的判卷系统**：读 timing report 要分清 path information、path delay、path required、summary；只看 slack 不够。
5. **Partitioning 决定工程可收敛性**：好的 block 边界减少 glue logic，让约束、优化、验证都更清楚。

## 推荐阅读顺序

- 第 1-11 页：先建立综合流程总图。
- 第 12-22 页：理解库、设计读入和对象模型。
- 第 23-42 页：理解 operating condition、drive、load、fanout、wire load。
- 第 43-62 页：理解 design rule、timing/area constraint 和约束优先级。
- 第 63-72 页：理解 compile、逻辑优化、门级映射和报告。
- 第 73-99 页：重点读 STA、I/O delay、clock model、timing report。
- 第 100-112 页：把知识落到 partitioning、目录组织和帮助系统。

## 输出文件

- [逐页索引](INDEX.md)
- [合并版逐页读书笔记](page-by-page-notes.md)
- [单页笔记目录](pages/)
- [单页截图目录](assets/pages/)
