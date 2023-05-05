Download Link: https://assignmentchef.com/product/solved-ece253-lab-6-finite-state-machines
<br>
This is an exercise in using finite state machines.

Part I

We wish to implement a finite state machine (FSM) that recognizes two specific sequences of applied input symbols, namely four consecutive 1s or four consecutive 0s. There is an input <em>w </em>and an output <em>z</em>. Whenever <em>w </em>=1 or <em>w </em>=0 for four consecutive clock pulses the value of <em>z </em>has to be 1; otherwise, <em>z </em>=0. Overlapping sequences are allowed, so that if <em>w </em>=1 for five consecutive clock pulses the output <em>z </em>will be equal to 1 after the fourth and fifth pulses. Figure 1 illustrates the required relationship between <em>w </em>and <em>z</em>.

Figure 1: Required timing for the output <em>z</em>.

A state diagram for this FSM is shown in Figure 2. For this part you are to manually derive an FSM circuit that implements this state diagram, including the logic expressions that feed each of the state flip-flops. To implement the FSM use nine state flip-flops called <em>y</em><sub>8</sub><em>,…,y</em><sub>0 </sub>and the one-hot state assignment given in Table 1.

Figure 2: A state diagram for the FSM.

<table width="176">

 <tbody>

  <tr>

   <td width="48"> </td>

   <td width="128">State Code</td>

  </tr>

  <tr>

   <td width="48">Name</td>

   <td width="128"><em>y</em>8<em>y</em>7<em>y</em>6<em>y</em>5<em>y</em>4<em>y</em>3<em>y</em>2<em>y</em>1<em>y</em>0</td>

  </tr>

  <tr>

   <td width="48">A</td>

   <td width="128">000000001</td>

  </tr>

  <tr>

   <td width="48">B</td>

   <td width="128">000000010</td>

  </tr>

  <tr>

   <td width="48">C</td>

   <td width="128">000000100</td>

  </tr>

  <tr>

   <td width="48">D</td>

   <td width="128">000001000</td>

  </tr>

  <tr>

   <td width="48">E</td>

   <td width="128">000010000</td>

  </tr>

  <tr>

   <td width="48">F</td>

   <td width="128">000100000</td>

  </tr>

  <tr>

   <td width="48">G</td>

   <td width="128">001000000</td>

  </tr>

  <tr>

   <td width="48">H</td>

   <td width="128">010000000</td>

  </tr>

  <tr>

   <td width="48">I</td>

   <td width="128">100000000</td>

  </tr>

 </tbody>

</table>

Table 1: One-hot codes for the FSM.

Design and implement your circuit on the DE1-SoC board as follows:

<ol>

 <li>Create a new Quartus project for the FSM circuit.</li>

 <li>Write a Verilog file that instantiates the nine flip-flops in the circuit and which specifies the logic expressionsthat drive the flip-flop input ports. Use only simple assign statements in your Verilog code to specify the logic feeding the flip-flops. Note that the one-hot code enables you to derive these expressions by inspection.</li>

</ol>

Use the toggle switch <em>SW</em><sub>0 </sub>on the DE1-SoC board as an active-low synchronous reset input for the FSM, use <em>SW</em><sub>1 </sub>as the <em>w </em>input, and the pushbutton <em>KEY</em><sub>0 </sub>as the clock input which is applied manually. Use the red light <em>LEDR</em><sub>9 </sub>as the output <em>z</em>, and assign the state flip-flop outputs to the red lights <em>LEDR</em><sub>8 </sub>to <em>LEDR</em><sub>0</sub>.

<ol start="3">

 <li>Include the Verilog file in your project, and assign the pins on the FPGA to connect to the switches and theLEDs.</li>

 <li>Simulate the behavior of your circuit.</li>

 <li>Once you are confident that the circuit works properly as a result of your simulation, download the circuitinto the FPGA chip. Test the functionality of your design by applying the input sequences and observing the output LEDs. Make sure that the FSM properly transitions between states as displayed on the red LEDs, and that it produces the correct output values on <em>LEDR</em><sub>9</sub>.</li>

 <li>Finally, consider a modification of the one-hot code given in Table 1. It is often desirable to set all flip-flopoutputs to the value 0 in the reset state.</li>

