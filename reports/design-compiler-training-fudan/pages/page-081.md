# Page 081 - Setup and Hold Time Check

![Page 81](../assets/pages/page-081.jpg)

## 页面定位

- **页码**：81/112
- **所属阶段**：STA 与时序报告：路径、clock model、I/O 约束和 slack
- **本页角色**：建立 STA 基本概念
- **阅读问题**：本页要回答：一条 timing path 如何被定义、分组和检查？
- **前后关系**：这部分回答“如何判断结果是否真的满足时序”：看路径、看 required/arrival、看 slack。

## 原文摘录

> Setup and Hold Time Check
> - Setup Time: The length of time that data must stabilize
> before the clock transition.
> The maximum data path is used to determine if setup
> constraint is met.
> - Hold time: The length of time that data must remain stable
> at the input pin after the active clock transition.
> The minimum data path is used to determine if hold time is
> met.

## 图中内容理解

这页内容代表 STA 或时序建模。图中或文字中的 clock、data path、latency、uncertainty、arrival、required、slack 都属于同一套时间账本。要理解它，就要判断每个对象是在 launch 侧、capture 侧、data path 侧还是 required time 侧。

## 原文逐项解读

1. **原文**：`Setup and Hold Time Check`
   **解读**：这是 STA 基础。DC 把设计拆成 timing path，分别计算 arrival time、required time 和 slack。
2. **原文**：`- Setup Time: The length of time that data must stabilize`
   **解读**：这是 STA 基础。DC 把设计拆成 timing path，分别计算 arrival time、required time 和 slack。
3. **原文**：`before the clock transition.`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
4. **原文**：`The maximum data path is used to determine if setup`
   **解读**：这是 STA 基础。DC 把设计拆成 timing path，分别计算 arrival time、required time 和 slack。
5. **原文**：`constraint is met.`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。
6. **原文**：`- Hold time: The length of time that data must remain stable`
   **解读**：这是 STA 基础。DC 把设计拆成 timing path，分别计算 arrival time、required time 和 slack。
7. **原文**：`at the input pin after the active clock transition.`
   **解读**：这句话在提醒我们：DC 命令最终都作用在对象上。约束写得对不对，首先取决于选中了正确的 design、port、pin、net 或 cell。
8. **原文**：`The minimum data path is used to determine if hold time is`
   **解读**：这是 STA 基础。DC 把设计拆成 timing path，分别计算 arrival time、required time 和 slack。
9. **原文**：`met.`
   **解读**：这是本页的标题或核心术语，作用是给后面的命令、图示或公式定主题。

## 关键概念拆解

- **相关对象/命令**：本页以概念、结构或图示关系为主，没有需要死记的单一命令。
- **它在流程中的位置**：本页属于“STA 与时序报告：路径、clock model、I/O 约束和 slack”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“建立 STA 基本概念”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：STA 是综合结果的判卷过程。每个数字都应放入 arrival time 或 required time 的账本里看；只看 slack 会错过真正原因，必须追踪路径身份、clock model、data path delay 和约束扣减。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：读 timing report 要像查账。先看 Path Type 和 start/end，再看 clock 与 data 分别怎么算，最后才看 slack；这样才能知道该改约束、改逻辑还是改 clock model。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“Setup and Hold Time Check”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 080](page-080.md)
- 下一页：[Page 082](page-082.md)
