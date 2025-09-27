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

- The simulator continuously checks for changes in input signals.

- If there is a change, it evaluates the corresponding output.

- If no change to the inputs → no change in outputs.

- The simulator continuously detecting and reacting to the input signal changes.

### iverilog-based simulation flow

<img width="855" height="392" alt="image" src="https://github.com/user-attachments/assets/7fe87f0f-a090-4517-888a-7626a1e7cafd" />



> Design ➡️ Testbench ➡️ iverilog ➡️ vcd file ➡️ gtkwave ➡️ output waveform

<hr style="height:3px; background-color:black; border:none;">

### Labs using iverilog and gtkwave

#### Introduction to lab: tool setup 

- Open a new terminal, create a directory vlsi.

- Clone the required files from the link below

https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git

<img width="1905" height="993" alt="image" src="https://github.com/user-attachments/assets/31f18abe-c8d6-4916-9b6d-9499b0f74a84" />


- Let's look at the sky130RTLDesignAndSynthesisWorkshop file.

<img width="1035" height="65" alt="image" src="https://github.com/user-attachments/assets/a6eb6f70-af6f-4ac5-b27c-30c80e508b5c" />

- Lib check
<img width="1077" height="132" alt="image" src="https://github.com/user-attachments/assets/8280f705-5342-4ea8-9a7e-d4a5a340a2df" />

- Verilog files: contain all our Verilog files, which are required for lab purposes 

<img width="1727" height="798" alt="image" src="https://github.com/user-attachments/assets/e781b211-c7e2-403b-9ca6-7b8193cbfb18" />

### How to work with iverilog and gtkwave

#### simulate the RTL code good_mux.v and test bench tb_good_mux.v using iverilog

```
$ iverilog good_mux.v tb_good_mux.v
```

<img width="1707" height="281" alt="image" src="https://github.com/user-attachments/assets/1797afb2-0bce-4d23-995c-f28089b65e95" />

#### To generate the vcd file
```
$ ./a.out
```
<img width="1533" height="290" alt="image" src="https://github.com/user-attachments/assets/b0ba6f50-d553-41d7-9523-3491bbaeacc7" />

#### gtkwave output

```
$ gtkwave tb_good_mux.vcd
```

<img width="1651" height="778" alt="image" src="https://github.com/user-attachments/assets/c3610ce7-b339-48ba-9780-ef701d10ecdf" />

<hr style="height:3px; background-color:black; border:none;">

## File Structure: 2:1 MUX Design and Testbench

- Let's see what is there in the design file

#### Note: I have not yet installed the gvim editor. To install the gvim editor, use command below 

```
sudo apt install neovim-qt
```

### Design File (good_mux.v)

```
gvim good_mux.v

```

- This is how the RTL Design file looks.

```
module good_mux (input i0 , input i1 , input sel , output reg y);
always @ (*)
begin
	if(sel)
		y <= i1;
	else 
		y <= i0;
end
endmodule

```

<img width="852" height="302" alt="image" src="https://github.com/user-attachments/assets/8b063f4a-1d13-46e0-9b51-d25aa5b2cfa1" />

-  This is how the Test bench file looks.

```
`timescale 1ns / 1ps
module tb_good_mux;
	// Inputs
	reg i0,i1,sel;
	// Outputs
	wire y;

        // Instantiate the Unit Under Test (UUT)
	good_mux uut (
		.sel(sel),
		.i0(i0),
		.i1(i1),
		.y(y)
	);

	initial begin
	$dumpfile("tb_good_mux.vcd");
	$dumpvars(0,tb_good_mux);
	// Initialize Inputs
	sel = 0;
	i0 = 0;
	i1 = 0;
	#300 $finish;
	end

always #75 sel = ~sel;
always #10 i0 = ~i0;
always #55 i1 = ~i1;
endmodule
```

<img width="540" height="587" alt="image" src="https://github.com/user-attachments/assets/96662491-ff7a-461e-89da-76bbc2f83238" />



















































