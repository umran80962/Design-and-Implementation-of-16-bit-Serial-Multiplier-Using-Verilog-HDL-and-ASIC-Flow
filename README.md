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
<img width="1140" height="503" alt="image" src="https://github.com/user-attachments/assets/ada252b5-dc73-41d9-8e45-6833b29c87db" />

5.2 Gate-Level Area Report
<img width="627" height="814" alt="Screenshot 2025-11-04 225653" src="https://github.com/user-attachments/assets/24ee4d69-8965-44de-b7a1-4d16ce577bfa" />

5.3 Power Report:
<img width="895" height="433" alt="image" src="https://github.com/user-attachments/assets/f1c574da-3531-4341-b69f-203473e95873" />

5.4 Timing Report:
<img width="979" height="287" alt="image" src="https://github.com/user-attachments/assets/6f95bbca-10fa-4957-a713-2d041af11a1a" />

6. Layout (Cadence Innovus)

Final routed chip layout was generated with no DRC or LVS violations.
(<img width="836" height="875" alt="image" src="https://github.com/user-attachments/assets/3a34b70b-e08d-43b1-89be-291c0c65c89b" />
)

7. Conclusion:
The 16-bit serial multiplier was successfully designed and verified using Verilog HDL. The design was synthesized and implemented in the ASIC flow, generating a clean layout with no DRC or LVS violations. The results confirm the area-efficient operation of the serial multiplier with correct functionality and acceptable timing performance. This work demonstrates the complete digital design flow from RTL to GDSII.

8. References:
1. Mohamed Asan Basiri M and Noor Mahammad, “Configurable folded IIR filter design”, IEEE Transactions on Circuits and Systems II, vol. 62, no. 12, pp. 1144–1148, 2015.
2.  A. Ahlander and Bertil Svensson, “Floating point calculations in bit-serial SIMD computers”, Fourth Swedish Workshop on Computer Systems Architecture, pp. 1–11, 1992.
3. Sadeghi, Mohsen, Mahya Zahedi, and Maaruf Ali, “The Cascade Carry Array Mul- tiplier – A Novel Structure of Digital Unsigned Multipliers for Low-Power Con- sumption and Ultra-Fast Applications”, AETiC, vol. 3, no. 3, pp. 19–27, 2019.
4. C. S. Wallace, “A suggestion for a fast multiplier”, IEEE Transactions on Electronic Computers, vol. EC-13, no. 1, pp. 14–17, Feb. 1964.
5. Carl Hamacher, Zvonko Vranesic, Safwat Zaky, and Naraig Manjikian, “Computer Organization and Embedded Systems”, McGraw Hill Publications, 6th Edition, 2002.
6. Mohamed Asan Basiri M and SK Noor Mahammad, “Memory based multiplier design in custom and FPGA implementation”, Advances in Intelligent Informatics, Springer, pp. 253–265, 2015.
7. Shuli Gao, Dhamin Al-Khalili, J. M. Pierre Langlois, and Noureddine Chabini, “Efficient Realization of BCD Multipliers Using FPGAs”, IJRC, vol. 2017, no. 2410408, pp. 1–12, 2017.
8. Parthibaraj Anguraj and Thiruvenkadam Krishnan, “Design and implementation of modified BCD digit multiplier for digit-by-digit decimal multiplier”, Analog In- tegrated Circuits and Signal Processing, Springer, vol. 107, pp. 683–694, 2021.
9. Guardia and Carlos Eduardo Minchola, “Implementation of a fully pipelined BCD multiplier in FPGA”, VIII Southern Conference on Programmable Logic, pp. 1–6, 2012.
10. Z. T. Sworna, M. U. I. Haque, and D. M. Anisuzzaman, “High-Speed and Area Efficient LUT-based BCD Multiplier Design”, IEEE WIECON-ECE, pp. 1–4, 2018.
11. https://www.realdigital.org/doc/6dae6583570fd816d1d675b93578203d
12. Mohamed Asan Basiri M, Samaresh Chandra Nayak, and Noor Mahammad, “Mul- tiplication acceleration through quarter precision Wallace tree multiplier”, IEEE SPIN Conference, pp. 502–505, Feb. 2014.
13. Sjalander M and Larsson-Edefors P, “High-Speed and Low-Power Multipliers Using the Baugh-Wooley Algorithm and HPM Reduction Tree”, IEEE ICECS, pp. 33–36, 2008.







(final product screenshot here)
