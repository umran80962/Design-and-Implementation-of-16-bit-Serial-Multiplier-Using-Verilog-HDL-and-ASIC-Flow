<h1><b>16-bit Serial Multiplier using Verilog HDL and ASIC Flow</b></h1>

This project implements a 16×16 serial multiplier using the shift-and-add method. The design was written in Verilog, simulated in Vivado, and then taken through ASIC tools (Genus and Innovus) for synthesis and layout. The goal was to build a compact multiplier that trades speed for lower hardware cost.

<h2><b>Abstract</b></h2>

This work presents a 16-bit serial multiplier designed in Verilog HDL. It uses the shift-and-add approach, where one bit is processed per clock cycle. The design was functionally verified in Xilinx Vivado and then synthesized and placed-and-routed using Cadence Genus and Innovus. The final output was a clean GDSII layout ready for fabrication. The focus was area efficiency while keeping correct behavior and stable timing.

<h2><b>Introduction</b></h2>

Multiplication is a core arithmetic function in processors and DSP systems. Serial multipliers offer a compact hardware solution by handling one bit at a time, unlike parallel multipliers that use more hardware for speed. This project develops a 16-bit serial multiplier and walks through RTL, simulation, synthesis, and physical design stages.

<h2><b>Design Methodology</b></h2>

Steps followed:

- RTL coding and testbench design in Verilog  
- Simulation and waveform check in Vivado  
- Synthesis in Cadence Genus  
- Place-and-route in Cadence Innovus  
- GDSII export for chip fabrication  

<h2><b>Working Principle</b></h2>

The multiplier performs 16-bit × 16-bit multiplication over 16 cycles using the shift-and-add method.

<h3><b>Inputs</b></h3>

- Serial_multin1 → Multiplicand (A)  
- Serial_multin2 → Multiplier (B)  
- clk, rst  

<h3><b>Output</b></h3>

- Serial_multout → 32-bit product  

<h3><b>Operation flow</b></h3>

1. A counter tracks which bit is being processed.  
2. The multiplier bit is checked.  
3. If bit = 1, the multiplicand is added to the partial sum.  
4. Partial results are shifted and accumulated.  
5. After 16 cycles, output holds the final 32-bit result.  

<h2><b>Implementation and Results</b></h2>

<h3><b>4.1 RTL Block Diagram</b></h3>
(<img width="831" height="905" alt="Screenshot 2025-11-04 223038" src="https://github.com/user-attachments/assets/f8bd614d-34ae-4416-8087-8a126b6df41c" />
)

<h3><b>4.2 Simulation Waveform</b></h3>
(<img width="940" height="655" alt="Screenshot 2025-11-04 223436" src="https://github.com/user-attachments/assets/a90e117a-6a72-4ab6-a4bd-403acd2b1b91" />
)

<h3><b>4.3 Vivado Output</b></h3>
(<img width="933" height="622" alt="Screenshot 2025-11-04 223535" src="https://github.com/user-attachments/assets/02523a48-c86d-4870-a48e-6fbf426ecc30" />
)

<h2><b>Netlist Generation and Analysis</b></h2>

After verification, synthesis was carried out using Cadence Genus tool. The generated netlist and report are summarized below.  
(<img width="875" height="640" alt="Screenshot 2025-11-04 223617" src="https://github.com/user-attachments/assets/8dfc4baf-e51e-4db9-945d-4df99974644b" />
)

<h3><b>5.1 Synthesis Report Summary</b></h3>
(<img width="1140" height="503" alt="Screenshot 2025-11-04 225453" src="https://github.com/user-attachments/assets/35e7d027-c561-4ac3-8588-9b30ade26705" />
)

<h3><b>5.2 Gate-Level Area Report</b></h3>
(<img width="627" height="814" alt="Screenshot 2025-11-04 225653" src="https://github.com/user-attachments/assets/77b95631-4cf8-48fd-a092-5809cceb26a0" />
)

<h3><b>5.3 Power Report</b></h3>
(<img width="895" height="433" alt="Screenshot 2025-11-04 225916" src="https://github.com/user-attachments/assets/343883f2-3647-4052-9193-095a5a2ba9e6" />
)

<h3><b>5.4 Timing Report</b></h3>
(<img width="979" height="287" alt="Screenshot 2025-11-04 225948" src="https://github.com/user-attachments/assets/085d95c4-7269-4c0b-a214-fdf17d4f159d" />
)

<h2><b>Layout (Cadence Innovus)</b></h2>

Final routed chip layout was generated with no DRC or LVS violations.  
<img width="836" height="875" alt="Screenshot 2025-11-04 230113" src="https://github.com/user-attachments/assets/59a027f9-15e8-485c-989e-bc15c55f86c5" />



<h2><b>Conclusion</b></h2>

The 16-bit serial multiplier was successfully designed and verified using Verilog HDL. The design was synthesized and implemented in the ASIC flow, generating a clean layout with no DRC or LVS violations. The results confirm the area-efficient operation of the serial multiplier with correct functionality and acceptable timing performance. This work demonstrates the complete digital design flow from RTL to GDSII.

<h2><b>References</b></h2>

(List of references same as provided)
