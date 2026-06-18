# Page 012 - Library Specification

![Page 12](../assets/pages/page-012.jpg)

## 页面定位

- **页码**：12/112
- **所属阶段**：前端准备：库、读入设计和 DC 对象模型
- **本页角色**：配置综合库
- **阅读问题**：本页要回答：DC 到哪里找库，最终映射到哪个目标库？
- **前后关系**：这部分回答“DC 如何认识设计”：库在哪里、RTL 如何读入、对象如何被引用。

## 原文摘录

> Library Specification
> - search_path: the path to search for unsolved reference
> library or design.
> - link_library: the library used for interpreting input
> description, any cells instantiated in your HDL code,
> Wire Load or Operating Condition models used during
> synthesis.
> - target_library: the ASIC technology that the design
> map to.
> - symbol_library: Used during schematic generation.
> - synthetic_library: designware library to be used. (IP)
> You can write them to .synopsys_dc.setup file.

## 页面结构与图示分析

本页主要是文字/命令列表结构。阅读顺序应从标题开始，再看项目符号或命令示例：标题给主题，项目符号给定义和限制，命令示例说明如何在 dc_shell 中落地。

## 原文逐项解读

1. **原文**：`Library Specification`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
2. **原文**：`- search_path: the path to search for unsolved reference`
   **解读**：这是 DC 运行前最核心的库和路径环境。`search_path` 解决文件在哪里，`link_library` 解决引用如何链接，`target_library` 决定最终能用哪些标准单元实现逻辑。
3. **原文**：`library or design.`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
4. **原文**：`- link_library: the library used for interpreting input`
   **解读**：这是 DC 运行前最核心的库和路径环境。`search_path` 解决文件在哪里，`link_library` 解决引用如何链接，`target_library` 决定最终能用哪些标准单元实现逻辑。
5. **原文**：`description, any cells instantiated in your HDL code,`
   **解读**：这是 STA 基础。DC 把设计拆成 timing path，分别计算 arrival time、required time 和 slack。
6. **原文**：`Wire Load or Operating Condition models used during`
   **解读**：这是工艺、电压、温度环境建模。它会改变 cell delay 和优化判断，不能当作无关背景。
7. **原文**：`synthesis.`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
8. **原文**：`- target_library: the ASIC technology that the design`
   **解读**：这是 DC 运行前最核心的库和路径环境。`search_path` 解决文件在哪里，`link_library` 解决引用如何链接，`target_library` 决定最终能用哪些标准单元实现逻辑。
9. **原文**：`map to.`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
10. **原文**：`- symbol_library: Used during schematic generation.`
   **解读**：这是标题下的一个子要点，通常在补充定义、适用对象、命令参数或注意事项。读时要把它和本页标题连起来。
11. **原文**：`- synthetic_library: designware library to be used. (IP)`
   **解读**：这是标题下的一个子要点，通常在补充定义、适用对象、命令参数或注意事项。读时要把它和本页标题连起来。
12. **原文**：`You can write them to .synopsys_dc.setup file.`
   **解读**：这是 DC 运行前最核心的库和路径环境。`search_path` 解决文件在哪里，`link_library` 解决引用如何链接，`target_library` 决定最终能用哪些标准单元实现逻辑。

## 关键概念拆解

- **相关对象/命令**：`search_path`, `link_library`, `target_library`
- **它在流程中的位置**：本页属于“前端准备：库、读入设计和 DC 对象模型”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“配置综合库”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：DC 的所有判断都站在库模型之上。库不仅提供门级单元，还定义延迟、负载、功耗和单位体系；如果库路径、链接库、目标库或单位理解错，后面看似精确的 timing/area 报告都会变成错误前提上的计算。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：写 DC 脚本时，第一步不是急着 compile，而是先把库、单位和链接关系查清楚，并在报告中验证库确实被正确加载。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“Library Specification”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 011](page-011.md)
- 下一页：[Page 013](page-013.md)
