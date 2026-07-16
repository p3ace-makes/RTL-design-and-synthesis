## Overview
Day 4 focused on understanding the impact of different Verilog coding styles on simulation and synthesis. Various designs were analyzed to study incorrect coding practices, blocking assignment behavior, and efficient RTL implementation using the ternary operator, followed by verification through simulation and synthesis.

## Bad MUX
### RTL Simulation
<img width="1147" height="645" alt="bad_mux WF" src="https://github.com/user-attachments/assets/00849e44-9a5f-433d-91b5-68d2c19174c9" />

### GL Simulation
<img width="1046" height="645" alt="bad_mux gls" src="https://github.com/user-attachments/assets/c2737d65-17c8-4b40-9e84-83ecbfbfbef4" />

## Ternary Operator MUX
<img width="1101" height="649" alt="ter_mux gls" src="https://github.com/user-attachments/assets/cc331580-418a-4a49-9efd-69b11ce376b0" />
<img width="1129" height="520" alt="ter_mux synth" src="https://github.com/user-attachments/assets/fa684cdc-17b7-4a78-8e10-9c9a8f2867d2" />

## Blocking Caveat
### RTL Simulation
<img width="1182" height="653" alt="block cav WF" src="https://github.com/user-attachments/assets/21a6a66f-0059-425b-88f8-dc0c80785c6b" />

### GL Simulation
<img width="1178" height="653" alt="block_cav gls" src="https://github.com/user-attachments/assets/ac86ae2d-f751-4fe5-a472-6718124f9f79" />

### Synthesis
<img width="1046" height="589" alt="block_cav synth" src="https://github.com/user-attachments/assets/64dae27d-899d-49cc-9334-7ec3df17346a" />

