# Neha856
<details>
	<summary>Week 0 - Tools Installation </summary>
	
# Week 0 - Tools Installation
## Yosys
```
# su – (for access as a root user)
# sudo apt-get update
# git clone https://github.com/YosysHQ/yosys.git
# cd yosys 
# sudo apt install make (If make is not installed please install it) 
# sudo apt-get install build-essential clang bison flex \libreadline-dev gawk tcl-dev libffi-dev git \graphviz   xdot pkg-config python3 libboost-system-dev \libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make 
$ sudo make install
```
## Yosys
```

root@Ubuntu:~# yosys

 /----------------------------------------------------------------------------\
 |  yosys -- Yosys Open SYnthesis Suite                                       |
 |  Copyright (C) 2012 - 2025  Claire Xenia Wolf <claire@yosyshq.com>         |
 |  Distributed under an ISC-like license, type "license" to see terms        |
 \----------------------------------------------------------------------------/
 Yosys 0.57+148 (git sha1 259bd6fb3, g++ 9.4.0-1ubuntu1~20.04.2 -fPIC -O3)

yosys> license

 /----------------------------------------------------------------------------\
 |                                                                            |
 |  yosys -- Yosys Open SYnthesis Suite                                       |
 |                                                                            |
 |  Copyright (C) 2012 - 2025  Claire Xenia Wolf <claire@yosyshq.com>         |
 |                                                                            |
 |  Permission to use, copy, modify, and/or distribute this software for any  |
 |  purpose with or without fee is hereby granted, provided that the above    |
 |  copyright notice and this permission notice appear in all copies.         |
 |                                                                            |
 |  THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES  |
 |  WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF          |
 |  MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR   |
 |  ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES    |
 |  WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN     |
 |  ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF   |
 |  OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.            |
 |                                                                            |
 \----------------------------------------------------------------------------/ 
 ```
## Iverilog
```
# sudo apt-get update
# sudo apt-get install iverilog
```
## Iverilog
```
  
root@Ubuntu:~# iverilog
iverilog: no source files.

Usage: iverilog [-ESvV] [-B base] [-c cmdfile|-f cmdfile]
                [-g1995|-g2001|-g2005|-g2005-sv|-g2009|-g2012] [-g<feature>]
                [-D macro[=defn]] [-I includedir]
                [-M [mode=]depfile] [-m module]
                [-N file] [-o filename] [-p flag=value]
                [-s topmodule] [-t target] [-T min|typ|max]
                [-W class] [-y dir] [-Y suf] [-l file] source_file(s)

See the man page for details.
```

## GTKWave
```
# sudo apt update
# sudo apt install gtkwave
```
## GTKWave
```
neha_iitk@Ubuntu:~$ gtkwave
Gtk-Message: 18:12:13.444: Failed to load module "canberra-gtk-module"

GTKWave Analyzer v3.3.103 (w)1999-2019 BSI

GTKWAVE | Use the -h, --help command line flags to display help.
```


# Day 1 - Introduction to Verilog RTL Design and Synthesis
## Introduction to open-source simulator Iverilog

Folder structure of the git clone:
- `lib` - will contain sky130 standard cell library
- `my_lib/verilog_models` - will contain standard cell verilog model
- `verilog_files` -contains the lab experiments source files

<img width="762" alt="intro_iverilog" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/ceceb871-47f9-4edc-8ec7-ac273dc5352c">


Example of a design good_mux.v and a testbench tb_good_mux.v 

<img width="1920" height="1043" alt="Image" src="https://github.com/user-attachments/assets/364baa1e-3e94-46a5-b93f-6d6009f2dec8">

Command to run the design and testbench
```
iverilog good_mux.v tb_good_mux.v
```
The output of the iverilog is a .vcd file and a.out file is created. By executing a.out iverilog dump the vcd file.

## Introduction to GTKWave
gtkwave will be used to generate the waveforms and display in visual format.

Command to view the vcd file in gtkwave 
```
gtkwave tb_good_mux.vcd
```
The waveform in gtwave is shown below

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/eab9617f-3c93-4a49-b403-8880c374d2a5">

