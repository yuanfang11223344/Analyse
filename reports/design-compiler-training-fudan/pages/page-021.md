# Page 021 - Unit in Standard Library

![Page 21](../assets/pages/page-021.jpg)

## 页面定位

- **页码**：21/112
- **所属阶段**：前端准备：库、读入设计和 DC 对象模型
- **本页角色**：确认库单位
- **阅读问题**：本页要回答：标准库中的时间、电压、电流、负载单位如何影响约束数值？
- **前后关系**：这部分回答“DC 如何认识设计”：库在哪里、RTL 如何读入、对象如何被引用。

## 原文要点

> Unit in Standard Library
> -time_unit: “1ns”
> -voltage_unit: “1V”
> -Current_unit: “1mA”
> -pulling_resistance_unit: “1kohm”
> -Leakage_power_unit: “1pW”
> -Capacitive_load_unit: “1pF”

## 原文解读

本页列出标准库中的基本单位：time、voltage、current、pulling resistance、leakage power、capacitive load。DC 后续所有 delay、load、drive、power 数值都要按这些库单位解释。

本页关联的关键对象/命令：本页以概念/图示为主，重点看标题和图中对象关系。

## 我的理解

我的理解是：单位是阅读约束和报告的底层语境。`set_load 2`、`create_clock -period 10` 这类数值只有放到库单位里才有真实含义。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

导入新工艺库后先确认 library unit，再写 clock period、input/output delay、set_load 和 set_drive。

## 本页小结

本页的核心收获：Unit in Standard Library 这一页应被理解为“确认库单位”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 020](page-020.md)
- 下一页：[Page 022](page-022.md)
