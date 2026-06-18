# Page 037 - Wire Load Model

![Page 37](../assets/pages/page-037.jpg)

## 页面定位

- **页码**：37/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：估计互连延迟
- **阅读问题**：本页要回答：没有布局布线时，DC 如何估计 net delay？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文要点

> Wire Load Model
> - A wire load model is an estimate of a net’s RC
> parasitics based on the net’s fanout.
> Example: dc_shell-t> set_wire_load_model 10x10

## 原文解读

本页定义 wire load model：在还没有真实布局布线 RC 的综合阶段，根据 net 的 fanout 估计互连寄生参数。`set_wire_load_model` 用来指定这种估计模型。

本页关联的关键对象/命令：`set_wire_load_model`, `set_wire_load_mode`, `dc_shell`

## 我的理解

我的理解是：wire load model 是早期综合对物理互连的近似。它利用 fanout 推测线长和 RC，因此 fanout 不只是规则统计，也会间接影响 net delay 估算。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

在没有后端寄生参数前，检查 wire load model 是否匹配设计规模；过于乐观或悲观都会影响 timing 优化方向。

## 本页小结

本页的核心收获：Wire Load Model 这一页应被理解为“估计互连延迟”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 036](page-036.md)
- 下一页：[Page 038](page-038.md)