## Introduction to Yosys
It is the synthesizer used to convert RTL to netlist.
Netlist should be the same as the Design but represented in the form of standard cells.
The same testbench can be used to verify RTL and Synthesized Netlist.

<img width="800" alt="intro_yosys" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/0920be6f-770d-447d-a2cf-eaf73280539e">

## Introduction to Logic Synthesis

<img width="611" alt="intro_logic_synthesis1" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/d01c7771-7bb7-42cd-b7a1-24472ca61226">

## Lab using Yosys and Sky130 PDKs
<img width="1920" height="1043" alt="yosyslab" src="https://github.com/user-attachments/assets/c53eb81e-a60b-488d-8b79-206c7303977d">

<img width="1920" height="1043" alt="showlogic" src="https://github.com/user-attachments/assets/41fd2b87-9c46-40b9-a2ef-1319120aafc2">

</details>

<details>

<summary>Day 2 - Timing libs, Hierarchical vs Flat Synthesis and Efficient Flop Coding Styles </summary>

# Day 2 - Timing libs, Hierarchical vs Flat Synthesis and Efficient Flop Coding Styles

## Introduction to timing .libs
Libraries are characterized based on PVT (process, voltage, temperature) \
Process -> Variations due to fabrication \
Voltage -> Variations due to voltage \
Temperature -> Variations due to temperature 

As seen in the screenshot below \
tt stands for typical in the .lib name \
025C stands for temperature of 25 C in the .lib name \
1v80 stands for voltage of 1.8V in the .lib name

<img width="1920" height="1043" alt="Image" src="https://github.com/user-attachments/assets/4bf87c5c-d665-4b07-a4b1-80b80b658fd9">

-cell defines the beginning of the cell. Other information of cells mentioned are:
- Leakage power based on the combination of inputs
- Area
- Power ports
- Input capacitance
- Power associated with the pin
- Transition
- Delay

## Hierarchical vs Flat Synthesis

### Hierarchical Synthesis
Report after synthesizing multiple_modules.v. As shown below the sub_modules statistics are printed. For example, sub-module1 has 1 AND gate and sub-module2 has 1 OR gate. This is an example of Hierarchical Synthesis.

<img width="1920" height="1043" alt="Image" src="https://github.com/user-attachments/assets/7af1d02d-f952-4309-92db-963b5b05ef2c">

Hierarchy is preserved. sub_module1 and sub_module2 are instantiated separately in the synthesized Verilog netlist. Rather than seeing AND or OR gate, we see sub_modules when we run the command 'show' as shown in the screenshot.

<img width="1920" height="1043" alt="Image" src="https://github.com/user-attachments/assets/c4bbf232-0efa-4fad-89ab-5e077c70e9ac">


If we look into the sub_module2 in synthesized netlist 'multiple_modules_hier.v', we see that rather than OR gate, the inputs a & b, pass through the inverter and then NAND gate. It is because in CMOS, stacking PMOS, which happens in 'OR' gate is bad as PMOS has lower mobility and always have to be wider to get some meaningful output. The next step is to check .lib file for the answer.

### Flat Synthesis
The design can be flattened by using the command `flatten`.

Screenshot shows the command, synthesized netlist and the logical diagram.

<img width="1920" height="1043" alt="Image" src="https://github.com/user-attachments/assets/f0a2bcec-1315-4f8e-8bb6-181e94857a6d">

<img width="1920" height="1043" alt="Image" src="https://github.com/user-attachments/assets/d9e9306f-5d24-43d1-8636-0df140c20b7c">

### Sub-module Level Synthesis
RTL (Register Transfer Level) designs are often modular, with various functional blocks or sub-modules. Sub-module level synthesis allows each of these sub-modules to be synthesized independently.

Why is the sub-module level synthesis necessary?
- Optimization and Area Reduction: By synthesizing sub-modules separately, the synthesis tool can optimize each one individually. It performs logic optimization, technology mapping, and area minimization for each sub-module. This leads to more efficient use of resources and reduced overall chip area.
- Resuability: Each submodule can be designed, verified, and optimized independently. They can be reused in a large design multiple times saving time and enhancing efficiency. 
- Parallel Processing: Different sub-modules can be synthesized concurrently, improving efficiency. For large designs, parallel synthesis significantly reduces turnaround time.

