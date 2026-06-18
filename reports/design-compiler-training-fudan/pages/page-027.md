# Page 027 - Set Input Pulling Resistance (khoms)

![Page 27](../assets/pages/page-027.jpg)

## 页面定位

- **页码**：27/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：建模输入驱动
- **阅读问题**：本页要回答：如何用具体库单元描述输入端外部驱动？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文要点

> Set Input Pulling Resistance (khoms)
> - set_drive
> - set_drive_cell : sets attributes on input or inout
> ports of the current design that specify that a
> library cell or output pin of a library cell drives the
> specified ports.
> - set_driving_cell -lib_cell AND2 {IN1}
> - set_driving_cell -lib_cell INV -pin Z \
> -library tech_lib [all_inputs]
> - set_driving_cell -lib_cell INV -don’t_scale {IN1}
> - set_driving_cell -rise -lib_cell BUF1_TS -pin Z {IN1}
> - set_driving_cell -fall -lib_cell DFF_TS -pin Q {IN1}

## 原文解读

本页讲 `set_driving_cell` / `set_drive_cell` 思路：不用抽象电阻，而是指定某个 library cell 或它的输出 pin 来驱动当前设计的输入端口。这样 DC 可以用更接近真实上游单元的 transition/delay 模型。

本页关联的关键对象/命令：`set_drive`, `set_drive_cell`

## 我的理解

我的理解是：当上游逻辑已知时，用 driving cell 比手填电阻更可追溯。它把“外部谁在驱动我”建模成具体库单元，而不是一个孤立数字。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

不要同时给同一输入端口叠加互相矛盾的 `set_drive` 和 `set_driving_cell`；约束脚本里要保留建模来源。

## 本页小结

本页的核心收获：Set Input Pulling Resistance (khoms) 这一页应被理解为“建模输入驱动”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 026](page-026.md)
- 下一页：[Page 028](page-028.md)
