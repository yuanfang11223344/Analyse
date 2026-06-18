# Page 026 - Set Input Pulling Resistance (khoms)

![Page 26](../assets/pages/page-026.jpg)

## 页面定位

- **页码**：26/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：建模输入驱动
- **阅读问题**：本页要回答：输入端外部驱动能力如何建模？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文要点

> Set Input Pulling Resistance (khoms)
> - set_drive
> - set_drive : Sets the rise_drive or fall_drive
> attributes to specified resistance values on
> specified input and inout ports.
> - set_drive 2 .0 {A B C}; or set_drive 2 .0 “A B C”;
> - set_drive 2 [all_inputs];
> - set_drive -rise 1 [get_ports B];
> - set_drive -rise drive_of(-rise TECH_LIBRARY/INVERTER/OUT) \
> [get_ports C]
>  drive_of : Returns the drive resistance value of the
> specified library cell pin.

## 原文解读

本页讲 `set_drive`。它在 input/inout port 上设置 rise_drive 或 fall_drive，相当于用电阻值描述外部电路驱动当前模块输入的能力；`drive_of` 可以从库单元 pin 上读取驱动电阻作为参考。

本页关联的关键对象/命令：`set_drive`

## 我的理解

我的理解是：输入端不是理想信号源。外部驱动越弱，输入 transition 越慢，内部 delay 和 design rule 检查都会受影响。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

对输入端口建模时，要确认是用固定 resistance，还是用库单元 pin 的 `drive_of` 作为外部驱动模型。

## 本页小结

本页的核心收获：Set Input Pulling Resistance (khoms) 这一页应被理解为“建模输入驱动”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 025](page-025.md)
- 下一页：[Page 027](page-027.md)