The commands to run sub-module synthesis
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog multiple_modules.v
synth -top sub_module1
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

The screenshot shows that when sub_module1 is synthesized, only AND gate is generated. 
<img width="1920" height="1043" alt="Image" src="https://github.com/user-attachments/assets/21d88211-a259-48f5-a937-c2836ad25c60">

## Various Flop Coding Styles and Optimization

### Why do we need flops and how do they prevent glitches in the circuit?

Glitches can occur in digital circuits due to various reasons such as signal delays, noise, or timing issues. Flops prevent glitches during the operation in the following ways:
- Synchronization: Flops are edge-triggered devices, meaning they respond only to transitions of the input signal (e.g., rising edge, falling edge). This synchronization ensures that the output changes only at specific points, reducing the likelihood of glitches caused by transient signal variations.
- Timing Control: Flops are typically controlled by a clock signal, ensuring that all circuit operations occur synchronously. This eliminates timing issues that could lead to glitches due to data arriving at different times.

<img width="846" altthe ="flops1" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/32aab966-261a-4e42-9f49-59572586cd0f">

### Different types of flops
To initialize flops, we need to `set` and `reset` which can be synchronous or asynchronous.

<img width="775" alt="syn_async_reset_flop1" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/338b941f-4a51-4cf3-9289-f344afac2922">

<img width="1920" height="1043" alt="Image" src="https://github.com/user-attachments/assets/c9bcc029-a626-4ba3-9225-4e0336cb9a94">

The screenshot below shows DFF with asynchronous reset HDL simulation in Iverilog and  waveform display in GTKwave. Irrespective of the clock and d, as soon as async_reset=1, q=0.

<img width="1920" height="1043" alt="Image" src="https://github.com/user-attachments/assets/5ee1db6b-63b9-4b86-be37-f60410987933">

### Synthesizing flops
The command to synthesize ***DFF with asynchronous reset*** as an example
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_asyncres.v
synth -top dff_asyncres
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```
<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/db3c931f-3d52-4c70-a798-927084cfeb23">

Similarly for dff_async_set 

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/b541638d-b7bc-44e0-bac4-5f18e09d9da4">


On synthesizing ***DFF with synchronous reset*** we get NOR gate with inverted `d` as shown in the screenshot below. However,on evaluating the boolean expression, we reached the same logic realization. 


<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/d78c3c35-3760-4fcd-b2e2-a6d198d3cdbe">

<img alt="dff_sync_reset2" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/81c0b90f-06af-4ee9-9f10-b8f4f8f743a7" width="700" height="500">

Using the `stat` command, all the cells used for logic synthesis are visible even though it is not evident from the statistics of doing synthesis.




### Synthesizing mult2 (multiply by 2)

 
To implement `y[3:0] = 2*a[2:0]`, we append a `1'b0 `to the `a[2:0]` i.e, `y[3:0] = {a[2:0],0}`. This is also equal to left shift the input bits by 1.
This can be realized by just wiring.
So we expect no hardware which is also seen in the screenshot below, analysis after synthesis and show. The command 'abc' is not required for mapping when there are no cells.

<img width="1920" height="1043" alt="Image" src="https://github.com/user-attachments/assets/c58f8c4d-20a3-426a-8284-42163c22506c">

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/e47abe5c-ae7e-4b0a-808a-796ec79d3fa6">
### Synthesizing mult9 (multiply by 9 or 8+1)

`y=9*a` can be considered `8*a+1*a`
To implement `y[5:0] = 9*a[2:0]`, we append `000` to `a[2:0]` and then add `a` i.e, `y[5:0] = {a[2:0],000} + a[2:0]`.
This can be realized just by wiring.
So we expect no hardware which is also seen in the screenshot below, analysis after synthesis and show. The command 'abc' is not required for mapping when there are no cells.

<img width="918" alt="mult8_syn" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/dd1b4634-50ed-4229-9d82-80689bafb7e7">
</details>

<details>
	<summary>Day 3 - Combinational and Sequential Optimizations </summary>
	
# Day 3 - Combinational and Sequential Optimizations

## Introduction to Optimizations

