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
