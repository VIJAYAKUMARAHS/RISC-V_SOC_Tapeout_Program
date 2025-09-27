# <p align="center">💻RISC-V REFERENCE SOC TAPOUT PROGRAM
</p>

##  📅Day 1 - Introduction to Verilog RTL design and Synthesis

## 1. Introduction to open-source simulator: iverilog

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

## 2. Labs using iverilog and gtkwave

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

## 3. Introduction to Yosys and Logic Synthesis

###  Introduction to yosys

### What is Synthesizer?

- The tool used for converting RTL design code to gate-level Netlist.

- Yosys is the tool I am using to synthesize code.

#### Let's look at how the flow 

<img width="866" height="257" alt="image" src="https://github.com/user-attachments/assets/6aafd058-b6ab-4059-b15e-e15c19d52f9d" />


#### Let's see how  the Yosys setup go's

<img width="895" height="477" alt="image" src="https://github.com/user-attachments/assets/a618cecd-1dd3-4483-a629-aa7da5008be6" />

```
$ read_verilog  //this used to read the design verilog file
$ read_liberty  //this used to read the .lib file
$ write_verilog  // this used to write the netlist
```


- Netlist is a representation of RTL design file

- .lib file contains the already designed standard cell gates
  
### How do I verify my synthesis is correct

<img width="888" height="499" alt="image" src="https://github.com/user-attachments/assets/64aa1dea-2363-4ced-887b-f4bff40d82f3" />


###  Introduction to logic synthesis

#### What is RTL Design?

<img width="637" height="407" alt="image" src="https://github.com/user-attachments/assets/d1b1cfb7-7d96-4577-bfa5-4be0c81103a9" />

- How do I map RTL Code and the required logic circuit

<img width="666" height="407" alt="image" src="https://github.com/user-attachments/assets/8732909e-4d0d-4068-a1eb-142823c33a0d" />

#### What happens in the Synthesis?

<img width="616" height="464" alt="image" src="https://github.com/user-attachments/assets/8ae19360-ef67-4427-b7ca-b9750c8c9631" />

#### What is .lib(Liberty) file? What it contains

<img width="642" height="433" alt="image" src="https://github.com/user-attachments/assets/ee9541d6-bf15-4563-a558-f71044e85aae" />

#### Why we need different flavours of gates (standard cells)

#### Why do we need Fast cells

<img width="645" height="417" alt="image" src="https://github.com/user-attachments/assets/27bd59dd-24a5-45e4-8eff-939f2f45d477" />

#### What is Setup Time?

> #### Definition: Setup time is the minimum amount of time the input signal (D) must be stable before the active clock edge (rising or falling, depending on design) so that the flip-flop reliably captures the correct data.

#### Why does it matter

- Ensures reliable data sampling.

- Violations lead to metastability or incorrect operation.

- Critical in timing analysis for high-speed circuits.

#### Why do we need slow cells?

<img width="665" height="455" alt="image" src="https://github.com/user-attachments/assets/010755a2-5a4a-44ae-8935-022ec639d04a" />

#### What is Hold Time?

> Definition: Hold time is the minimum amount of time the input signal (D) must remain stable after the active clock edge so that the flip-flop correctly latches the data.

#### Difference between Setup & Hold
- Setup time → stable before clock edge.
  
- Hold time → stable after clock edge.

#### Let's compare Fast cells and Slow cells

<img width="637" height="387" alt="image" src="https://github.com/user-attachments/assets/234552b8-19e1-45b6-ac5a-c113d062b2fc" />

#### Selection of STD cells

<img width="640" height="388" alt="image" src="https://github.com/user-attachments/assets/a5ba9ede-307e-4d22-9739-aa9f5536ca01" />


#### Illustration of Synthesis

<img width="673" height="470" alt="image" src="https://github.com/user-attachments/assets/15c2bb46-fef0-4744-b47e-36a3053fe6ec" />

<hr style="height:3px; background-color:black; border:none;">

## 4. Labs using Yosys and Sky130 PDKs

### Synthesis using Yosys for (good_mux.v)

#### Steps to invoke the Yosys tool and Synthesis 

- Type the Command
```
$ yosys
```
<img width="1343" height="477" alt="image" src="https://github.com/user-attachments/assets/74e44513-ff49-47db-8753-d35e52f69093" />

#### Synthesis Steps

- First, we have to read the library

```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
<img width="1257" height="491" alt="image" src="https://github.com/user-attachments/assets/465d7181-754b-4e62-8d32-5ab13501b51c" />

We got 418 std cells from the .lib file

- Second, we have to read the RTL Verilog file

```
read_verilog good_mux.v
```

<img width="1000" height="263" alt="image" src="https://github.com/user-attachments/assets/77156772-c8bb-4e33-8505-5815527e3f0e" />

- Let's synthesize the design

```
synth -top good_mux

```
<img width="1008" height="637" alt="image" src="https://github.com/user-attachments/assets/f7f2548b-2167-4dc2-a6ca-4fc89b9270e8" />

```
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

<img width="787" height="298" alt="image" src="https://github.com/user-attachments/assets/681f37d7-787f-408d-9dd3-98dcb1b1f690" />





