### Combinational Logic Optimization
It means squeezing the logic to get the most optimized design in terms of area and power. the most commonly used techniques are:
1) Constant propagation using direct optimization
2) Boolean logic optimization using K-map and Quine McKlusky

An example of constant propagation optimization is highlighted below.
<img width="618" alt="1_const_prop" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/c8bd1118-52f7-441b-8cff-254d851cb892">

An example of boolean optimization is highlighted below.

<img width="619" alt="2-boolean-opt" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/aa864102-ef33-4d45-9ec9-929738172cd4">

### Sequential Logic Optimization
The technqiues used are:
1) Basic
   - Sequential constant propagation
2) Advanced (not covered as part of lab)
   - Static optimization
   - Retiming
   - Sequential logic cloning (floorplan aware synthesis)

An example of sequential constant propagation is highlighted below of DFF with asynchronous reset where D input is grounded. To note, the same technique cannot be applied to DFF with the asynchronous set because while `Q=1` when `Set=1`, but `Q=0` at `Set=0` at the next CLK pulse. Q is dependent not only on Set but also on the clock edge.

<img width="629" alt="3-seq-const-prop" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/3e31a212-a0b0-42c3-be92-d0075a9f7d1c">

Retiming is a technique to improve the performance of the circuit.

<img width="600" alt="4-seq-adv" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/23bcc15c-813b-496a-aebf-ebbf5ceba557">

## Combinational Logic Optimizations
Commands for optimization

```
opt_clean -purge
```
### Optimization of opt_check.v
Syntax for opt_check.v
```
module opt_check (input a , input b , output y);
        assign y = a?b:0;
endmodule
```
For opt_check.v the assignment `y = a?b:0` reduces to `y = ab`. The screenshot shown below explains this

<img width="533" alt="5-seq-opt" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/f4b6a999-f665-412f-a705-9496bfdd04c2">

The logic implementation after synthesis for opt_check.v is shown below, showing only AND gate.

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/68ebce10-6b7d-4ba5-916a-571f0233a486">


### Optimization of opt_check2.v
Syntax for opt_check2.v
```
module opt_check2 (input a , input b , output y);
        assign y = a?1:b;
endmodule
```
For opt_check2.v the assignment `y = a?1:b` reduces to `y = a + b`. 

The logic implementation after synthesis for opt_check2.v is shown below, showing only OR gate.

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/9f71ceef-1121-44f0-8d47-76cf48c25945">

### Optimization of opt_check3.v
Syntax for opt_check3.v
```
module opt_check3 (input a , input b, input c , output y);
	assign y = a?(c?b:0):0;
endmodule
```
For opt_check.v the assignment `y = a?(c?b:0):0` reduces to `y = abc`. The screenshot shown below explains this.

<img width="541" alt="8-opt-check3" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/c9fb59d8-d080-4776-bec6-46e3b48b3d68">

The logic implementation after synthesis for opt_check3.v is shown below, showing 3 input AND gate.

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/ccdcb29c-2744-4c0f-94c2-9820ac6b22e5">

similarly The logic implementation after synthesis for opt_check3.v is shown below,

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/ae78ecd4-af4b-48a0-b91e-e6fa4ce38329">

### Optimization of multiple_module_opt.v

Syntax of multiple_module_opt.v
```
module sub_module2 (input a, input b, output y);
	assign y = a | b;
endmodule

module sub_module1 (input a, input b, output y);
	assign y = a&b;
endmodule


module multiple_modules (input a, input b, input c , output y);
	wire net1;
	sub_module1 u1(.a(a),.b(b),.y(net1));  //net1 = a&b
	sub_module2 u2(.a(net1),.b(c),.y(y));  //y = net1|c ,ie y = a&b + c;
endmodule

```
synthesis for multiple_module_opt.v is shown below

<img width="1920" height="1043" alt="Image" src="https://github.com/user-attachments/assets/867c43f4-ac86-47b5-b809-96a65f4241aa">

The logic implementation after synthesis for multiple_module_opt.v is shown below.

<img width="1920" height="1043" alt="Image" src="https://github.com/user-attachments/assets/dd467269-1a3f-44ec-be29-1a06eb70cff7">


## Sequential Logic Optimizations

