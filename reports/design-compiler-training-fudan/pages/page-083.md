# Page 083 - Clock Tree Modeling

![Page 83](../assets/pages/page-083.jpg)

## 页面定位

- **页码**：83/112
- **所属阶段**：STA 与时序报告：路径、clock model、I/O 约束和 slack
- **本页角色**：建模时钟网络
- **阅读问题**：本页要回答：clock latency/uncertainty 如何影响 setup/hold？
- **前后关系**：这部分回答“如何判断结果是否真的满足时序”：看路径、看 required/arrival、看 slack。

## 原文摘录

> Clock Tree Modeling
> - Two parameter to model:
> - Specify clock network latency
> - set_clock_latency –rise tr –fall tf [get_ports TCK]
> - Specify uncertainty(skew) of clock network
> - set_clock_uncertainty –rise tp –fall tm [get_ports TCK]

## 图中内容理解

这页内容代表 STA 或时序建模。图中或文字中的 clock、data path、latency、uncertainty、arrival、required、slack 都属于同一套时间账本。要理解它，就要判断每个对象是在 launch 侧、capture 侧、data path 侧还是 required time 侧。

## 原文逐项解读

1. **原文**：`Clock Tree Modeling`
   **解读**：这是时钟网络建模。latency 描述时钟到达延迟，uncertainty 描述抖动、偏斜或保守裕量，它们会改变 setup/hold 判断。
2. **原文**：`- Two parameter to model:`
   **解读**：这是标题下的一个子要点，通常在补充定义、适用对象、命令参数或注意事项。读时要把它和本页标题连起来。
3. **原文**：`- Specify clock network latency`
   **解读**：这是时钟网络建模。latency 描述时钟到达延迟，uncertainty 描述抖动、偏斜或保守裕量，它们会改变 setup/hold 判断。
4. **原文**：`- set_clock_latency –rise tr –fall tf [get_ports TCK]`
   **解读**：这是时钟网络建模。latency 描述时钟到达延迟，uncertainty 描述抖动、偏斜或保守裕量，它们会改变 setup/hold 判断。
5. **原文**：`- Specify uncertainty(skew) of clock network`
   **解读**：这是时钟网络建模。latency 描述时钟到达延迟，uncertainty 描述抖动、偏斜或保守裕量，它们会改变 setup/hold 判断。
6. **原文**：`- set_clock_uncertainty –rise tp –fall tm [get_ports TCK]`
   **解读**：`set_clock_uncertainty` 建模 clock skew、jitter 或保守裕量。uncertainty 会收紧时序要求，因此数值越大，timing 越难满足。

## 关键概念拆解

- **相关对象/命令**：`set_clock_latency`, `set_clock_uncertainty`
- **它在流程中的位置**：本页属于“STA 与时序报告：路径、clock model、I/O 约束和 slack”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“建模时钟网络”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：STA 是综合结果的判卷过程。每个数字都应放入 arrival time 或 required time 的账本里看；只看 slack 会错过真正原因，必须追踪路径身份、clock model、data path delay 和约束扣减。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：读 timing report 要像查账。先看 Path Type 和 start/end，再看 clock 与 data 分别怎么算，最后才看 slack；这样才能知道该改约束、改逻辑还是改 clock model。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“Clock Tree Modeling”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 082](page-082.md)
- 下一页：[Page 084](page-084.md)
