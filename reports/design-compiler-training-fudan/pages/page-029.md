# Page 029 - Setting Output Loading Capacitance (pF)

![Page 29](../assets/pages/page-029.jpg)

## 页面定位

- **页码**：29/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：建模输出负载
- **阅读问题**：本页要回答：输出端外部负载如何建模？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文摘录

> Setting Output Loading Capacitance (pF)
> -set_load
> - set _load 2 in1
> - set port_load [expr 2.5+3*[load_of tech_lib/IV/A]]
> - set_load $port_load [all_outputs]
> - set_load [load_of tech_lib/IV/Z] {input_1 inoput_2}

## 页面结构与图示分析

本页主要是文字/命令列表结构。阅读顺序应从标题开始，再看项目符号或命令示例：标题给主题，项目符号给定义和限制，命令示例说明如何在 dc_shell 中落地。

## 原文逐项解读

1. **原文**：`Setting Output Loading Capacitance (pF)`
   **解读**：这是输出负载建模。它告诉 DC 输出端要推动多大的电容负载，直接影响输出 cell sizing、transition、delay、面积和功耗。
2. **原文**：`-set_load`
   **解读**：这是输出负载建模。它告诉 DC 输出端要推动多大的电容负载，直接影响输出 cell sizing、transition、delay、面积和功耗。
3. **原文**：`- set _load 2 in1`
   **解读**：这是标题下的一个子要点，通常在补充定义、适用对象、命令参数或注意事项。读时要把它和本页标题连起来。
4. **原文**：`- set port_load [expr 2.5+3*[load_of tech_lib/IV/A]]`
   **解读**：这是输出负载建模。它告诉 DC 输出端要推动多大的电容负载，直接影响输出 cell sizing、transition、delay、面积和功耗。
5. **原文**：`- set_load $port_load [all_outputs]`
   **解读**：这是输出负载建模。它告诉 DC 输出端要推动多大的电容负载，直接影响输出 cell sizing、transition、delay、面积和功耗。
6. **原文**：`- set_load [load_of tech_lib/IV/Z] {input_1 inoput_2}`
   **解读**：这是输出负载建模。它告诉 DC 输出端要推动多大的电容负载，直接影响输出 cell sizing、transition、delay、面积和功耗。

## 关键概念拆解

- **相关对象/命令**：`set_load`
- **它在流程中的位置**：本页属于“设计环境建模：工艺、负载、扇出和线负载”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“建模输出负载”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：这一页属于 design environment。环境建模不是“外围杂项”，而是在告诉 DC 当前模块外部世界长什么样。输入驱动、输出负载、fanout、wire load 和 PVT 会共同决定 delay、transition、cell sizing 与优化压力。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：模块级综合必须主动补全外部世界。不要默认输入是理想驱动、输出没有负载、互连没有延迟；这些偷懒会让时序结果过于乐观。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“Setting Output Loading Capacitance (pF)”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 028](page-028.md)
- 下一页：[Page 030](page-030.md)
