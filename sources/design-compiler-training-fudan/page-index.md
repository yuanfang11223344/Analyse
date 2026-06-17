# Page Index

| Page | Chars | Title/Sample |
|---:|---:|---|
| 1 | 71 | Design Compiler / JoyShockley / School of Microelectronics / Fudan University |
| 2 | 0 |  |
| 3 | 10 | Map to lib |
| 4 | 126 | Synthesis Is Constraint-Driven / You set the goals (through constraints) / Design Compiler optimizes the design to meet your goals |
| 5 | 125 | Synthesis Is Path-Based / Design Compiler uses Static Timing Analysis (STA) / to calculate the timing of the paths in the design. |
| 6 | 6 | Agenda |
| 7 | 6 | Agenda |
| 8 | 0 |  |
| 9 | 0 |  |
| 10 | 0 |  |
| 11 | 17 | Basic Design Flow |
| 12 | 488 | Library Specification / - search_path: the path to search for unsolved reference / library or design. / - link_library: the library used for interpreting input |
| 13 | 392 | .synopsys_dc.setup example / lappend search_path [list ./src ./scripts \ / /net/home/EDAs/synopsys/syn/libraries/syn\ / /net/sunb2i/export/home/xyzeng/xiaohao/fft_2k_4k_8k/dc/lib\ |
| 14 | 575 | - To specify technology libraries, you must specify the / target library and link library. / - Design Compiler uses the target library to build a circuit. During / mapping, Design  |
| 15 | 311 | Read Design /  step1: read, read_verilog, read_vhdl / 或 analyze + elaborate (analyze HDL / code and establish Boolean functions) |
| 16 | 0 |  |
| 17 | 332 | Example / 1 dc_shell-t> read_verilog top.v / dc_shell-t> read_verilog sub_design.v / dc_shell-t> current_design top |
| 18 | 27 | Design Objects In Synthesis |
| 19 | 35 | Design Objects: Verilog Perspective |
| 20 | 37 | Design Objects: Schematic Perspective |
| 21 | 173 | Unit in Standard Library / -time_unit: “1ns” / -voltage_unit: “1V” / -Current_unit: “1mA” |
| 22 | 0 |  |
| 23 | 28 | 2. Define Design Environment |
| 24 | 46 | Conmands used to Define the / Design Environment |
| 25 | 185 | Set Operating Conditions / - Operating condition model scales components / delay, directs the optimizer to simulate variations / in process, temperature and voltage |
| 26 | 449 | Set Input Pulling Resistance (khoms) / - set_drive / - set_drive : Sets the rise_drive or fall_drive / attributes to specified resistance values on |
| 27 | 498 | Set Input Pulling Resistance (khoms) / - set_drive / - set_drive_cell : sets attributes on input or inout / ports of the current design that specify that a |
| 28 | 297 | Setting Output Loading Capacitance (pF) / -set_load / - set_load : Sets the load attribute to a specified / value on specified ports and nets. |
| 29 | 210 | Setting Output Loading Capacitance (pF) / -set_load / - set _load 2 in1 / - set port_load [expr 2.5+3*[load_of tech_lib/IV/A]] |
| 30 | 413 | set_fanout_load / - You can model the external fanout effects by / specifying the expected fanout load values on output / ports with the set_fanout_load command. |
| 31 | 367 | set_load V.S. set_fanout_load / - fanout load is not the same as load. / - fanout load is a unitless value that represents a / numerical contribution to the total fanout. Load is a |
| 32 | 229 | Design Constraints: set_max_fanout / -set_max_fanout is a design constraints. / -set_max_fanout: set the max_fanout / attribute to a specified value on input |
| 33 | 519 | set_fanout_load V.S. set_max_fanout / - set_fanout_load is design envoronment; / set_max_fanout is a design constraint. / - Design Compiler models fanout restrictions by |
| 34 | 107 | Case Study: fanout_load & max_fanout_load / >>set_fanout_load 3.0 OUT1 / >>set_max_fanout 8 [get_designs ADDER] |
| 35 | 362 | Case Study / - An input pin normally has a fanout load of 1, but it can / have a higher value. / - The fanout load imposed by a driven cell (U3) is not |
| 36 | 9 | Net Delay |
| 37 | 149 | Wire Load Model / - A wire load model is an estimate of a net’s RC / parasitics based on the net’s fanout. / Example: dc_shell-t> set_wire_load_model 10x10 |
| 38 | 78 | Setting Wire Load Mode / dc_shell-t> set_wire_load_mode <top/enclosed/segmented> |
| 39 | 357 | Hierarchical Wire Load Models / - DC supports three modes for determining which wire / load model to use for nets that cross hierarchical / boundaries: |
| 40 | 561 | Hierarchical Wire Load Models / - Enclose: DC uses the wire load model of the smallest design that / fully encloseds the net. If the design enclosing the net has no wire load / mod |
| 41 | 207 | - set _wire_load_model -name “10*10” -library my_lib.db / - current_design LOW / - set_wire_load_model -name “10*10” / - current_design TOP |
| 42 | 0 |  |
| 43 | 72 | Design Constraints: Design Rule Constraints / and Optimization Constraints |
| 44 | 241 | - Design Rule Constraints: technology-specific / restriction. / - Optimization Constraints: design goals and / requirements. |
| 45 | 281 | Design Rule Constraints / - Design rules can not be violated at any cost, even if it / will violate the timing and area goal. / - Rule Constraints Demand: |
| 46 | 152 | set_max_transition (ns) / - set_max_transition: set the maximum / transition time for specified clocks, ports, or / designs. |
| 47 | 249 | set_max_transition (ns) / -Port: late_riser / -set_max_transition 2.0 late_riser / -Design: TEST |
| 48 | 22 | clock path & data path |
| 49 | 454 | set_max_capacitance / - It is set as a pin-level attribute that defines the / maximum total capacitive load that an output pin can / drive. |
| 50 | 209 | set_max_capacitance / - set_max_capacitance 2.0 [get_ports late_riser] / - set_max_capacitance 2.0 [current_design] / - set_max_capacitance 2.0 [get_clocks clk1] |
| 51 | 43 | Summary of Design Rule Commands and / Objects |
| 52 | 231 | Optimization Constraints / The optimization constraints comprise / -Timing constraints (performance and / speed) |
| 53 | 276 | Timing Constraints / - Use the create_clock command to specify a clock. / - Use the set_input_delay and set_output_delay / commands to specify the input and output port timing |
| 54 | 151 | create_clock / -create_clock: creates a clock object and / defines its waveform in the current design. / - create_clock “PHI1” –period 10 –waveform {5.0 9.5} |
| 55 | 15 | set_input_delay |
| 56 | 16 | set_output_delay |
| 57 | 322 | set_max_delay & set_min_delay / -set_max_delay: Specifies a maximum / delay target for path in the current design. / -set_max_delay 10.0 -to {Y} |
| 58 | 323 | Optimization Constraints / - Optimization constraints, in order of attention are / - Maximum delay / - Minimum delay |
| 59 | 318 | Timing Constraints for Sequential / Circuit / - create_clock: define your clock’s waveform & / respect the set-up time requirements of all |
| 60 | 217 | Setting Area Constraint / - Area Unit: / - Equivalent gate counts / - um2 |
| 61 | 282 | Constraints Priority / - During the optimization ,there exists a constraint / priority relationship / - Design Rule Constraint |
| 62 | 0 |  |
| 63 | 32 | How to map and optimize a design |
| 64 | 193 | Compile is the “art” of synthesis / - Logical level optimization / - flatten : remove structure / - structure: minimize generic logic |
| 65 | 255 | Logical Level Optimization / - Operate with boolean representation of circuit . / - Has a global effect on the overall area/speed / characteristic of a design. |
| 66 | 167 | Structure / - Factors out common sub-expression as / intermediate variable / - Useful for speed optimization as well as area |
| 67 | 271 | Flatten / - Flatten is default OFF / - Remove all intermediate variable / - Result a two-level sum-of-product form |
| 68 | 234 | Gate Level Optimization / - Select components to meet timing, design rule / & area goals specified for the circuit. / - Has a local effect on the area/speed |
| 69 | 251 | Combinational Mapping / - Mapping rearranges / components, / combining and re- |
| 70 | 264 | Sequential Mapping / - Optimize the mapping / to sequential cells / from technology |
| 71 | 474 | Compile Command and Options / - compile –map_effort medium / high / - high, it does critical path re-synthesis, but it will use / more CPU time, in some case the action of compile |
| 72 | 342 | How to generate results and report / attributes for synthesis / - Attributes to Report / report_design, report_clock, report_port, |
| 73 | 0 |  |
| 74 | 206 | Basic Conceptions of STA / - Timing paths and groups / - Delay calculation / - Setup and hold time check |
| 75 | 31 | Timing Paths in Design Compiler |
| 76 | 79 | - Input Paths / - Output Paths / - Register-to-Register Paths / - Combinational Paths |
| 77 | 273 | Timing Groups / - How to organize timing paths into group? / - Paths are grouped according to the clocks controlling / their endpoints. |
| 78 | 21 | Timing Paths Exercise |
| 79 | 0 |  |
| 80 | 221 | Path Delay Calculation / - To calculate total delay, each path is broken into timing arcs. / - Each timing arc contributes either a net delay or cell delay / - All the net and cell |
| 81 | 360 | Setup and Hold Time Check / - Setup Time: The length of time that data must stabilize / before the clock transition. / The maximum data path is used to determine if setup |
| 82 | 0 |  |
| 83 | 234 | Clock Tree Modeling / - Two parameter to model: / - Specify clock network latency / - set_clock_latency –rise tr –fall tf [get_ports TCK] |
| 84 | 199 | Clock Tree Modeling Example / - create_clock –period 10 –waveform {0 5} [get_ports TCK] / - set_clock_latency –rise 1 –fall 2 [get_ ports TCK] / - set_clock_uncertainty –rise 0.8 – |
| 85 | 339 | Effect of Clock Tree Modeling on Setup / Time / - Assumed library (Flip Flop) setup time requirement = 1ns / create_clock –period 10 –waveform {0 5} [get_ports TCK] |
| 86 | 334 | Effect of Clock Tree Modeling on Hold / Time / - Assumed library (Flip Flop) hold time requirement = 1ns / create_clock –period 10 –waveform {0 5} [get_ports TCK] |
| 87 | 275 | Modeling Source Latency / - Source latency is the propagation time from the actual clock / origin to the clock definition point in the design / create_clock –period 10 –waveform {0 |
| 88 | 28 | Constraining the Input Paths |
| 89 | 28 | Constraining the Input Paths |
| 90 | 29 | Constraining the Output Paths |
| 91 | 29 | Constraining the Output Paths |
| 92 | 79 | DC Timing Reports / - Use the report_timing command to access the / timing reports. |
| 93 | 1064 | Startpoint: ARM7TDMI/debuger/tms_latch_reg/CKN / (internal path startpoint clocked by HCLK) / Endpoint: ARM7TDMI/debuger/tms_s_reg / (falling edge-triggered flip-flop clocked by HC |
| 94 | 39 | Timing Report: Path Information Section |
| 95 | 33 | Timing Report: Path Delay Section |
| 96 | 36 | Timing Report: Path Required Section |
| 97 | 30 | Timing Report: Summary Section |
| 98 | 0 |  |
| 99 | 0 |  |
| 100 | 21 | What is partitioning? |
| 101 | 0 |  |
| 102 | 0 |  |
| 103 | 0 |  |
| 104 | 16 | Avoid Glue Logic |
| 105 | 32 | Remove Glue Logic Between Blocks |
| 106 | 199 | This partitioning is recommended due to: / - Possible technology-dependent ( “black box”) I/O pad cells / - Possible untestable “Divide By” clock generation / - Possible technology |
| 107 | 0 |  |
| 108 | 0 |  |
| 109 | 0 |  |
| 110 | 211 | How to start DC / 1 unix/linux> dc_shell-t / dc_shell> source scripts/xx.tcl -e -v / 2 unix/linux> dc_shell –f scripts/xx.tcl (/tee ./log/run.log) |
| 111 | 17 | Project Directory |
| 112 | 92 | How Get Help? / For example: / - dc_shell> man set_input_delay / - dc_shell> set_input_delay -help |
