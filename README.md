### TITTLE

### DESIGN AND SIMULATE AN SR FLIP FLOP WITH A NOR GATE AND POSITIVE EDGE TRIGGERING IN VERILOG:

### HARDWARE REQUIRED:

A computer, Verilog simulation tool,Verilog development environment,SR flip-flop with NOR gate

### Procedure

### STEP 1:

In this code, we define a module called sr_flipflop that takes inputs s (set), r (reset), and clk (clock), and outputs q (flip-flop output) and q_bar (inverted output).

### STEP 2:

Inside the module, we declare two registers q and q_bar to store the values of q and its complement, respectively.

### STEP 3:

We use a positive edge-triggered clock (@(posedge clk)) to trigger the flip-flop's behavior. When the clock's rising edge occurs, the logic inside the always block is executed.

### STEP 4:

We use an if-else if statement to implement the behavior of the SR flip-flop. If s is high (1) and r is low (0), the flip-flop is set, and the output q is set to high (1). If s is low (0) and r is high (1), the flip-flop is reset, and the output q is set to low (0).

### STEP 5:

Finally, we use the assign statement to assign the inverted value of q to q_bar.

### STEP 6:

To simulate this SR flip-flop, you can write a testbench in Verilog that provides different inputs (s, r, and clk) and observes the outputs (q and q_bar). You can use any Verilog simulator, such as ModelSim or Xilinx ISE, to run the simulation and observe the behavior of the SR flip-flop.

### STEP 7:

End the program

### THEORY:

SR Flip flop are the basic element of the sequential circuit. Flip flop is a digital circuit capable of storing single bit of binary data. They can store either of the two stable state that is binary zero or one. If flip flop is set to one particular state it will store that until power is switched off or until you have changed the state. Means flip flop remember the state it was previously set and memorizes the date provided to it. Here we have designed the SR flip flop with the use of NOR gate.

SR flip flop or SR latch is the most essential and widely used flip flop. It is also known as SET-RESET flip flop. 

SR flip flop has two inputs S and R. S is used to set the flip flop and R is used to reset the flip flop and two outputs Q and Q(NOT)  in this one is complement of another. 

### LOGIC DIAGRAM

![image](https://github.com/Anandanaruvi/Simulation-project--Digital-Electronics/assets/120443233/23c4e543-7ae1-4ad0-9d1e-f0430920f6e8)

### PROGRAM
NAME: A.ARUVI

REF NO: 212222230014

``` 
module sr_flipflop (
  input s, r, clk,
  output q, q_bar
);

  wire s_nor_r;
  wire r_nor_s;

  nor (s_nor_r, s, r);
  nor (r_nor_s, r, s);

  d_flipflop flipflop (
    .d(1'b1),
    .clk(clk),
    .q(q),
    .q_bar(q_bar)
  );

endmodule

module d_flipflop (
  input d, clk,
  output reg q, q_bar
);

  always @(posedge clk) begin
    q <= d;
    q_bar <= ~d;
  end

endmodule
```
### NETLIST DIAGRAM
```
s  ────────┐
           ├──────┐
r ────────┘      │
                 ├───────► q
clk ──────────────┘
        NOR Gate
```
### TIMING DIAGRAM
```
    +---+            +---+
        |   |            |   |
   S -- |   |------------|   |
        |   |            |   |
   R -- |   |------------|   |
        |   |            |   |
  CLK --|   |_____/\/\/\__|   |
        |   |     ↑      |   |
        |   |     |      |   |
   Q -- |   |_____↓______|   |
        |   |            |   |
  Q_bar-|___|____________|___|
         ↑   ↑            ↑   ↑
        Tsetup Thold      Tpd Tpd 
```
### TRUTH TABLE:
```
 S  |  R  |  CLK  ||  Q  |  Q_bar
----------------------------------
  0  |  0  |   0   ||  Q  |  Q_bar
  0  |  0  |   1   ||  Q  |  Q_bar
  0  |  1  |   0   ||  Q  |  Q_bar
  0  |  1  |   1   ||  0  |   1
  1  |  0  |   0   ||  Q  |  Q_bar
  1  |  0  |   1   ||  1  |   0
  1  |  1  |   0   ||  Q  |  Q_bar
  1  |  1  |   1   ||  X  |   X
```
### Result 

Thus the sr flip flop with a nor gate has been designed and stimulated.
