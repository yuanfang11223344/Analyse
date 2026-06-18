# Page 013 - .synopsys_dc.setup example

![Page 13](../assets/pages/page-013.jpg)

## 页面定位

- **页码**：13/112
- **所属阶段**：前端准备：库、读入设计和 DC 对象模型
- **本页角色**：配置综合库
- **阅读问题**：本页要回答：DC 到哪里找库，最终映射到哪个目标库？
- **前后关系**：这部分回答“DC 如何认识设计”：库在哪里、RTL 如何读入、对象如何被引用。

## 原文摘录

> .synopsys_dc.setup example
> lappend search_path [list ./src ./scripts \
> /net/home/EDAs/synopsys/syn/libraries/syn\
> /net/sunb2i/export/home/xyzeng/xiaohao/fft_2k_4k_8k/dc/lib\
> ]
> set target_library "smic18_tt.db"
> set link_library " * $target_library smic18IO_line_tt.db\
> smic18IO_stagger_tt.db dw_foundation.sldb"
> set symbol_library " smic18.sdb "
> set synthetic_library " dw_foundation.sldb “
> ……

## 图中内容理解

这页内容代表 DC 的库/单位基础。图中或文字中的路径、库名、单位字段不是背景信息，而是在定义工具后续能使用哪些 cell、如何解释 delay/load/power 数值。对电路结构而言，库决定可选器件；对脚本而言，这些设置决定链接和映射是否可靠。

## 原文逐项解读

1. **原文**：`.synopsys_dc.setup example`
   **解读**：这是 DC 运行前最核心的库和路径环境。`search_path` 解决文件在哪里，`link_library` 解决引用如何链接，`target_library` 决定最终能用哪些标准单元实现逻辑。
2. **原文**：`lappend search_path [list ./src ./scripts \`
   **解读**：这是 DC 运行前最核心的库和路径环境。`search_path` 解决文件在哪里，`link_library` 解决引用如何链接，`target_library` 决定最终能用哪些标准单元实现逻辑。
3. **原文**：`/net/home/EDAs/synopsys/syn/libraries/syn\`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
4. **原文**：`/net/sunb2i/export/home/xyzeng/xiaohao/fft_2k_4k_8k/dc/lib\`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
5. **原文**：`]`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
6. **原文**：`set target_library "smic18_tt.db"`
   **解读**：这是 DC 运行前最核心的库和路径环境。`search_path` 解决文件在哪里，`link_library` 解决引用如何链接，`target_library` 决定最终能用哪些标准单元实现逻辑。
7. **原文**：`set link_library " * $target_library smic18IO_line_tt.db\`
   **解读**：这是 DC 运行前最核心的库和路径环境。`search_path` 解决文件在哪里，`link_library` 解决引用如何链接，`target_library` 决定最终能用哪些标准单元实现逻辑。
8. **原文**：`smic18IO_stagger_tt.db dw_foundation.sldb"`
   **解读**：这是 STA 基础。DC 把设计拆成 timing path，分别计算 arrival time、required time 和 slack。
9. **原文**：`set symbol_library " smic18.sdb "`
   **解读**：这句话给出本页概念的定义、条件或结论。理解时要把主语、动作和作用对象拆开：谁被设置、什么属性被改变、后续哪类优化或报告会受影响。
10. **原文**：`set synthetic_library " dw_foundation.sldb “`
   **解读**：这句话给出本页概念的定义、条件或结论。理解时要把主语、动作和作用对象拆开：谁被设置、什么属性被改变、后续哪类优化或报告会受影响。
11. **原文**：`……`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。

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

本页的核心不是“.synopsys_dc.setup example”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 012](page-012.md)
- 下一页：[Page 014](page-014.md)
