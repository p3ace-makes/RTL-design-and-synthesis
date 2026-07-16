Implemented and simulated a 2:1 Multiplexer in Verilog to verify its functional behavior. The design was then synthesized using Yosys with the Sky130 standard cell library, and the generated gate-level schematic was analyzed.

## Simulation
<img width="1065" height="640" alt="Day1 mux waveform" src="https://github.com/user-attachments/assets/e1e2fe38-84cb-4ea0-802b-8c2085623d1b" />

## Verilog Code
module good_mux (input i0, input i1, input sel, output reg y);
always @ (*)
begin
    if(sel)
        y <= i1;
    else 
        y <= i0;
end
endmodule

## Synthesis
<img width="1264" height="662" alt="Day1 mux synth" src="https://github.com/user-attachments/assets/9d3f2dba-663a-4456-8479-1ed16b6bdf2b" />
