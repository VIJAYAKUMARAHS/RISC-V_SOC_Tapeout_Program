# <p align="center">💻RISC-V REFERENCE SOC TAPOUT PROGRAM
</p>

##  📅Day 1 - Introduction to Verilog RTL design and Synthesis

### Introduction to open-source simulator: iverilog

####  Introduction to iverilog design and test bench

### Simulator

RTL design is checked for adherence to the specification by simulating the design.

The simulator used for this course is Icarus Verilog (iverilog).

### Design

The Design consists of actual Verilog code or a set of Verilog codes that have the intended functionality to meet the required specifications.

### Testbench

The TestBench is the setup to apply stimulus (test_vectors) to the design to check its functionality

<img width="821" height="394" alt="image" src="https://github.com/user-attachments/assets/cf1bb7eb-c5ed-4f11-a6c8-9e56d8dc7af2" />

Note:

- Design may have one or more primary inputs, one or more primary outputs

- TB (Testbench) doesn't have a primary input or primary outputs

### How the simulator works

The simulator continuously checks for changes in input signals.

If there is a change, it evaluates the corresponding output.

If no change to the inputs → no change in outputs.

The simulator continuously detecting and reacting to the input signal changes.

### iverilog-based simulation flow

<img width="855" height="392" alt="image" src="https://github.com/user-attachments/assets/7fe87f0f-a090-4517-888a-7626a1e7cafd" />



> Design ➡️ Testbench ➡️ iverilog ➡️ vcd file ➡️ gtkwave ➡️ output waveform

<hr style="height:3px; background-color:black; border:none;">

### Labs using iverilog and gtkwave

#### Introduction to lab: tool setup 

Open a new terminal, create a directory vlsi.

Clone the required files from the link below

https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git

<img width="1905" height="993" alt="image" src="https://github.com/user-attachments/assets/31f18abe-c8d6-4916-9b6d-9499b0f74a84" />


Let's look at the sky130RTLDesignAndSynthesisWorkshop file.

<img width="1035" height="65" alt="image" src="https://github.com/user-attachments/assets/a6eb6f70-af6f-4ac5-b27c-30c80e508b5c" />

Lib check
<img width="1077" height="132" alt="image" src="https://github.com/user-attachments/assets/8280f705-5342-4ea8-9a7e-d4a5a340a2df" />

Verilog files: contain all our Verilog files, which are required for lab purposes 

<img width="1727" height="798" alt="image" src="https://github.com/user-attachments/assets/e781b211-c7e2-403b-9ca6-7b8193cbfb18" />

### How to work with iverilog and gtkwave

#### Step 1: simulate the RTL code good_mux.v and test bench tb_good_mux.v using iverilog
















