</ol>

Table 2 shows a modified one-hot state assignment in which the reset state, <em>A</em>, uses all 0s. This is accomplished by inverting the state variable <em>y</em><sub>0</sub>. Create a modified version of your Verilog code that implements this state assignment. (<em>Hint</em>: you should need to make very few changes to the logic expressions in your circuit to implement the modified state assignment.)

<ol start="7">

 <li>Compile your new circuit and test it.</li>

</ol>

<table width="176">

 <tbody>

  <tr>

   <td width="48"> </td>

   <td width="128">State Code</td>

  </tr>

  <tr>

   <td width="48">Name</td>

   <td width="128"><em>y</em>8<em>y</em>7<em>y</em>6<em>y</em>5<em>y</em>4<em>y</em>3<em>y</em>2<em>y</em>1<em>y</em>0</td>

  </tr>

  <tr>

   <td width="48">A</td>

   <td width="128">000000000</td>

  </tr>

  <tr>

   <td width="48">B</td>

   <td width="128">000000011</td>

  </tr>

  <tr>

   <td width="48">C</td>

   <td width="128">000000101</td>

  </tr>

  <tr>

   <td width="48">D</td>

   <td width="128">000001001</td>

  </tr>

  <tr>

   <td width="48">E</td>

   <td width="128">000010001</td>

  </tr>

  <tr>

   <td width="48">F</td>

   <td width="128">000100001</td>

  </tr>

  <tr>

   <td width="48">G</td>

   <td width="128">001000001</td>

  </tr>

  <tr>

   <td width="48">H</td>

   <td width="128">010000001</td>

  </tr>

  <tr>

   <td width="48">I</td>

   <td width="128">100000001</td>

  </tr>

 </tbody>

</table>

Table 2: Modified one-hot codes for the FSM.

Part II

For this part you are to write another style of Verilog code for the FSM in Figure 2. In this version of the code you should not manually derive the logic expressions needed for each state flip-flop. Instead, describe the state table for the FSM by using a Verilog case statement in an always block, and use another always block to instantiate the state flip-flops. You can use a third always block or simple assignment statements to specify the output <em>z</em>. To implement the FSM, use four state flip-flops <em>y</em><sub>3</sub><em>,…,y</em><sub>0 </sub>and binary codes, as shown in Table 3.

<table width="122">

 <tbody>

  <tr>

   <td width="48"> </td>

   <td width="74">State Code</td>

  </tr>

  <tr>

   <td width="48">Name</td>

   <td width="74"><em>y</em>3<em>y</em>2<em>y</em>1<em>y</em>0</td>

  </tr>

  <tr>

   <td width="48">A</td>

   <td width="74">0000</td>

  </tr>

  <tr>

   <td width="48">B</td>

   <td width="74">0001</td>

  </tr>

  <tr>

   <td width="48">C</td>

   <td width="74">0010</td>

  </tr>

  <tr>

   <td width="48">D</td>

   <td width="74">0011</td>

  </tr>

  <tr>

   <td width="48">E</td>

   <td width="74">0100</td>

  </tr>

  <tr>

   <td width="48">F</td>

   <td width="74">0101</td>

  </tr>

  <tr>

   <td width="48">G</td>

   <td width="74">0110</td>

  </tr>

  <tr>

   <td width="48">H</td>

   <td width="74">0111</td>

  </tr>

  <tr>

   <td width="48">I</td>

   <td width="74">1000</td>

  </tr>

 </tbody>

</table>

Table 3: Binary codes for the FSM.

A suggested skeleton of the Verilog code is given in Figure 3.

module part2 ( <em>… </em>);

