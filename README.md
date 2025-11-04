     16-bit Serial Multiplier using Verilog HDL and ASIC Flow

This project implements a 16×16 serial multiplier using the shift-and-add method. The design was written in Verilog, simulated in Vivado, and then taken through ASIC tools (Genus and Innovus) for synthesis and layout. The goal was to build a compact multiplier that trades speed for lower hardware cost.

Abstract

This work presents a 16-bit serial multiplier designed in Verilog HDL. It uses the shift-and-add approach, where one bit is processed per clock cycle. The design was functionally verified in Xilinx Vivado and then synthesized and placed-and-routed using Cadence Genus and Innovus. The final output was a clean GDSII layout ready for fabrication. The focus was area efficiency while keeping correct behavior and stable timing.

1. Introduction

Multiplication is a core arithmetic function in processors and DSP systems. Serial multipliers offer a compact hardware solution by handling one bit at a time, unlike parallel multipliers that use more hardware for speed.
This project develops a 16-bit serial multiplier and walks through RTL, simulation, synthesis, and physical design stages.

2. Design Methodology

Steps followed:

RTL coding and testbench design in Verilog

Simulation and waveform check in Vivado

Synthesis in Cadence Genus

Place-and-route in Cadence Innovus

GDSII export for chip fabrication

3. Working Principle

The multiplier performs 16-bit × 16-bit multiplication over 16 cycles using the shift-and-add method.

Inputs

Serial_multin1 → Multiplicand (A)

Serial_multin2 → Multiplier (B)

clk, rst

Output

Serial_multout → 32-bit product

Operation flow

A counter tracks which bit is being processed.

The multiplier bit is checked.

If bit = 1, the multiplicand is added to the partial sum.

Partial results are shifted and accumulated.

After 16 cycles, output holds the final 32-bit result.

4. Implementation and Results
4.1 RTL Block Diagram

(<img width="831" height="905" alt="Screenshot 2025-11-04 223038" src="https://github.com/user-attachments/assets/8f142d9e-3495-48da-976f-aeaf04884e87" />
)

4.2 Simulation Waveform

(<img width="940" height="655" alt="image" src="https://github.com/user-attachments/assets/b70ca1dd-f542-4fc4-b191-140917627931" />
)

4.3 Vivado Output

(<img width="933" height="622" alt="image" src="https://github.com/user-attachments/assets/3cced3e8-3a00-4ff1-a957-d7f7888007c8" />
)

5. Synthesis Results (Cadence Genus)
5.1 Summary

Module: Serial_multiplier16bit

Cell count: 351

Total area: ~2801 units (from standard cell library report)

5.2 Key Cells Used

Adders, AND gates, and AOI structures mainly used for accumulation logic

5.3 Power Report (Summary)

Total power ~1.96e-04 W

5.4 Timing Report

Setup slack met

Clean timing at target frequency

6. Layout (Cadence Innovus)

Final routed chip layout was generated with no DRC or LVS violations.
(layout image here)

7. Conclusion

The 16-bit serial multiplier was successfully built, verified, and implemented up to GDSII. It achieved area-efficient multiplication with correct timing and clean fabrication-ready layout. This shows the full flow from Verilog RTL to physical chip design.

8. References
