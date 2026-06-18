# Design Compiler Training Fudan - 逐页分析索引


- **源文件**：`/Users/ganxuanzhi/学习/DC综合学习文件/eetop.cn_Design_Compiler_Traning_Fudan.pdf`
- **页数**：112
- **重构方式**：逐页读书笔记；每页单独截图、单独解读、单独总结；旧版 20 页分块报告和 contact sheet 已移除。
- **合并版**：[page-by-page-notes.md](page-by-page-notes.md)
- **总览**：[summary.md](summary.md)

## 使用方式

1. 从下表进入任意页。
2. 先看单页截图，再读原文要点。
3. 用“原文解读/我的理解/实操提醒”复盘该页在 DC 综合流程中的作用。

## 页码索引

| Page | 标题 | 阶段 | 角色 | 笔记 |
|---:|---|---|---|---|
| 1 | Design Compiler | 综合总览：约束驱动、路径驱动和库映射 | 执行优化和映射 | [Page 001](pages/page-001.md) |
| 2 | Basic synthesis flow diagram | 综合总览：约束驱动、路径驱动和库映射 | 建立全局框架 | [Page 002](pages/page-002.md) |
| 3 | Map to lib | 综合总览：约束驱动、路径驱动和库映射 | 建立全局框架 | [Page 003](pages/page-003.md) |
| 4 | Synthesis Is Constraint-Driven | 综合总览：约束驱动、路径驱动和库映射 | 执行优化和映射 | [Page 004](pages/page-004.md) |
| 5 | Synthesis Is Path-Based | 综合总览：约束驱动、路径驱动和库映射 | 执行优化和映射 | [Page 005](pages/page-005.md) |
| 6 | Agenda | 课程目录：建立阅读地图 | 章节导航 | [Page 006](pages/page-006.md) |
| 7 | Agenda | 课程目录：建立阅读地图 | 章节导航 | [Page 007](pages/page-007.md) |
| 8 | Agenda transition | 课程目录：建立阅读地图 | 章节导航 | [Page 008](pages/page-008.md) |
| 9 | Agenda transition | 课程目录：建立阅读地图 | 章节导航 | [Page 009](pages/page-009.md) |
| 10 | Agenda transition | 课程目录：建立阅读地图 | 章节导航 | [Page 010](pages/page-010.md) |
| 11 | Basic Design Flow | 前端准备：库、读入设计和 DC 对象模型 | 流程节点说明 | [Page 011](pages/page-011.md) |
| 12 | Library Specification | 前端准备：库、读入设计和 DC 对象模型 | 配置综合库 | [Page 012](pages/page-012.md) |
| 13 | .synopsys_dc.setup example | 前端准备：库、读入设计和 DC 对象模型 | 配置综合库 | [Page 013](pages/page-013.md) |
| 14 | - To specify technology libraries, you must specify the | 前端准备：库、读入设计和 DC 对象模型 | 配置综合库 | [Page 014](pages/page-014.md) |
| 15 | Read Design | 前端准备：库、读入设计和 DC 对象模型 | 读入并建立设计层次 | [Page 015](pages/page-015.md) |
| 16 | Read design visual note | 前端准备：库、读入设计和 DC 对象模型 | 读入并建立设计层次 | [Page 016](pages/page-016.md) |
| 17 | Example | 前端准备：库、读入设计和 DC 对象模型 | 读入并建立设计层次 | [Page 017](pages/page-017.md) |
| 18 | Design Objects In Synthesis | 前端准备：库、读入设计和 DC 对象模型 | 理解 DC 对象模型 | [Page 018](pages/page-018.md) |
| 19 | Design Objects: Verilog Perspective | 前端准备：库、读入设计和 DC 对象模型 | 理解 DC 对象模型 | [Page 019](pages/page-019.md) |
| 20 | Design Objects: Schematic Perspective | 前端准备：库、读入设计和 DC 对象模型 | 理解 DC 对象模型 | [Page 020](pages/page-020.md) |
| 21 | Unit in Standard Library | 前端准备：库、读入设计和 DC 对象模型 | 配置综合库 | [Page 021](pages/page-021.md) |
| 22 | Library units visual note | 前端准备：库、读入设计和 DC 对象模型 | 配置综合库 | [Page 022](pages/page-022.md) |
| 23 | 2. Define Design Environment | 设计环境建模：工艺、负载、扇出和线负载 | 流程节点说明 | [Page 023](pages/page-023.md) |
| 24 | Conmands used to Define the | 设计环境建模：工艺、负载、扇出和线负载 | 流程节点说明 | [Page 024](pages/page-024.md) |
| 25 | Set Operating Conditions | 设计环境建模：工艺、负载、扇出和线负载 | 建模 PVT 环境 | [Page 025](pages/page-025.md) |
| 26 | Set Input Pulling Resistance (khoms) | 设计环境建模：工艺、负载、扇出和线负载 | 配置综合库 | [Page 026](pages/page-026.md) |
| 27 | Set Input Pulling Resistance (khoms) | 设计环境建模：工艺、负载、扇出和线负载 | 配置综合库 | [Page 027](pages/page-027.md) |
| 28 | Setting Output Loading Capacitance (pF) | 设计环境建模：工艺、负载、扇出和线负载 | 配置综合库 | [Page 028](pages/page-028.md) |
| 29 | Setting Output Loading Capacitance (pF) | 设计环境建模：工艺、负载、扇出和线负载 | 建模输出负载 | [Page 029](pages/page-029.md) |
| 30 | set_fanout_load | 设计环境建模：工艺、负载、扇出和线负载 | 配置综合库 | [Page 030](pages/page-030.md) |
| 31 | set_load V.S. set_fanout_load | 设计环境建模：工艺、负载、扇出和线负载 | 建模输出负载 | [Page 031](pages/page-031.md) |
| 32 | Design Constraints: set_max_fanout | 设计环境建模：工艺、负载、扇出和线负载 | 区分扇出环境和扇出规则 | [Page 032](pages/page-032.md) |
| 33 | set_fanout_load V.S. set_max_fanout | 设计环境建模：工艺、负载、扇出和线负载 | 配置综合库 | [Page 033](pages/page-033.md) |
| 34 | Case Study: fanout_load & max_fanout_load | 设计环境建模：工艺、负载、扇出和线负载 | 区分扇出环境和扇出规则 | [Page 034](pages/page-034.md) |
| 35 | Case Study | 设计环境建模：工艺、负载、扇出和线负载 | 配置综合库 | [Page 035](pages/page-035.md) |
| 36 | Net Delay | 设计环境建模：工艺、负载、扇出和线负载 | 估计互连延迟 | [Page 036](pages/page-036.md) |
| 37 | Wire Load Model | 设计环境建模：工艺、负载、扇出和线负载 | 区分扇出环境和扇出规则 | [Page 037](pages/page-037.md) |
| 38 | Setting Wire Load Mode | 设计环境建模：工艺、负载、扇出和线负载 | 估计互连延迟 | [Page 038](pages/page-038.md) |
| 39 | Hierarchical Wire Load Models | 设计环境建模：工艺、负载、扇出和线负载 | 估计互连延迟 | [Page 039](pages/page-039.md) |
| 40 | Hierarchical Wire Load Models | 设计环境建模：工艺、负载、扇出和线负载 | 估计互连延迟 | [Page 040](pages/page-040.md) |
| 41 | - set _wire_load_model -name “10*10” -library my_lib.db | 设计环境建模：工艺、负载、扇出和线负载 | 配置综合库 | [Page 041](pages/page-041.md) |
| 42 | Design constraints transition | 设计环境建模：工艺、负载、扇出和线负载 | 流程节点说明 | [Page 042](pages/page-042.md) |
| 43 | Design Constraints: Design Rule Constraints | 约束建模：设计规则、时序、面积和优先级 | 设置设计规则底线 | [Page 043](pages/page-043.md) |
| 44 | - Design Rule Constraints: technology-specific | 约束建模：设计规则、时序、面积和优先级 | 设置设计规则底线 | [Page 044](pages/page-044.md) |
| 45 | Design Rule Constraints | 约束建模：设计规则、时序、面积和优先级 | 建模输出负载 | [Page 045](pages/page-045.md) |
| 46 | set_max_transition (ns) | 约束建模：设计规则、时序、面积和优先级 | 设置设计规则底线 | [Page 046](pages/page-046.md) |
| 47 | set_max_transition (ns) | 约束建模：设计规则、时序、面积和优先级 | 设置设计规则底线 | [Page 047](pages/page-047.md) |
| 48 | clock path & data path | 约束建模：设计规则、时序、面积和优先级 | 流程节点说明 | [Page 048](pages/page-048.md) |
| 49 | set_max_capacitance | 约束建模：设计规则、时序、面积和优先级 | 建模输出负载 | [Page 049](pages/page-049.md) |
| 50 | set_max_capacitance | 约束建模：设计规则、时序、面积和优先级 | 建模输出负载 | [Page 050](pages/page-050.md) |
| 51 | Summary of Design Rule Commands and | 约束建模：设计规则、时序、面积和优先级 | 设置设计规则底线 | [Page 051](pages/page-051.md) |
| 52 | Optimization Constraints | 约束建模：设计规则、时序、面积和优先级 | 理解优化目标和优先级 | [Page 052](pages/page-052.md) |
| 53 | Timing Constraints | 约束建模：设计规则、时序、面积和优先级 | 设置时序预算 | [Page 053](pages/page-053.md) |
| 54 | create_clock | 约束建模：设计规则、时序、面积和优先级 | 设置时序预算 | [Page 054](pages/page-054.md) |
| 55 | set_input_delay | 约束建模：设计规则、时序、面积和优先级 | 设置时序预算 | [Page 055](pages/page-055.md) |
| 56 | set_output_delay | 约束建模：设计规则、时序、面积和优先级 | 设置时序预算 | [Page 056](pages/page-056.md) |
| 57 | set_max_delay & set_min_delay | 约束建模：设计规则、时序、面积和优先级 | 设置时序预算 | [Page 057](pages/page-057.md) |
| 58 | Optimization Constraints | 约束建模：设计规则、时序、面积和优先级 | 设置时序预算 | [Page 058](pages/page-058.md) |
| 59 | Timing Constraints for Sequential | 约束建模：设计规则、时序、面积和优先级 | 设置时序预算 | [Page 059](pages/page-059.md) |
| 60 | Setting Area Constraint | 约束建模：设计规则、时序、面积和优先级 | 理解优化目标和优先级 | [Page 060](pages/page-060.md) |
| 61 | Constraints Priority | 约束建模：设计规则、时序、面积和优先级 | 设置设计规则底线 | [Page 061](pages/page-061.md) |
| 62 | Mapping and optimization transition | 约束建模：设计规则、时序、面积和优先级 | 执行优化和映射 | [Page 062](pages/page-062.md) |
| 63 | How to map and optimize a design | 综合优化：逻辑优化、映射、compile 与报告 | 流程节点说明 | [Page 063](pages/page-063.md) |
| 64 | Compile is the “art” of synthesis | 综合优化：逻辑优化、映射、compile 与报告 | 执行优化和映射 | [Page 064](pages/page-064.md) |
| 65 | Logical Level Optimization | 综合优化：逻辑优化、映射、compile 与报告 | 理解优化目标和优先级 | [Page 065](pages/page-065.md) |
| 66 | Structure | 综合优化：逻辑优化、映射、compile 与报告 | 理解优化目标和优先级 | [Page 066](pages/page-066.md) |
| 67 | Flatten | 综合优化：逻辑优化、映射、compile 与报告 | 执行优化和映射 | [Page 067](pages/page-067.md) |
| 68 | Gate Level Optimization | 综合优化：逻辑优化、映射、compile 与报告 | 设置设计规则底线 | [Page 068](pages/page-068.md) |
| 69 | Combinational Mapping | 综合优化：逻辑优化、映射、compile 与报告 | 设置设计规则底线 | [Page 069](pages/page-069.md) |
| 70 | Sequential Mapping | 综合优化：逻辑优化、映射、compile 与报告 | 配置综合库 | [Page 070](pages/page-070.md) |
| 71 | Compile Command and Options | 综合优化：逻辑优化、映射、compile 与报告 | 设置设计规则底线 | [Page 071](pages/page-071.md) |
| 72 | How to generate results and report | 综合优化：逻辑优化、映射、compile 与报告 | 理解优化目标和优先级 | [Page 072](pages/page-072.md) |
| 73 | STA transition | STA 与时序报告：路径、clock model、I/O 约束和 slack | 流程节点说明 | [Page 073](pages/page-073.md) |
| 74 | Basic Conceptions of STA | STA 与时序报告：路径、clock model、I/O 约束和 slack | 建立 STA 基本概念 | [Page 074](pages/page-074.md) |
| 75 | Timing Paths in Design Compiler | STA 与时序报告：路径、clock model、I/O 约束和 slack | 执行优化和映射 | [Page 075](pages/page-075.md) |
| 76 | - Input Paths | STA 与时序报告：路径、clock model、I/O 约束和 slack | 建立 STA 基本概念 | [Page 076](pages/page-076.md) |
| 77 | Timing Groups | STA 与时序报告：路径、clock model、I/O 约束和 slack | 建立 STA 基本概念 | [Page 077](pages/page-077.md) |
| 78 | Timing Paths Exercise | STA 与时序报告：路径、clock model、I/O 约束和 slack | 建立 STA 基本概念 | [Page 078](pages/page-078.md) |
| 79 | Timing path exercise visual | STA 与时序报告：路径、clock model、I/O 约束和 slack | 建立 STA 基本概念 | [Page 079](pages/page-079.md) |
| 80 | Path Delay Calculation | STA 与时序报告：路径、clock model、I/O 约束和 slack | 估计互连延迟 | [Page 080](pages/page-080.md) |
| 81 | Setup and Hold Time Check | STA 与时序报告：路径、clock model、I/O 约束和 slack | 建立 STA 基本概念 | [Page 081](pages/page-081.md) |
| 82 | Clock tree modeling transition | STA 与时序报告：路径、clock model、I/O 约束和 slack | 建模时钟网络 | [Page 082](pages/page-082.md) |
| 83 | Clock Tree Modeling | STA 与时序报告：路径、clock model、I/O 约束和 slack | 建模时钟网络 | [Page 083](pages/page-083.md) |
| 84 | Clock Tree Modeling Example | STA 与时序报告：路径、clock model、I/O 约束和 slack | 设置时序预算 | [Page 084](pages/page-084.md) |
| 85 | Effect of Clock Tree Modeling on Setup | STA 与时序报告：路径、clock model、I/O 约束和 slack | 配置综合库 | [Page 085](pages/page-085.md) |
| 86 | Effect of Clock Tree Modeling on Hold | STA 与时序报告：路径、clock model、I/O 约束和 slack | 配置综合库 | [Page 086](pages/page-086.md) |
| 87 | Modeling Source Latency | STA 与时序报告：路径、clock model、I/O 约束和 slack | 设置时序预算 | [Page 087](pages/page-087.md) |
| 88 | Constraining the Input Paths | STA 与时序报告：路径、clock model、I/O 约束和 slack | 约束模块 I/O 路径 | [Page 088](pages/page-088.md) |
| 89 | Constraining the Input Paths | STA 与时序报告：路径、clock model、I/O 约束和 slack | 约束模块 I/O 路径 | [Page 089](pages/page-089.md) |
| 90 | Constraining the Output Paths | STA 与时序报告：路径、clock model、I/O 约束和 slack | 约束模块 I/O 路径 | [Page 090](pages/page-090.md) |
| 91 | Constraining the Output Paths | STA 与时序报告：路径、clock model、I/O 约束和 slack | 约束模块 I/O 路径 | [Page 091](pages/page-091.md) |
| 92 | DC Timing Reports | STA 与时序报告：路径、clock model、I/O 约束和 slack | 拆解 timing report | [Page 092](pages/page-092.md) |
| 93 | Startpoint: ARM7TDMI/debuger/tms_latch_reg/CKN | STA 与时序报告：路径、clock model、I/O 约束和 slack | 拆解 timing report | [Page 093](pages/page-093.md) |
| 94 | Timing Report: Path Information Section | STA 与时序报告：路径、clock model、I/O 约束和 slack | 拆解 timing report | [Page 094](pages/page-094.md) |
| 95 | Timing Report: Path Delay Section | STA 与时序报告：路径、clock model、I/O 约束和 slack | 拆解 timing report | [Page 095](pages/page-095.md) |
| 96 | Timing Report: Path Required Section | STA 与时序报告：路径、clock model、I/O 约束和 slack | 拆解 timing report | [Page 096](pages/page-096.md) |
| 97 | Timing Report: Summary Section | STA 与时序报告：路径、clock model、I/O 约束和 slack | 拆解 timing report | [Page 097](pages/page-097.md) |
| 98 | Timing report exercise visual | STA 与时序报告：路径、clock model、I/O 约束和 slack | 拆解 timing report | [Page 098](pages/page-098.md) |
| 99 | Timing report exercise visual | STA 与时序报告：路径、clock model、I/O 约束和 slack | 拆解 timing report | [Page 099](pages/page-099.md) |
| 100 | What is partitioning? | Partitioning：层次划分、glue logic 和工程边界 | 改进设计分区 | [Page 100](pages/page-100.md) |
| 101 | Partitioning visual note | Partitioning：层次划分、glue logic 和工程边界 | 改进设计分区 | [Page 101](pages/page-101.md) |
| 102 | Partitioning visual note | Partitioning：层次划分、glue logic 和工程边界 | 改进设计分区 | [Page 102](pages/page-102.md) |
| 103 | Partitioning visual note | Partitioning：层次划分、glue logic 和工程边界 | 改进设计分区 | [Page 103](pages/page-103.md) |
| 104 | Avoid Glue Logic | Partitioning：层次划分、glue logic 和工程边界 | 改进设计分区 | [Page 104](pages/page-104.md) |
| 105 | Remove Glue Logic Between Blocks | Partitioning：层次划分、glue logic 和工程边界 | 改进设计分区 | [Page 105](pages/page-105.md) |
| 106 | This partitioning is recommended due to: | Partitioning：层次划分、glue logic 和工程边界 | 改进设计分区 | [Page 106](pages/page-106.md) |
| 107 | Partitioning visual note | Partitioning：层次划分、glue logic 和工程边界 | 改进设计分区 | [Page 107](pages/page-107.md) |
| 108 | Partitioning visual note | Partitioning：层次划分、glue logic 和工程边界 | 改进设计分区 | [Page 108](pages/page-108.md) |
| 109 | Partitioning visual note | Partitioning：层次划分、glue logic 和工程边界 | 改进设计分区 | [Page 109](pages/page-109.md) |
| 110 | How to start DC | 工程使用：启动 DC、项目目录和帮助系统 | 建立工程运行习惯 | [Page 110](pages/page-110.md) |
| 111 | Project Directory | 工程使用：启动 DC、项目目录和帮助系统 | 建立工程运行习惯 | [Page 111](pages/page-111.md) |
| 112 | How Get Help? | 工程使用：启动 DC、项目目录和帮助系统 | 建立工程运行习惯 | [Page 112](pages/page-112.md) |
