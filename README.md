# Verilog-Code-for-Swapping-Three-Numbers
## SHARUN N (212223060257)
## Aim
To design and simulate a Verilog HDL code for swapping the values of three numbers without using any temporary variables, and verify the correctness of the swapping operation through a testbench using the Vivado 2023.1 simulation environment.

## Apparatus Required
Vivado 2023.1 or equivalent Verilog simulation tool.

## Procedure
Launch Vivado 2023.1:

Open Vivado and create a new project.
Write the Verilog Code for Swapping:

Write the Verilog code that swaps the values of three numbers (a, b, and c) using basic arithmetic or bitwise operations without using temporary variables.
Create the Testbench:

Write a testbench to simulate the swapping operation. The testbench should initialize three numbers, trigger the swapping module, and check if the values are swapped correctly.
Add the Verilog Files:

Add the Verilog module and the testbench file to the Vivado project.
Run Simulation:

Run the behavioral simulation in Vivado to verify the swapping operation.
Observe the Waveforms:

Examine the waveform to confirm that the values of the three numbers are swapped as expected.
Save and Document Results:

Capture the waveform output and include the results in your report for verification.

## Verilog Code:
### By Blocking 
```
`timescale 1ns/1ps
module swap(a,b,c,clk,aout,bout,cout);
input [3:0]a,b,c;
output reg[3:0] aout,bout,cout;
input clk;
always @(posedge clk)
begin
aout=b;
bout=c;
cout=a;
end
endmodule
```
### By Non-Blocking
```
`timescale 1ns/1ps
module swapnonblocking(
  input [3:0] a, b, c,
  input clk,
  output reg [3:0] aout, bout, cout
);

always @(posedge clk) begin
  aout <= b;
  bout <= c;
  cout <= a;
end

endmodule
```
### By Blocking (Using same variable)
```
`timescale 1ns/1ps
module blockingusingsamevar;
  reg clk;
  reg [3:0] a, b, c;
  initial clk = 0;
  always #5 clk = ~clk;
  initial begin
    a = 4'd8;
    b = 4'd7;
    c = 4'd6;
  end
  always @(posedge clk) begin
    a = b;
    b = c;
    c = a;
  end
endmodule
```
### By Non-Blocking (Using same variable)
```
`timescale 1ns/1ps
module nonblockingusingsamevar;
  reg clk;
  reg [3:0] a, b, c;
  initial clk = 0;
  always #5 clk = ~clk;
  initial begin
    a = 4'd8;
    b = 4'd7;
    c = 4'd6;
  end
  always @(posedge clk) begin
    a <= b;
    b <= c;
    c <= a;
  end
endmodule
```
Testbench for Swapping Three Numbers:

// swap_three_numbers_tb.v
```
`timescale 1ns / 1ps

module swap_three_numbers_tb;

    // Inputs
    reg [7:0] a;
    reg [7:0] b;
    reg [7:0] c;

    // Outputs
    wire [7:0] a_out;
    wire [7:0] b_out;
    wire [7:0] c_out;

    // Instantiate the Unit Under Test (UUT)
    swap_three_numbers uut (
        .a_in(a),
        .b_in(b),
        .c_in(c),
        .a_out(a_out),
        .b_out(b_out),
        .c_out(c_out)
    );

    // Test procedure
    initial begin
        // Initialize inputs
        a = 8'd10; // Assign 10 to a
        b = 8'd20; // Assign 20 to b
        c = 8'd30; // Assign 30 to c

        // Wait for 10 ns to observe swap
        #10;

        // Display results
        $display("Before Swap: a = %d, b = %d, c = %d", a, b, c);
        #10;
        $display("After Swap: a = %d, b = %d, c = %d", a_out, b_out, c_out);
        
        // Stop the simulation
        #10 $stop;
    end
endmodule
```
## OUTPUT
### By Blocking

![Screenshot 2025-04-19 142302](https://github.com/user-attachments/assets/0d145fc6-fa16-4026-8aac-344757a0d517)

### By Non-Blocking

![Screenshot 2025-04-19 141808](https://github.com/user-attachments/assets/710e8b80-12c4-4e9b-b9bf-9c8707fdcd65)

### By Blocking(Using same variable)

![Screenshot 2025-04-19 142716](https://github.com/user-attachments/assets/40dd6b6a-330c-416d-a48b-3c670cbc457f)

### By Non Blocking(Using same variable)

![file_2025-04-19_09 05 08](https://github.com/user-attachments/assets/8a77bb79-ca0d-4a39-a1ea-77de5e71ee91)

## Conclusion
In this experiment, a Verilog HDL code for swapping three numbers was designed and successfully simulated. The testbench verified the swapping operation, showing that the values of three input numbers (a, b, and c) were swapped correctly without the use of temporary variables. This experiment demonstrated the effectiveness of Verilog in implementing logical operations and control mechanisms such as swapping values. The simulation results confirm the correct functionality of the design.
