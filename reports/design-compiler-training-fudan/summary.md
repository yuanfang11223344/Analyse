# Design Compiler Training Fudan 总报告

**源文件**：`/Users/ganxuanzhi/学习/DC综合学习文件/eetop.cn_Design_Compiler_Traning_Fudan.pdf`  
**页数**：112 页  
**材料来源**：Fudan University, School of Microelectronics, State Key Lab of ASIC & System  
**作者/署名**：JoyShockley  
**PDF 元数据**：PowerPoint 2007 导出，创建时间 2014-02-15  
**处理日期**：2026-06-17  
**处理方式**：分 6 批抽取文本 + 缩略图拼板检查 + 中文学习笔记 + 总结  

---

## 中文摘要

这份资料是一套 Design Compiler 入门培训幻灯片，主线是从 RTL 进入 DC 综合流程：先设置库和设计对象，再定义设计环境，然后写设计规则约束和优化约束，执行 compile，读 STA/timing report，最后讨论 partitioning、项目目录和工具启动方式。

它不是一本完整命令手册，而是一份“综合流程地图”。最有价值的地方在于帮学习者建立 DC 的工作顺序：库和对象是基础，environment 描述外部世界，constraints 描述目标和边界，compile 是优化动作，report_timing 是判断结果是否收敛的证据。

## 全局结构

| 页码 | 主题 | 学习目标 |
|---:|---|---|
| 1-20 | 基本流程、库、读设计、对象 | 知道 DC 综合从哪里开始，库和对象如何进入工具数据库 |
| 21-40 | 设计环境 | 学会建模 PVT、输入驱动、输出负载、fanout 和 wire load |
| 41-60 | 设计规则和优化约束 | 区分硬性 design rule 和 timing/area 等优化目标 |
| 61-80 | compile 和 STA 基础 | 理解逻辑优化、门级映射、报告输出和 timing path |
| 81-100 | STA 细节和 timing report | 学会 setup/hold、clock modeling 和 report_timing 阅读 |
| 101-112 | partitioning 和工程使用 | 认识分区原则、避免 glue logic、启动 DC 和管理项目目录 |

## 核心知识链路

```text
HDL/RTL
  -> read/analyze/elaborate
  -> link/uniquify
  -> library + design objects
  -> design environment
  -> design rule constraints
  -> optimization constraints
  -> compile
  -> reports + mapped netlist + SDC/SDF
  -> timing closure iteration
```

## 关键结论

1. **DC 是约束驱动的综合器**  
   你给目标和边界，工具根据目标做优化。没有约束的综合结果没有工程意义。

2. **库设置是第一道关**  
   `target_library` 决定能映射到哪些 cell；`link_library` 决定引用能否解析。这里错了，后续 timing 和 area 都没有意义。

3. **Design environment 和 constraints 不是一回事**  
   `set_drive`、`set_load`、`set_operating_conditions` 描述外部世界；`set_max_transition`、`create_clock`、`set_input_delay`、`set_max_area` 描述规则和目标。

4. **设计规则约束优先级高于优化目标**  
   transition、fanout、capacitance 等 design rule 往往必须优先满足，即使牺牲 timing 或 area。

5. **Compile 同时包含逻辑级和门级优化**  
   `structure`、`flatten` 改变逻辑表达；mapping、buffering、resizing、cloning 在目标库层面改善结果。

6. **STA 是判断综合质量的主要证据**  
   最终要读 `report_timing`，看 startpoint、endpoint、path type、arrival、required 和 slack。

7. **Partitioning 是综合可控性的工程基础**  
   好的 block 划分能减少 glue logic，降低跨边界优化困难，让每个模块更容易收敛。

## 术语对照表

| 英文术语 | 中文解释 | 记忆方式 |
|---|---|---|
| Design Compiler, DC | Synopsys 逻辑综合工具 | RTL 到门级网表 |
| `target_library` | 目标工艺库 | 工具能“用什么门” |
| `link_library` | 链接库 | 工具能“找到什么引用” |
| `synthetic_library` | 综合库/DesignWare 库 | 高级 IP 或运算组件 |
| `analyze` | 分析 HDL | 类似编译前端 |
| `elaborate` | 展开设计 | 建立层次和逻辑 |
| `link` | 解析引用 | 让模块和库单元闭合 |
| `uniquify` | 层次唯一化 | 多实例拆成独立副本 |
| Operating condition | 工作条件 | PVT 角落 |
| `set_drive` | 输入驱动建模 | 外部驱动电阻 |
| `set_driving_cell` | 输入驱动单元建模 | 外部由哪个 cell 驱动 |
| `set_load` | 输出电容负载 | 输出接了多大电容 |
| `set_fanout_load` | 外部 fanout 负载 | 无量纲 fanout 贡献 |
| `set_max_fanout` | 最大 fanout 约束 | 设计规则目标 |
| Wire Load Model | 线负载模型 | pre-layout 估算 net RC |
| Design rule constraint | 设计规则约束 | 硬规则 |
| Optimization constraint | 优化约束 | timing/area 等目标 |
| `create_clock` | 创建时钟 | 同步 timing 的根 |
| `set_input_delay` | 输入延迟约束 | 外部到输入端占用的时间 |
| `set_output_delay` | 输出延迟约束 | 输出到外部占用的时间 |
| `compile` | 综合优化 | 逻辑优化 + 门级映射 |
| `report_timing` | 时序报告 | 判断 slack 的主报告 |
| Slack | 时序余量 | 非负为 MET，负数为 violation |
| Partitioning | 设计分区 | 把复杂设计拆成可综合块 |
| Glue logic | 胶水逻辑 | 卡在模块边界的小逻辑 |

