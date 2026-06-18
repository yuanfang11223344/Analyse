# Page 072 - How to generate results and report

![Page 72](../assets/pages/page-072.jpg)

## 页面定位

- **页码**：72/112
- **所属阶段**：综合优化：逻辑优化、映射、compile 与报告
- **本页角色**：理解优化目标和优先级
- **阅读问题**：本页要回答：这个概念/命令在流程中解决什么问题？
- **前后关系**：这部分回答“DC 如何改变电路”：从布尔级、门级到时序驱动优化。

## 原文摘录

> How to generate results and report
> attributes for synthesis
> - Attributes to Report
> report_design, report_clock, report_port,
> report_net, report_hierarch, report_area,
> report_reference, report_constraint
> - Results to generate
> write –output –format ddc mapped.ddc
> write –output –format verilog mapped.v
> write_sdc mapped.sdc
> write_sdf mapped.sdf

## 图中内容理解

这页内容代表约束模型。图中或命令表达的不是电路功能，而是 DC 必须满足的边界条件：哪些是硬性 design rule，哪些是 timing budget，哪些是面积/速度目标。综合时电路结构会围绕这些目标被重写。

## 原文逐项解读

1. **原文**：`How to generate results and report`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
2. **原文**：`attributes for synthesis`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
3. **原文**：`- Attributes to Report`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
4. **原文**：`report_design, report_clock, report_port,`
   **解读**：这是检查和验证阶段。报告不是附属品，而是确认设计环境、约束和优化结果是否正确的证据。
5. **原文**：`report_net, report_hierarch, report_area,`
   **解读**：这是优化目标或优先级。它告诉我们 DC 在多个目标冲突时先满足什么、后优化什么。
6. **原文**：`report_reference, report_constraint`
   **解读**：这是检查和验证阶段。报告不是附属品，而是确认设计环境、约束和优化结果是否正确的证据。
7. **原文**：`- Results to generate`
   **解读**：这是标题下的一个子要点，通常在补充定义、适用对象、命令参数或注意事项。读时要把它和本页标题连起来。
8. **原文**：`write –output –format ddc mapped.ddc`
   **解读**：这句话给出本页概念的定义、条件或结论。理解时要把主语、动作和作用对象拆开：谁被设置、什么属性被改变、后续哪类优化或报告会受影响。
9. **原文**：`write –output –format verilog mapped.v`
   **解读**：这句话给出本页概念的定义、条件或结论。理解时要把主语、动作和作用对象拆开：谁被设置、什么属性被改变、后续哪类优化或报告会受影响。
10. **原文**：`write_sdc mapped.sdc`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
11. **原文**：`write_sdf mapped.sdf`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。

## 关键概念拆解

- **相关对象/命令**：本页以概念、结构或图示关系为主，没有需要死记的单一命令。
- **它在流程中的位置**：本页属于“综合优化：逻辑优化、映射、compile 与报告”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“理解优化目标和优先级”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：约束是在给 DC 写合同。design rule 是必须满足的底线，timing constraint 是系统预算的分配，area 等目标是优化偏好。脚本写约束时必须分清这些约束的优先级和作用对象。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：约束要能解释来源。每个 clock、delay、load、max rule 都应该能回答“来自系统需求、工艺库、接口协议还是经验假设”。无法解释来源的约束，后期很难 debug。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“How to generate results and report”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 071](page-071.md)
- 下一页：[Page 073](page-073.md)
