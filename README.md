# Design-and-Implementation-of-16-bit-Serial-Multiplier-Using-Verilog-HDL-and-ASIC-Flow
Design and Implementation of 16-bit Serial Multiplier Using Verilog HDL and ASIC Flow
# Design-and-Implementation-of-16-bit-Serial-Multiplier-Using-Verilog-HDL-and-ASIC-Flow

Design and Implementation of 16-bit Serial Multiplier Using Verilog HDL and ASIC Flow


## Overview
This project implements a 16-bit serial multiplier using a shift-and-add approach.  
It multiplies one bit per clock cycle, which helps reduce hardware cost compared to a full parallel multiplier.

The design is written in Verilog, tested in Vivado, and then taken through the ASIC flow using Cadence Genus and Innovus to generate GDSII.


## Features
- 16-bit serial multiplication
- Shift-and-add architecture
- RTL verified in Xilinx Vivado
- Synthesized and implemented in Cadence (Genus + Innovus)
- Final GDSII layout created


## How It Works
1. Read one multiplier bit per clock.
2. If the bit is 1, add shifted multiplicand to partial sum.
3. Shift and repeat for 16 cycles.
4. Output is a 32-bit product.


## Verilog Code

```verilog
module serial_multiplier16bit (
    input clk, rst,
    input [15:0] A, B,
    output reg [31:0] product
);

    reg [15:0] multiplicand, multiplier;
    reg [31:0] partial_sum;
    reg [4:0] count;

    always @(posedge clk or posedge rst) begin
        if(rst) begin
            multiplicand <= A;
            multiplier   <= B;
            partial_sum  <= 0;
            product      <= 0;
            count        <= 0;
        end
        else if(count < 16) begin
            if(multiplier[0] == 1'b1)
                partial_sum <= partial_sum + (multiplicand << count);

            multiplier <= multiplier >> 1;
            count <= count + 1;
        end
        else begin
            product <= partial_sum;
        end
    end

endmodule
module tb;
    reg clk = 0, rst = 1;
    reg [15:0] A = 16'd25, B = 16'd13;
    wire [31:0] product;

    serial_multiplier16bit dut(clk, rst, A, B, product);

    always #5 clk = ~clk;

    initial begin
        #10 rst = 0;
        #400 $display("Product = %d", product);
        $finish;
    end
endmodule
read_netlist netlist.v
floorplan
place_opt
cts
route_opt
write_gds chip.gds
/src       → Verilog files
/sim       → Testbench, waves
/netlist   → Genus output
/layout    → Innovus results (DEF, GDS)
