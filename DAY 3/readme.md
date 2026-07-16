## Overview
Day 3 explored synthesis optimizations using Yosys, including constant propagation, counter optimization, module-level optimization, and Boolean logic simplification. The optimized designs were then mapped to the Sky130 standard cell library for analysis.

## Constant Propagation & Sequential Optimization
### Const 1
<img width="1050" height="637" alt="const1 WF" src="https://github.com/user-attachments/assets/abf41f54-54fc-4e67-af92-c6a95e1771e1" />
<img width="1017" height="572" alt="const1 synth" src="https://github.com/user-attachments/assets/152b92fe-71d2-4f47-bbf0-4de732e60e0b" />

### Const 2
<img width="1107" height="645" alt="const2 WF" src="https://github.com/user-attachments/assets/8c955006-18a4-4edc-9c87-b287654fc31b" />
<img width="995" height="637" alt="const2 synth" src="https://github.com/user-attachments/assets/e2b388d6-2648-4c94-8436-2b61b4b4e558" />

### Const 3
Const3 combines asynchronous reset and asynchronous set in a two-stage D Flip-Flop design. The synthesized circuit maps the stages to the corresponding Sky130 flip-flops with reset (dfrtp) and set (dfstp) functionality.

<img width="1266" height="614" alt="const3 synth" src="https://github.com/user-attachments/assets/a3f2b088-a05a-44a6-9bb3-18c3a32e3ea6" />

### Const 4
```verilog
module dff_const4(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b1;
		q1 <= 1'b1;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end
endmodule
```
q1 is always assigned 1.
q receives the value of q1.
Since q1 is always 1, after the first clock edge q also becomes 1.<br?
However, q depends on the previous value of q1, because both are updated using non-blocking assignments (<=). This creates a sequential dependency between the two registers.

<img width="1001" height="641" alt="const4 synth" src="https://github.com/user-attachments/assets/2e1e2b8c-2598-41c9-b2b8-c951c60723c0" />

### Const 5
<img width="1291" height="492" alt="const5 synth" src="https://github.com/user-attachments/assets/f793bfec-0f4a-4ba2-b6d8-2e4ae0cb815e" />

## Counter Optimization
<img width="1316" height="449" alt="counter_opt" src="https://github.com/user-attachments/assets/caf4e5d9-a505-4eb7-a140-6e52b8355c2a" />

<img width="1287" height="467" alt="counter Opt2" src="https://github.com/user-attachments/assets/7fb7f87c-e456-449b-af72-1e631b8e0253" />

## Multiple Module Optimization
<img width="1178" height="630" alt="multiple_opt" src="https://github.com/user-attachments/assets/b24b4425-8abc-437c-9d59-aea0b5384bce" />

After optimization, Yosys further simplifies the design by eliminating unnecessary intermediate logic and merging equivalent operations across module boundaries. The resulting synthesized circuit uses fewer standard cells while maintaining the same output behavior.

<img width="1185" height="649" alt="multiple_opt2" src="https://github.com/user-attachments/assets/5999c47b-07a0-446b-accb-f470bdc03c4e" />

## Boolean Logic Optimization
### Optimization Check 1
<img width="1136" height="649" alt="opt check" src="https://github.com/user-attachments/assets/048d7120-62df-4413-adee-e6fbd1c77bfd" />

### Optimization Check 2
<img width="1106" height="622" alt="opt check 2" src="https://github.com/user-attachments/assets/37956d4d-ef0b-4365-bfd0-73d10a25afbb" />

### Optimization Check 3
<img width="1162" height="649" alt="opt check 3" src="https://github.com/user-attachments/assets/3a494019-3766-4efd-9271-c4f34cece7ec" />

### Optimization Check 4
<img width="1183" height="649" alt="opt check 4" src="https://github.com/user-attachments/assets/74177114-885e-4d95-981a-0d3b5874f7ea" />










