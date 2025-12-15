AIM:

To implement 4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

SOFTWARE REQUIRED:

Quartus prime

THEORY

4 Bit Ripple Counter

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

<img width="1013" height="390" alt="Screenshot 2025-12-15 173744" src="https://github.com/user-attachments/assets/07e2acd7-1371-48d7-9b08-b5871505ca2c" />



In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

<img width="577" height="436" alt="Screenshot 2025-12-15 173800" src="https://github.com/user-attachments/assets/0611ca9c-5933-4a38-9444-0e2ca43f8cb8" />


<img width="458" height="343" alt="Screenshot 2025-12-15 173810" src="https://github.com/user-attachments/assets/52588ec0-110a-409e-8d7f-ad0177af4912" />



Procedure

1.Connect all JK flip-flops with J = K = 1.

2.Apply the external clock to the first flip-flop.

3.Connect Q0 to clock of second flip-flop, Q1 to clock of third, and so on.

4.Switch ON the power supply.

5.Apply clock pulses.

6.Observe the output sequence of the counter.

PROGRAM
~~~
module ripple_counter (q, clk, reset); 
output [3:0] q;
input clk, reset;
T_FF tffo(q[0], clk, reset); 
T_FF tff1(q[1], q[0], reset); 
T_FF tff2(q[2], q[1], reset); 
T_FF tff3(q[3], q[2], reset); 
endmodule

module D_FF(q, d, clk, reset); 
output q;
input d, clk, reset;
reg q;
always @(posedge reset or negedge clk)
 if (reset)
q = 1'b0;
 else
q = d;
endmodule

module T_FF(q, clk, reset);
output q;
input clk, reset;
wire d;
D_FF dff0(q, d, clk, reset);
not n1(d, q); // not is Verilog-provided primitive. 
endmodule

Developed by:JAYACHANDRA V

RegisterNumber: 25017587*/
~~~

RTL LOGIC FOR 4 Bit Ripple Counter

TIMING DIGRAMS FOR 4 Bit Ripple Counter

RESULTS

Thus the 4-bit ripple counter using verilog and validating their functionality using their functional tables is implemented and verified.

