# Page 106 - This partitioning is recommended due to:

![Page 106](../assets/pages/page-106.jpg)

## 页面定位

- **页码**：106/112
- **所属阶段**：Partitioning：层次划分、glue logic 和工程边界
- **本页角色**：改进设计分区
- **阅读问题**：本页要回答：如何划分 block 才能减少跨层级复杂度？
- **前后关系**：这部分把综合从命令层拉回架构层：分区方式会直接决定脚本复杂度、可测性和可收敛性。

## 原文摘录

> This partitioning is recommended due to:
> - Possible technology-dependent ( “black box”) I/O pad cells
> - Possible untestable “Divide By” clock generation
> - Possible technology-dependent JTAG circuitry

## 图中内容理解

这页说明推荐分区的原因。图中/文字中的 I/O pad、分频时钟、工艺相关单元代表不同工程属性：有些是黑盒，有些影响测试，有些依赖工艺库。它们不应随便混入普通逻辑 block。

## 原文逐项解读

1. **原文**：`This partitioning is recommended due to:`
   **解读**：这是工程组织与可维护性。分区、目录、脚本和帮助系统决定综合是否可复现、可调试。
2. **原文**：`- Possible technology-dependent ( “black box”) I/O pad cells`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
3. **原文**：`- Possible untestable “Divide By” clock generation`
   **解读**：这是 STA 基础。DC 把设计拆成 timing path，分别计算 arrival time、required time 和 slack。
4. **原文**：`- Possible technology-dependent JTAG circuitry`
   **解读**：这是标题下的一个子要点，通常在补充定义、适用对象、命令参数或注意事项。读时要把它和本页标题连起来。

## 关键概念拆解

- **相关对象/命令**：`partitioning`
- **它在流程中的位置**：本页属于“Partitioning：层次划分、glue logic 和工程边界”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“改进设计分区”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：后半部分把命令学习拉回工程组织。好的 partitioning、清晰目录、可复现脚本和会查帮助，决定这套 DC 流程能不能在真实项目里持续维护。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：项目越大，越不能只靠命令技巧。分区、目录、脚本和帮助系统要标准化，否则一次综合结果很难被别人复现和审查。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“This partitioning is recommended due to:”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 105](page-105.md)
- 下一页：[Page 107](page-107.md)