## 推荐学习顺序

1. 先读 [批次 1](chunk-01-pages-001-020.md)，建立 DC 流程和库设置概念。
2. 再读 [批次 2](chunk-02-pages-021-040.md)，理解 environment modeling。
3. 读 [批次 3](chunk-03-pages-041-060.md)，把 design rule 和 timing/area 约束分清。
4. 读 [批次 4](chunk-04-pages-061-080.md)，理解 compile 做了什么。
5. 重点反复读 [批次 5](chunk-05-pages-081-100.md)，学会读 timing report。
6. 最后读 [批次 6](chunk-06-pages-101-112.md)，把 partitioning 和项目组织接到工程实践。

## 最小 DC 脚本骨架

```tcl
# 1. Library setup
lappend search_path [list ./src ./scripts ./lib]
set target_library "smic18_tt.db"
set link_library "* $target_library dw_foundation.sldb"
set synthetic_library "dw_foundation.sldb"

# 2. Read design
analyze -f verilog ./src/sub_design.v
elaborate sub_design
analyze -f verilog ./src/top.v
elaborate top
current_design top
link
uniquify

# 3. Environment
set_operating_conditions slow
set_driving_cell -lib_cell INV -pin Z [all_inputs]
set_load [load_of slow/AND2X1/A] [all_outputs]
set_wire_load_mode enclosed

# 4. Design rule constraints
set_max_transition 1.5 [current_design]
set_max_capacitance 2.0 [current_design]
set_max_fanout 20 [current_design]

# 5. Timing and area constraints
create_clock clk -period 10 -waveform {0 5} [get_ports clk]
set_input_delay 2.0 -clock clk [remove_from_collection [all_inputs] [get_ports clk]]
set_output_delay 2.0 -clock clk [all_outputs]
set_max_area 0

# 6. Compile
compile -map_effort medium

# 7. Reports and outputs
report_constraint -all_violators > ./rpt/constraint.rpt
report_timing > ./rpt/timing.rpt
report_area > ./rpt/area.rpt
write -format ddc -output ./netlist/mapped.ddc
write -format verilog -output ./netlist/mapped.v
write_sdc ./sdc/mapped.sdc
write_sdf ./sdf/mapped.sdf
```

## 图表解读

这份 PDF 有很多图形页，文本抽取无法完全表达图中的结构关系：

- 页 2-3：综合从 HDL 到 generic boolean，再优化并映射到 target technology。
- 页 11：Basic Design Flow，展示库设置、读设计、环境、约束、compile、STA 的流程关系。
- 页 18-20：从 Verilog 和 schematic 两个视角解释 design object。
- 页 34-38：fanout/load/wire load 的图形例子。
- 页 55-56、88-91：input/output delay 的时序预算图，是理解 I/O constraint 的关键。
- 页 93-97：timing report 的结构图，建议对照 `report_timing` 文本看。
- 页 100-106：partitioning 和 glue logic 的图示，说明为什么模块边界影响综合质量。

缩略图拼板保存在：

```text
/Users/ganxuanzhi/Documents/自动化任务/repos/Analyse_repo/sources/design-compiler-training-fudan/contact-sheets/
```

## 我的理解

这份资料真正要教的不是某个命令，而是 DC 综合的工程闭环：

```text
建库和设计对象 -> 建环境 -> 写约束 -> compile -> 读报告 -> 修约束/代码/分区 -> 再 compile
```

对初学者来说，最容易卡住的是把命令当成孤立语法背诵。更好的方式是把每条命令放进“它在给哪个对象设置什么属性”这个框架里。比如 `set_load` 是给输出端建模，`set_max_transition` 是给对象设置设计规则上限，`create_clock` 是创建 timing analysis 的 clock object。这样就能从脚本堆里看出逻辑。

## 后续可追问的问题

- `target_library` 和 `link_library` 在真实项目里应该怎么组织？
- `set_input_delay` 和 `set_output_delay` 如何根据上游/下游模块分配？
- `set_max_delay`/`set_min_delay` 与 clock-based constraints 有什么区别？
- 如何读懂一个真实的 `report_timing` 并判断 violation 原因？
- 什么时候该用 `flatten`，什么时候应该保持层次？
- 如何为一个 DC 项目设计目录结构和 Makefile/run script？

## 局限

- 文本抽取总量约 18.7k 字符，说明大量信息在图中；本报告已经结合缩略图拼板，但没有逐图 OCR。
- 原 PDF 年代较早，命令思想仍有学习价值，但具体 DC 版本选项应以当前 Synopsys 文档为准。
- 文件名中 `Traning` 可能是原始拼写错误，报告沿用原文件名以便追溯。