Both the dff_const1.v and dff_const2 are explained below.

<img width="851" alt="12-dff-const1-const2" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/b9bede59-edaa-4f4f-ad90-9036c63aa4da">

### Optimizing dff_const1.v

Syntax for dff_const1.v
```
module dff_const1(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
end

endmodule
```
For dff_const1.v, `q=0` as long as `reset=1`. However, when `reset=0` `q` doesn't immediately becomes `1` rather at the next rising edge of the `clk` as shown below. ***So the optimization cannot be applied***.

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/70ed95b9-1f9f-47f4-9182-732e87cb3a32">

The commands to run the synthesis
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const1.v
synth -top dff_const1
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

The logic implementation after synthesis for dff_const1.v is shown below.

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/cc19c738-7542-46f5-95a4-b64c8a802ffb">

***complete dff_const2,3,4,5***

### Optimizing dff_const3.v

Syntax for dff_const3.v
```
module dff_const3(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b1;
		q1 <= 1'b0;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
```
For dff_const3.v, there are two flops.  `q1=0` as long as `reset=1`. However, when `reset=0` `q1` doesn't immediately becomes `1` rather at the next rising edge of the `clk` with some propagation delay as shown below. `q=1` as long as `reset=1`, acting as `set` rather than `reset`. However, when `reset=0` `q` samples `q1` as `0` as there are some propagation delay for `q1`as shown below. At the next `clk` edge `q` samples `q1` as `1`.
***So the optimization cannot be applied***.

<img width="973" alt="14-dff-const3" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/6bf8a7c4-07f1-4f70-9878-e2773b3eeab5">

The command to run HDL simulation
```
iverilog dff_const3.v tb_dff_const3.v
./a.out
gtkwave tb_dff_const3.vcd
```
The HDL simulation is shown below.

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/f0a8ffdc-8f06-41a3-92b6-cdd28c458df9">

The commands to run the synthesis
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const3.v
synth -top dff_const3
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

The logic implementation after synthesis for dff_const3.v is shown below.

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/e87b6486-27e5-4564-80b2-4433fbb8a843">

Similarly done dff_const5.v and The logic implementation after synthesis for dff_const5.v is shown below.

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/b5b35f56-f535-4e3c-a566-3228ee568914">

## Sequential Optimzations for Unused Outputs

### Optimization of Case1: 3-bit Up Counter with q[0] used (counter_opt.v)
Example of a counter where bits at the position of [2] and [1] are unused.

```
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = count[0];

always @(posedge clk ,posedge reset)
begin
	if(reset)
		count <= 3'b000;
	else
		count <= count + 1;
end

endmodule
```
The screenshot explains the logic of the counter. Only q[0] is used. ***So the optimization can be applied***.

<img width="1200" alt="17-counter" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/dbdbd8d5-a305-4f31-b8ba-a8c33d53d67a">

