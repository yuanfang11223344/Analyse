# Page 093 - Startpoint: ARM7TDMI/debuger/tms_latch_reg/CKN

![Page 93](../assets/pages/page-093.jpg)

## 页面定位

- **页码**：93/112
- **所属阶段**：STA 与时序报告：路径、clock model、I/O 约束和 slack
- **本页角色**：拆解 timing report
- **阅读问题**：本页要回答：timing report 每一段数字从哪里来，slack 如何形成？
- **前后关系**：这部分回答“如何判断结果是否真的满足时序”：看路径、看 required/arrival、看 slack。

## 原文摘录

> Startpoint: ARM7TDMI/debuger/tms_latch_reg/CKN
> (internal path startpoint clocked by HCLK)
> Endpoint: ARM7TDMI/debuger/tms_s_reg
> (falling edge-triggered flip-flop clocked by HCLK)
> Path Group: HCLK
> Path Type: min
> Point Incr Path
> ------------------------------------------------------------------------------
> clock HCLK (fall edge) 6.00 6.00
> clock network delay (propagated) 0.87 6.87
> input external delay 0.00 6.87 f
> ARM7TDMI/debuger/tms_latch_reg/CKN (FFDNHD2X) 0.00 6.87 f
> ARM7TDMI/debuger/tms_latch_reg/Q (FFDNHD2X) <- 0.18 & 7.05 r
> ARM7TDMI/debuger/tms_s_reg/D (FFDNHD2X) 0.00 & 7.05 r
> data arrival time 7.05
> clock HCLK (fall edge) 6.00 6.00
> clock network delay (propagated) 0.87 6.87
> clock uncertainty 0.10 6.97
> ARM7TDMI/debuger/tms_s_reg/CKN (FFDNHD2X) 6.97 f
> library hold time 0.08 7.05
> data required time 7.05
> ------------------------------------------------------------------------------
> data required time 7.05
> data arrival time -7.05
> ------------------------------------------------------------------------------
> slack (MET) 0.00
> How to read timing report?

## 页面结构与图示分析

图中是一段完整 timing report。结构上先列 path information，再列 data arrival，再列 data required，最后给 slack。读报告时要像对账一样逐行追踪。

## 原文逐项解读

1. **原文**：`Startpoint: ARM7TDMI/debuger/tms_latch_reg/CKN`
   **解读**：Startpoint 是 timing path 的起点。这里起点是 `tms_latch_reg/CKN`，说明分析从这个寄存器/锁存器相关时钟 pin 开始，首先要确认它属于哪个 clock domain。
2. **原文**：`(internal path startpoint clocked by HCLK)`
   **解读**：括号说明 startpoint 是内部路径起点，并且受 HCLK 控制。这告诉我们该路径不是单纯输入端口路径，而是设计内部时序路径。
3. **原文**：`Endpoint: ARM7TDMI/debuger/tms_s_reg`
   **解读**：Endpoint 是 timing path 的终点。这里终点是 `tms_s_reg`，也就是数据最后要满足该寄存器的采样要求。
4. **原文**：`(falling edge-triggered flip-flop clocked by HCLK)`
   **解读**：括号说明 endpoint 是下降沿触发的触发器，并由 HCLK 驱动。因此后面的 required time 要按 HCLK 的 falling edge 关系来计算。
5. **原文**：`Path Group: HCLK`
   **解读**：Path Group 表示该路径被归入哪个时钟组。这里是 HCLK，说明优化和报告会按 HCLK 这个 timing group 组织。
6. **原文**：`Path Type: min`
   **解读**：Path Type 是 min，通常对应 hold/最小延迟检查。读这页时不能用 setup/max path 的直觉，而要关注数据是否太快到达。
7. **原文**：`Point Incr Path`
   **解读**：`Point` 是路径上的对象，`Incr` 是本点新增延迟，`Path` 是累计时间。读 timing report 时要沿着这一列像记账一样累加。
8. **原文**：`------------------------------------------------------------------------------`
   **解读**：这是报告中的分隔线，用来把 path information、data arrival、data required、summary 等区域分开。分隔线本身没有数值意义，但能帮助我们识别报告结构。
9. **原文**：`clock HCLK (fall edge) 6.00 6.00`
   **解读**：这一行建立 HCLK falling edge 的时间基准。两个数字通常表示该 clock edge 的增量和累计 path time，是后续 arrival/required 的起点。
10. **原文**：`clock network delay (propagated) 0.87 6.87`
   **解读**：clock network delay 是时钟网络传播延迟。`propagated` 表示这里使用的是传播后的 clock network delay，而不是完全理想时钟。
11. **原文**：`input external delay 0.00 6.87 f`
   **解读**：input external delay 表示外部输入侧已经建模的延迟。在这条报告中为 0.00，说明外部输入延迟没有额外占用时间。
12. **原文**：`ARM7TDMI/debuger/tms_latch_reg/CKN (FFDNHD2X) 0.00 6.87 f`
   **解读**：这是路径经过的时钟 pin。报告把具体层次路径和 cell 类型列出来，方便定位到底是哪一个实例参与了时序计算。
