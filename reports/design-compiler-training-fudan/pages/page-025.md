# Page 025 - Set Operating Conditions

![Page 25](../assets/pages/page-025.jpg)

## 页面定位

- **页码**：25/112
- **所属阶段**：设计环境建模：工艺、负载、扇出和线负载
- **本页角色**：建模 PVT 环境
- **阅读问题**：本页要回答：当前设计被假设运行在什么 PVT/环境条件下？
- **前后关系**：这部分回答“模块外部世界是什么样”：输入驱动、输出负载、扇出和互连估计都会影响优化。

## 原文要点

> Set Operating Conditions
> - Operating condition model scales components
> delay, directs the optimizer to simulate variations
> in process, temperature and voltage
> - set_operating_conditions

## 原文解读

本页讲 operating conditions，用来模拟工艺、电压、温度变化对延迟和优化的影响。

本页关联的关键对象/命令：本页以概念/图示为主，重点看标题和图中对象关系。

## 我的理解

我的理解是：operating condition 是把“芯片在什么环境下工作”告诉 DC。不同 PVT 角下，cell delay 和优化选择都会变化。

把它放回完整 DC 流程里看，本页不是孤立知识点，而是在帮助我们更准确地描述“设计、环境、约束、优化结果”中的一个环节。读这一页时，我会优先问：它改变的是 DC 数据库里的哪个对象？它会让 compile 的优化空间变大还是变小？它最终应该在什么报告里被验证？

## 实操提醒

约束脚本要明确典型/慢速/快速角，不能默认环境就进入 signoff 式判断。

## 本页小结

本页的核心收获：Set Operating Conditions 这一页应被理解为“建模 PVT 环境”的读书笔记节点；掌握它的标准不是背下标题，而是能说明它如何影响后续约束、优化或 timing 报告。

## 导航

- 上一页：[Page 024](page-024.md)
- 下一页：[Page 026](page-026.md)
