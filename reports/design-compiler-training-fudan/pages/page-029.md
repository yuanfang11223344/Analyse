# Page 029 - Setting Output Loading Capacitance (pF)

![Page 29](../assets/pages/page-029.jpg)

## 页面定位

- **页码**：29/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：建模输出负载
- **阅读问题**：本页要回答：输出端外部负载如何建模？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文要点

> Setting Output Loading Capacitance (pF)
> -set_load
> - set _load 2 in1
> - set port_load [expr 2.5+3*[load_of tech_lib/IV/A]]
> - set_load $port_load [all_outputs]
> - set_load [load_of tech_lib/IV/Z] {input_1 inoput_2}

## 原文解读

本页讲输出负载建模。`set_load` 给端口或 net 设置电容负载，影响输出 cell sizing、transition 和 delay。

本页关联的关键对象/命令：`set_load`

## 我的理解

我的理解是：输出端连接了外部逻辑，DC 必须知道要推动多重的负载；负载估小会得到乐观时序，估大会增加面积和功耗压力。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

对 output port 写约束时，把 pad、下游输入 pin、电容预算分别核清楚。

## 本页小结

本页的核心收获：Setting Output Loading Capacitance (pF) 这一页应被理解为“建模输出负载”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 028](page-028.md)
- 下一页：[Page 030](page-030.md)