13. **原文**：`ARM7TDMI/debuger/tms_latch_reg/Q (FFDNHD2X) <- 0.18 & 7.05 r`
   **解读**：这是 startpoint 触发器/锁存器的输出 Q。`Incr` 中的 0.18 表示从时钟相关点到 Q 输出产生的数据延迟贡献。
14. **原文**：`ARM7TDMI/debuger/tms_s_reg/D (FFDNHD2X) 0.00 & 7.05 r`
   **解读**：这是 endpoint 触发器的数据输入 D。到达这里的累计时间就是数据到达 endpoint 的时间基础。
15. **原文**：`data arrival time 7.05`
   **解读**：data arrival time 是数据实际到达时间。它由 clock edge、clock network delay、外部 delay、cell/net delay 等逐步累加得到。
16. **原文**：`clock HCLK (fall edge) 6.00 6.00`
   **解读**：这一行建立 HCLK falling edge 的时间基准。两个数字通常表示该 clock edge 的增量和累计 path time，是后续 arrival/required 的起点。
17. **原文**：`clock network delay (propagated) 0.87 6.87`
   **解读**：clock network delay 是时钟网络传播延迟。`propagated` 表示这里使用的是传播后的 clock network delay，而不是完全理想时钟。
18. **原文**：`clock uncertainty 0.10 6.97`
   **解读**：clock uncertainty 是时钟不确定性/裕量。它会收紧 required time，使时序分析更保守。
19. **原文**：`ARM7TDMI/debuger/tms_s_reg/CKN (FFDNHD2X) 6.97 f`
   **解读**：这是路径经过的时钟 pin。报告把具体层次路径和 cell 类型列出来，方便定位到底是哪一个实例参与了时序计算。
20. **原文**：`library hold time 0.08 7.05`
   **解读**：library hold time 是目标库中触发器的 hold 要求。对 min/hold path 来说，它会加入 required time，要求数据不要过早变化。
21. **原文**：`data required time 7.05`
   **解读**：data required time 是数据必须满足的时间边界。slack 就是 required 与 arrival 的比较结果。
22. **原文**：`------------------------------------------------------------------------------`
   **解读**：这是报告中的分隔线，用来把 path information、data arrival、data required、summary 等区域分开。分隔线本身没有数值意义，但能帮助我们识别报告结构。
23. **原文**：`data required time 7.05`
   **解读**：data required time 是数据必须满足的时间边界。slack 就是 required 与 arrival 的比较结果。
24. **原文**：`data arrival time -7.05`
   **解读**：这里的负号是 timing report 汇总格式，用来执行 `required - arrival` 的 slack 计算。不是说 arrival time 本身为负，而是把 7.05 作为被减数列入汇总。
25. **原文**：`------------------------------------------------------------------------------`
   **解读**：这是报告中的分隔线，用来把 path information、data arrival、data required、summary 等区域分开。分隔线本身没有数值意义，但能帮助我们识别报告结构。
26. **原文**：`slack (MET) 0.00`
   **解读**：slack (MET) 表示该路径满足时序。这里 slack 为 0.00，说明刚好满足，没有额外裕量。
27. **原文**：`How to read timing report?`
   **解读**：这是本页提出的阅读任务：不是只看最后 slack，而是把 timing report 拆成路径身份、数据到达、数据要求和 slack 汇总四部分来读。

## 关键概念拆解

- **相关对象/命令**：`Startpoint`, `Endpoint`, `slack`
- **它在流程中的位置**：本页属于“STA 与时序报告：路径、clock model、I/O 约束和 slack”。这意味着它不是孤立知识点，而是在完整 DC 流程中承担“拆解 timing report”的作用。
- **要验证的地方**：学习完本页后，应能在脚本、设计对象或报告中找到对应证据；例如库是否加载、端口是否被约束、路径是否出现在 timing report、或优化结果是否反映在面积/时序报告里。

## 我的理解

我的理解是：这页是读 timing report 的范例。它不是在展示一堆数字，而是在展示一条 min/hold path 的完整时间账：先算 data arrival，再算 data required，最后得出 slack 0.00，说明刚好满足。

更具体地说，读这一页时我会把它拆成三层：第一层是原文在定义什么对象或命令；第二层是它改变了 DC 数据库中的哪个属性；第三层是这个改变会怎样影响后续 compile、report 或工程维护。只有把这三层连起来，才算真正读懂，而不是记住几个英文命令。

## 对我们的启示

对我们的启示：遇到 timing report，先不要问“slack 多少”，而要先问“这是 max 还是 min、start/end 是谁、clock 怎么算、data 怎么走”。这样 debug 才有方向。

如果把这页用于真实项目，我会把它转成一个检查问题：当前脚本有没有明确表达这一页要求的环境、约束或报告检查？如果没有，这就是后续综合结果不可信或难以复现的风险点。

## 本页小结

本页的核心不是“Startpoint: ARM7TDMI/debuger/tms_latch_reg/CKN”这个标题本身，而是理解它如何影响 DC 对设计的认识、优化空间和报告解释。复习时不要只背命令，要能说清：它作用于谁、设置什么、为什么需要、错了会导致什么后果。

## 导航

- 上一页：[Page 092](page-092.md)
- 下一页：[Page 094](page-094.md)
