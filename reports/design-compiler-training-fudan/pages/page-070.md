# Page 070 - Sequential Mapping

![Page 70](../assets/pages/page-070.jpg)

## 页面定位

- **页码**：70/112
- **所属阶段**：综合优化：逻辑优化、映射、compile 与报告
- **本页角色**：执行优化和映射
- **阅读问题**：本页要回答：DC 如何从逻辑表达变成目标库门级实现？
- **前后关系**：这部分回答“DC 如何改变电路”：从布尔级、门级到时序驱动优化。

## 原文摘录

> Sequential Mapping
> - Optimize the mapping
> to sequential cells
> from technology
> library.
> - Analyze combinational
> surrounding a
> sequential cell to see if
> it can absorb the logic
> attribute with HDL.
> - Try to save speed and
> area by using a more
> complex sequential
> cell.

## 图中内容理解

这页内容代表综合优化过程。图中或命令表达的是 DC 如何把抽象逻辑变成目标库单元：逻辑重构、flatten/structure、组合映射、时序单元映射和 effort 选择都会改变最终电路结构。

## 原文逐项解读

1. **原文**：`Sequential Mapping`
   **解读**：这是综合优化和映射。DC 会在逻辑结构、目标库单元和时序目标之间做取舍，最终生成门级实现。
2. **原文**：`- Optimize the mapping`
   **解读**：这是综合优化和映射。DC 会在逻辑结构、目标库单元和时序目标之间做取舍，最终生成门级实现。
3. **原文**：`to sequential cells`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
4. **原文**：`from technology`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
5. **原文**：`library.`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
6. **原文**：`- Analyze combinational`
   **解读**：这是把 RTL 变成 DC 内部设计数据库的步骤。关键不只是读文件，而是建立层次、解析引用，并确认当前操作对象。
7. **原文**：`surrounding a`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
8. **原文**：`sequential cell to see if`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
9. **原文**：`it can absorb the logic`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
10. **原文**：`attribute with HDL.`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
11. **原文**：`- Try to save speed and`
   **解读**：这是标题下的一个子要点，通常在补充定义、适用对象、命令参数或注意事项。读时要把它和本页标题连起来。
12. **原文**：`area by using a more`
   **解读**：这是优化目标或优先级。它告诉我们 DC 在多个目标冲突时先满足什么、后优化什么。
13. **原文**：`complex sequential`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
14. **原文**：`cell.`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。

## 关键概念拆解

- **相关对象/命令**：`analyze`
- **它在流程中的位置**：本页属于“综合优化：逻辑优化、映射、compile 与报告”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“执行优化和映射”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：compile 并不是一个黑盒按钮，它会根据约束和库模型在逻辑级、门级、时序路径上做取舍。理解本页，就是理解 DC 为什么会改变结构、选择更大 cell、flatten 层次或使用复杂 sequential cell。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：优化选项要跟报告闭环。改 `compile` 选项、flatten/structure 或 effort 前后，都要比较 timing、area、DRC 和层次变化，而不是凭感觉调工具。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“Sequential Mapping”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 069](page-069.md)
- 下一页：[Page 071](page-071.md)