The commands to run the synthesis
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog counter_opt.v
synth -top counter_opt
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```
We see only one flop after the synthesis and also seen in synthesis report after `synth -top counter_opt.v`

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/7c5f39e8-73eb-4145-9b4b-0fffa1328161">

### Optimization of Case2: 3-bit Up Counter (counter_opt2.v)

Example of a counter where all the bits are used.
```
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = (count[2:0] == 3'b100);

always @(posedge clk ,posedge reset)
begin
	if(reset)
		count <= 3'b000;
	else
		count <= count + 1;
end

endmodule
```
The commands to run the synthesis
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog counter_opt.v
synth -top counter_opt
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```
We see only 3 flops after the synthesis and also seen in synthesis report after `synth -top counter_opt.v`
<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/f39b40ca-7619-4b20-a736-7a8efce186f9">

<img width="1167" alt="21-counter-opt2" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/11cd582b-4ccd-4b99-82e2-1c68c92db131">

</details>

<details>

 <summary>Day 4 - GLS, Blocking vs Non-blocking and Synthesis-Simulation Mismatch</summary>
 
# Day 4 - GLS, Blocking vs Non-blocking and Synthesis-Simulation Mismatch

## GLS, Synthesis-Simulation Mismatch, and Blocking/Non-blocking Statements

### Why is Gate Level Simulation (GLS) necessary?
- Verify the correctness of the design after synthesis
- Ensure the timing of the design is met which is done with delay annotation (timing aware)

  <img width="628" alt="1-gls-iverilog" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/e3bef5db-4722-4561-ad10-0370a924fdc9">
  
### Synthesis Simulation Mismatches

It happens because of the following reasons
- Missing sensitivity list
- Blocking vs non-blocking assignments
- Non-standard verilog coding

#### (1) Missing sensitivity list

As shown in the screenshot below, `always` block is evaluated only when `sel` is changing. So output `y` is not evaluated when `sel` is not changing although `i0` and `i1` are changing. Rather it acts like a latch. The code on the right side represents the correct design coding for `mux`. In this case `always` is evaluated for any signal changes. 

<img width="632" alt="2-missing-sensitivity-list" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/5c494646-600e-4b19-a3ce-7db8c1baa5a7">

#### (2) Blocking vs Non-blocking Assignments

 ##### Blocking Statements
 
 - Represented by `=`
 - Executes the statements in the order it is written inside always block
 - So the first statement is evaluated before the second statement

##### Non-Blocking Statements
- Represented by `<=`
- Executes all the RHS when always block is entered and assigns to LHS
- Parallel execution

   The left side of the screenshot below gives us the correct execution. While the right side can lead to serious issues as `d` is assigned to `q` directly. ***So choosing non-blocking statements is best practice*** (highlighted in the screenshot below).

<img width="612" alt="4-blocking-statement" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/bde53551-9858-4eee-afd2-f37cd0dff762">

 ##### Blocking Statements Leading to Synthesis Simulation Mismatch

In the code shown below, `y` gets the old `q0` value. This will mimic delay or flop. But when you synthesize, there will be no flop. If the order is changed (right side code), latest value of `q0` is assigned to `y`. 

When synthesized, both will lead to the same circuit. However, simulation will result in different behavior. For the left side of the code, `y` gets the old `q0` value and for the right side of the code, `y` gets the latest `q0` value leading to a synthesis simulation mismatch. 

This issue is resolved by using ***non-blocking statements***.

 <img width="615" alt="5-blocking-statement" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/aed8bcbb-ca5e-467d-bfd7-8c679ce91263">

## Labs on GLS and Synthesis-Simulation Mismatch

### Ternary operator MUX (ternary_operator_mux.v)

The Verilog code of ternary_operator_mux.v
```
module ternary_operator_mux (input i0 , input i1 , input sel , output y);
	assign y = sel?i1:i0;
	endmodule
```
The command to run HDL simulation
```
iverilog ternary_operator_mux.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
```
HDL Simulation waveform of ternary_operator_mux.v is shown in the screenshot below

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/60144e5c-b014-4a9e-a01a-6378972f105f">

The commands to run the synthesis for ternary_operator_mux.v
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog ternary_operator_mux.v
synth -top ternary_operator_mux
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog ternary_operator_mux_net.v
```

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/36c08a16-bf95-42ed-afc2-b0ad06a7dc2a">

The commands to do GLS for ternary_operator_mux.v
```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
```
The GLS output is shown below.
<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/842e8e88-960b-4894-bfa3-5d169f9c708e">

### Bad MUX (bad_mux.v)

The `always` block is executed only at `sel` signal. It works like a flop rather than mux.
The Verilog code of bad_mux.v
```
module bad_mux (input i0 , input i1 , input sel , output reg y);
always @ (sel)
begin
	if(sel)
		y <= i1;
	else 
		y <= i0;
end
endmodule
```

The command to run HDL simulation
```
iverilog bad_mux.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```
HDL Simulation waveform of bad_mux.v is shown in the screenshot below

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/fe4ae747-d0be-43ad-917f-505cb2146d1f">

The commands to run the synthesis for bad_mux.v.
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog bad_mux.v
synth -top bad_mux
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog bad_mux_net.v
```

The synthesis report shows it is still inferring the mux but not the flop.

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/b5a71d48-b33a-42af-b55c-4c090b4d99ac">

The commands to do GLS for bad_mux.v
```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v bad_mux_net.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```
The GLS output is shown below. This shows correct functionality which is different from HDL simulation, leading to ***synthesis simulation mismatch***.

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/4e61ce3d-0957-473f-ab00-47c177a68648">

## Labs on Synthesis-Simulation Mismatch for Blocking Statements

### Blocking Caveat (blocking_caveat.v)

The logic to simulate is shown below.
<img width="594" alt="12-blocking-caveat" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/d7e6ea20-93fb-41d4-9f56-9910fe8f9931">

The Verilog code of blocking_caveat.v
```
module blocking_caveat (input a , input b , input  c, output reg d); 
reg x;
always @ (*)
begin
	d = x & c;
	x = a | b;
end
endmodule
```

The command to run HDL simulation
```
iverilog blocking_caveat.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
```
HDL Simulation waveform of blocking_caveat.v is shown in the screenshot below. `d` takes the old value of `x` causing incorrect functionality.

<img width="976" alt="13-blocking caveat" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/0a3a28b9-9647-47b5-83dd-eec1d81092cc">


The commands to run the synthesis for bad_mux.v.
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog blocking_caveat.v
synth -top blocking_caveat
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog blocking_caveat_net.v
```

The synthesis report and logic synthesis is shown below.

<img width="1007" alt="14-blocking-caveat" src="https://github.com/sukanyasmeher/sfal-vsd/assets/166566124/2e61c1bd-37b6-4a38-bf5f-39c345f2305b">


The commands to do GLS for bad_mux.v
```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_net.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
```
The GLS output is shown below. In this case, `d` takes the current value of `x` causing incorrect functionality.The waveform shows correct functionality which is different from HDL simulation, leading to ***synthesis simulation mismatch***.

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/4e61ce3d-0957-473f-ab00-47c177a68648">

</details>

<details>
	<summary>Day 5 - Introduction to DFT</summary>
	
# Day 5 - Optimization in Synthesis 

## Introduction:
When we write RTL (Register Transfer Level) code in VHDL/Verilog/SystemVerilog, the synthesis tool tries to map it into actual hardware (gates, flip-flops, multiplexers, etc.).

Optimization means:

-Reducing area (number of gates/transistors)

-Improving timing (speed, critical path delay)

-Reducing power consumption

-Removing unused logic (dead code elimination, constant propagation).
 
# If case constructs 

These are decision-making constructs used to describe conditional hardware.

## Incomplete IF 

if → priority-based logic (good when one condition should override others).

<img width="710" height="329" alt="Image" src="https://github.com/user-attachments/assets/e685d169-f39a-4d4e-8edb-4cce5b540008">

HDL Simulation waveform of incomp_if.v is shown in the screenshot below
<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/5ea90042-a4f0-4ff5-8c7e-e54a1fa079d6">

Here whenever i0=high at that time my y=i1 and when i0=low , y is latching on that value.and after logic synthesis in yosys we get

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/d2a741e8-bd61-4859-bed0-925f1138c85e">

## Incomplete case

case → parallel, no implied priority (good for encoding/decoding states, ALUs, multiplexers).
<img width="970" height="473" alt="Image" src="https://github.com/user-attachments/assets/2174a15d-7947-45bc-92de-a8c30ebc0fed">

HDL Simulation waveform of incomp_case.v is shown in the screenshot below
<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/0572a52d-0148-46d7-bffb-4a9c3fd0e944">

Here when select line sel=00, y following io, when sel=01, y follows i1 and when sel=10and11,y latching on the value of y before.and after logic synthesis in yosys we get

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/d53a2356-8b9d-43f6-ac6d-508ac7da3aec">
 
## Complete case 

-In a case statement, all possible values of the case expression are covered by case items or default.

-This ensures no undefined outputs and avoids latch inference in synthesis.

<img width="655" height="369" alt="Image" src="https://github.com/user-attachments/assets/d81bc0d4-6fab-4682-a247-2c020a81cbc3">


HDL Simulation waveform of incomp_case.v is shown in the screenshot below
<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/ab9f0d6d-ba81-408e-9a57-a10f006e7d1f">

After logic synthesis in yosys we get

<img width="1920" height="1042" alt="Image" src="https://github.com/user-attachments/assets/f04c5c1c-6766-46ae-a699-bf4c8de64a67">

