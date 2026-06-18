# Page 028 - Setting Output Loading Capacitance (pF)

![Page 28](../assets/pages/page-028.jpg)

## 页面定位

- **页码**：28/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：建模输出负载
- **阅读问题**：本页要回答：输出端外部负载如何建模？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文要点

> Setting Output Loading Capacitance (pF)
> -set_load
> - set_load : Sets the load attribute to a specified
> value on specified ports and nets.
> - load_of: Returns the capacitance of the specified
> library cell pin.
> - Example:
> set MAX_LOAD [load_of slow/AND2X1/A]
> set_load [expr $MAX_LOAD*15] [all_outputs]

## 原文解读

本页讲 `set_load`。它在 port 或 net 上设置电容负载；`load_of` 可以从库单元 pin 读取电容，用来估算下游多个输入 pin 带来的总负载。

本页关联的关键对象/命令：`set_load`

## 我的理解

我的理解是：输出端负载决定当前模块需要多强的输出驱动。负载估小会让时序过于乐观，估大则可能迫使 DC 选择更大的 cell，带来面积和功耗增加。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

对 output port 写 `set_load` 时，把 pad、电容预算、下游输入 pin 数量分开核算，再合成脚本里的最终数值。

## 本页小结

本页的核心收获：Setting Output Loading Capacitance (pF) 这一页应被理解为“建模输出负载”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 027](page-027.md)
- 下一页：[Page 029](page-029.md)
