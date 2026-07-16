## Overview
Day 2 focused on designing and synthesizing sequential circuits and optimized combinational logic in Verilog. Functional verification was performed through simulation, followed by synthesis using Yosys and technology mapping to the Sky130 standard cell library to analyze the generated hardware implementations.

## Special Case (Mult 8)
**VERILOG CODE**
```verilog
module mult8 (input [2:0] a , output [5:0] y);
    assign y = a * 9;
endmodule
```
Multiplication by a constant can be optimized during synthesis to reduce hardware complexity.In this design, the input is multiplied by 9, which is equivalent to (a << 3) + a. Yosys recognizes this optimization and implements the circuit using simple shift and add logic instead of a dedicated multiplier.

<img width="1049" height="679" alt="mult8" src="https://github.com/user-attachments/assets/6696b3b2-71b7-46f1-ab76-7559455ed47d" />

## Asynchronous Reset D Flip-Flop
A D Flip-Flop with asynchronous reset clears the output immediately when **RESET_B** is asserted, independent of the clock. During synthesis, Yosys maps the design to the **sky130_fd_sc_hd__dfrtp_1** standard cell with asynchronous reset support.

<img width="1072" height="672" alt="async WF" src="https://github.com/user-attachments/assets/3566d170-08c1-4157-b1e9-b485a957ffd4" />
<img width="1210" height="660" alt="reset async synth" src="https://github.com/user-attachments/assets/b2d31215-c9b5-4aa2-8b25-8496203c8852" />

## Asynchronous Set D Flip-Flop
A D Flip-Flop with asynchronous set forces the output high immediately when **SET_B** is asserted, regardless of the clock. The synthesized design is implemented using the **sky130_fd_sc_hd__dfstp_2** standard cell.

<img width="1210" height="653" alt="set async synth" src="https://github.com/user-attachments/assets/4753cc00-12c0-4aa3-a8b3-0de1605f0b35" />

## Synchronous Reset D Flip-Flop
A D Flip-Flop with synchronous reset updates its output only on the active clock edge when the reset signal is asserted. The simulation waveform verifies that the reset affects the output only during a clock edge, confirming correct synchronous reset behavior.

<img width="1120" height="641" alt="sync WF" src="https://github.com/user-attachments/assets/e5276395-f6ee-4504-9faf-5f161647716a" />





