---
layout: FPGA Board
type: project
image: img/FPGABoard/FPGA.jpg
title: "FPGA Board"
# All dates must be YYYY-MM-DD format!
date: 2023-10-28
published: true
labels:
  - Xilinx Vivado
  - FPGA Board
  - LEDs
  - ALU Circuits
summary: "Implement an arithmetic logic unit to ALU and then implement the ALU to the FPGA board by using the Web-pack tool."
---

<img class="img-fluid" src="../img/FPGABoard/FPGA.jpg">

<h2> ALU Circuit </h2>
We are given an ALU to build in SystemVerilog. 

Now looking at the circuit there is a 3 different circuits within the circuit, the Register circuit, an ALU circuit, and a Multiplexer circuit.
	There are three three registers that we need, RegA, RegB, and RegY. All three of them synchronize with the clock signal of the FPGA board. RegY will always load a value for the Mux input, so it behaves like a 4D flip-flop. 

From the table, we know that every time the input ‘CLR’ is 1, the register is cleared. If ‘CLR’ is 0 and ‘LD’ is 1 then the register will load a new value. If both are 0, then the register holds its current value. Upon knowing this, we can build a Register Function.
This adds a register function, with a 4-bit input and output, along with a clock, load, and clear inputs. We will have a clock that every time it is positive, will execute the sequential logic. The sequential logic is a condition statement, that if clear is equal to 1, the output will be 0 clearing the register. If load is equal to 1, then the output will be updated with the value of the input and then loaded to the register. 
	The next circuit that we need to build would be the ALU. It is a combinational circuit and we are given a table to follow. 

On the table, we know that we have a 2-bit select input, 4-bit A and B input, and 4-bit Y output. At each select input(SelALU), it will be doing addition, subtraction, bit-wise OR, and bit-wise AND, to the A and B inputs to get the Y output. 

As we can see above, we have the input and outputs. The select input (SelALU) will be choosing which operations to use using a case statement. When SelALU is ‘00’ it will run ‘Y=A+B’, ‘01’ will run ‘Y=A-B’, ‘10’ will run ‘Y=A|B’, and lastly ‘11’ will run ‘Y=A&B’. Ultimately, outputting Y. 
The last circuit that we need is the 4:1 multiplexer circuit. This circuit will have its output connected to the LEDs of the FPGA board.

Here we have another 2-bit select input for mux(SelMUX) and an output of 4-bit M. The registers A, B, and Y from the very first circuit that I made from this will also become an input. 

So we have the inputs of 3-bit A, B, and Y, a 2-bit input of select input(SelMux), and a 4-bit output of M. Using the same logic as the last paragraph, the select input will be choosing which of the Registers A, B, and Y will equal M such as SelMux is ‘00’, output M will be Register A, ‘01’ output M will be Register B, ‘10’ output M will be Register Y, and ‘11’ output will be 0. If The output M is 1, then the LED corresponding to it will turn on, if 0 then it will be off. 
	Now that all the circuits are made, we have to connect them all so that they function as the circuit. As you can see, Register A and B outputs will be an input of ALU and MUX circuits. ALU circuit output will be the input of Register Y. Register Y will be the input of the MUX circuit, and then the output of the MUX circuit will connect to the LEDs of the FPGA board, which will turn on or off depending on the output. 

I made a topModule() function as the main module of all the circuits. It has the clock input(clk), a 2-bit push button(Pb) input, an 8-bit switch(s) input, and a 4-bit LEDs output. The wires declaration will connect the circuits acting as the input and output of the circuits. 
So to get Register A and Register B, we must call the Register function twice and instantiate a differing name such as regA and regB so we know what they are. Both registers are identical, they have 4 switches from switch 7 to 4, push button 2, and a clock because back on the register circuit it has a clock input that synchronizes with the FPGA board, so this is a must-have so it works properly. The difference is that regA has a push button 0 and the output will be wire 1(w1), while regB has a push button 1 with the output of wire 2(w2). 
	Again we call the function alu and instantiate a different name like ALU (all capitalized). Since we know the output of regA and regB are part of the input of ALU, we just add them as w1 and w2 as their input, along with switch 3 to 2 inputs, and then we can call the output as wire 3(w3).
	In the same format, call the function register again and instantiate a name regY. The input is the output of ALU which is w3 then add the clock. Now I put ‘1’ as an input to connect it to the load input from the register function and to indicate that the register should load the input value of w3 when the signal is asserted. The ‘0’ input connects to the clear input of the register function indicating that the register should not be cleared. 
	Lastly, we call the mux function and called it MUX.Wwe know that the w1, w2, and w4 are part of the input along with switch 1 and switch 0 outputting 4-bit LEDs. The LEDs 1 to 4 should turn on or off depending on the buttons and switches.


<h2> Field Programmable Gate Arrays Board </h2>
	If you followed the PDF “TutorialArtix-7Basys3”[3], then you should know that we had to download a folder with an important file called Basys-3-Master.xdc[3] on page 12. This is added to the constraints folder in Vivado. Basically, this file will reflect the inputs and outputs of the topModule function. It contains all the constraints that we need, and all we have to do is uncomment them. 

As you can see all the names of the switches, buttons, clock, and LEDs are exactly the same as the input and output of the topModule function. It has 8 switches which correspond to the 8-bit ‘s’ input, 3 push buttons correspond to the 3-bit input Pb, it has the clock as clk, and 4 LEDs which correspond to the 4-bit output LEDs.
Now when you don’t push any button or switch any switches on the FPGA, you get no light.

All the registers would be at 0 and the switches are off. Now if you flip the switch 2 to 5, LEDs[0] and LEDs[1] are turned on. 

When switches 2 to 5 are flipped, registers A and B will output 1 while register Y will output 0. In the MUX function, when M = 1, the LED corresponding to the M will turn on. Now if you turn on switches 3 to 6, you get the LEDs turned on.

The switches 3 to 6 turn on LEDs[0], LEDs[1], and LEDs[2]. Meaning that the output of regA, regB, and regY is equal to 1. However, the last LED is always off because back in the mux function, the very last M is equal to 0.