<em>… </em>define input and output ports

<em>… </em>define signals

reg [3:0] y_Q, Y_D;               // y_Q represents current state, Y_D represents next state parameter A = 4’b0000, B = 4’b0001, C = 4’b0010, D = 4’b0011, E = 4’b0100, F = 4’b0101, G = 4’b0110, H = 4’b0111, I = 4’b1000;

always @(w, y_Q)

begin: state_table case (y_Q)

A: if (!w) Y_D = B; else Y_D = F;

<em>… </em>remainder of state table default: Y_D = 4’bxxxx;

endcase

end // state_table

always @(posedge Clock) begin: state_FFs <em>… </em>end // state_FFS

<em>… </em>assignments for output z and the LEDs endmodule

Figure 3: Skeleton Verilog code for the FSM.

Implement your circuit as follows.

<ol>

 <li>Create a new project for the FSM.</li>

 <li>Include in the project your Verilog file that uses the style of code in Figure 3. Use the same switches,pushbuttons, and lights that were used in Part I.</li>

 <li>Before compiling your code it is necessary to explicitly tell the Synthesis tool in Quartus that you wish tohave the finite state machine implemented using the state assignment specified in your Verilog code. If you do not explicitly give this setting to Quartus, the Synthesis tool will automatically use a state assignment of its own choosing, and it will ignore the state codes specified in your Verilog code. To make this setting, choose Assignments &gt; Settings in Quartus, and click on the Compiler Settings item on the left side of the window, then click on the Advanced Setting (Synthesis) button. As indicated in Figure 4, change the parameter State Machine Processing to the setting User-Encoded.</li>

 <li>Compile your project. To examine the circuit produced by Quartus open the RTL Viewer tool. Double-clickon the box shown in the circuit that represents the finite state machine, and determine whether the state diagram that it shows properly corresponds to the one in Figure 2. To see the state codes used for your FSM, open the Compilation Report, select the Analysis and Synthesis section of the report, and click on State Machines.</li>

 <li>Download the circuit into the FPGA chip and test its functionality.</li>

 <li>In step 3 you instructed the Quartus Synthesis tool to use the state assignment given in your Verilog code. Tosee the result of removing this setting, open again the Quartus settings window by choosing Assignments &gt; Settings, and click on the Compiler Settings item, then click on the Advanced Settings (Synthesis button. Change the setting for State Machine Processing from User-Encoded to One-Hot. Recompile the circuit and then open the report file, select the Analysis and Synthesis section of the report, and click on State Machines. Compare the state codes shown to those given in Table 2, and discuss any differences that you observe.</li>

</ol>

Figure 4: Specifying the state assignment method in Quartus.

Part III

In this part of the exercise you are to implement a Morse-code encoder using an FSM. The Morse code uses patterns of short and long pulses to represent a message. Each letter is represented as a sequence of dots (a short pulse), and dashes (a long pulse). For example, the first eight letters of the alphabet have the following representation:

A • — B — •••

C        — • — • D             — •• E    • F          •• — •

G        — — •

<h1>                                                                                    H         ••••</h1>

Design and implement a Morse-code encoder circuit using an FSM. Your circuit should take as input one of the first eight letters of the alphabet and display the Morse code for it on a red LED. Use switches <em>SW</em><sub>2−0 </sub>and pushbuttons <em>KEY</em><sub>1−0 </sub>as inputs. When a user presses <em>KEY</em><sub>1</sub>, the circuit should display the Morse code for a letter specified by <em>SW</em><sub>2−0 </sub>(000 for A, 001 for B, etc.), using 0.5-second pulses to represent dots, and 1.5-second pulses to represent dashes. Pushbutton <em>KEY</em><sub>0 </sub>should function as an asynchronous reset.

A high-level schematic diagram of a possible circuit for the Morse-code encoder is shown in Figure 5.

Figure 5: High-level schematic diagram of the circuit for Part IV.

Preparation and In-Lab Marks