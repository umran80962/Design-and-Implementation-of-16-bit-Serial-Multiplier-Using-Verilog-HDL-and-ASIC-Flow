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

(<img width="831" height="905" alt="Screenshot 2025-11-04 223038" src="https://github.com/user-attachments/assets/4b627349-58cf-4ea0-8e55-0c023ba41ca0" />
)

4.2 Simulation Waveform

(<img width="940" height="655" alt="Screenshot 2025-11-04 223436" src="https://github.com/user-attachments/assets/15085433-cdeb-4ca9-be8b-6389048e3296" />
)

4.3 Vivado Output

(<img width="933" height="622" alt="Screenshot 2025-11-04 223535" src="https://github.com/user-attachments/assets/1ed75b7c-7ecd-49c6-a745-f0dab58ea4b5" />
)

5. Netlist Generation and Analysis:
After verification, synthesis was carried out using Cadence Genus tool. The generated netlist and report are summarized below.
<img width="875" height="640" alt="Screenshot 2025-11-04 223617" src="https://github.com/user-attachments/assets/36f2e2ff-f37f-4a79-bbff-6638914e180f" />
)

5.1 Synthesis Report Summary:
(<img width="1140" height="503" alt="image" src="https://github.com/user-attachments/assets/ada252b5-dc73-41d9-8e45-6833b29c87db" />
)

Module: Serial_multiplier16bit

Cell count: 351

Total area: ~2801 units (from standard cell library report)











(final product screenshot here)
