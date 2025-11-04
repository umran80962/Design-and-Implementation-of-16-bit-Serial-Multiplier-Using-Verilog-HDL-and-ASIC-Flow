4×4 Systolic Array Accelerator: RTL to GDSII

This project implements a 4×4 systolic array accelerator for matrix-multiplication, written in Verilog HDL and taken through a full ASIC flow (RTL → Simulation → Synthesis → Layout) using the open-source OpenLane flow and the SkyWater 130 nm PDK. It targets high-throughput hardware for CNN and scientific computing applications.

Abstract

We present a hardware accelerator that uses a 4×4 grid of MAC units (16 processing elements) arranged in a systolic fashion. The design is parameterised for scalability, and we demonstrate the full digital flow (RTL → testbench → synthesis → placement & routing → GDSII output). The goal is to show how a structured array with data-flow reuse can deliver high throughput with efficient use of hardware.

1. Introduction

Systolic arrays are a key architectural choice for matrix-multiplication, convolution engines, and ML accelerators. Instead of processing one multiply-accumulate (MAC) at a time, a 4×4 systolic array performs 16 MACs in parallel per cycle (after pipeline warm-up). This project builds such a 4×4 array, verifies it at RTL, and takes it through an ASIC flow with placement & routing and timing closure.

2. Design Methodology

The flow followed:

Write parameterised Verilog for MAC unit and systolic array topology

Develop a comprehensive testbench (multiple input/test cases) and simulate using Icarus Verilog + GTKWave

Perform logic synthesis using Yosys (via OpenLane) targeting the SkyWater 130 nm process

Floorplan, place & route, clock tree synthesis, timing-signoff using the OpenLane/OPENROAD flow

Generate GDSII layout ready for fabrication

3. Architecture
Design Hierarchy

Processing Element (PE): A MAC unit with acc += a × b, with valid/ready handshake

Array Top-Level: 4 rows × 4 columns of PEs

Dataflow

Matrix A data flows horizontally (left → right)

Matrix B data flows vertically (top → down)

Each PE accumulates partial sums locally

Pipeline

Initial latency to fill the array (~4-7 cycles)

Steady state: one output per cycle for each of the 16 results

Key Specifications
Parameter	Value
Array Size	4 × 4
Input Width	8 bits
Accumulator Width	32 bits
MACs per Cycle	16
Throughput	16 MAC operations / clock (steady state)
4. Implementation & Results
4.1 RTL Block Diagram

(insert block-diagram image here)

4.2 Simulation Waveforms

(insert waveform screenshot here)

4.3 Synthesis & Layout

Target technology: SkyWater 130 nm

Post-route area, timing, power metrics:

Total area ~ 2810.20 µm²

Maximum operating frequency ~ 176 MHz (typical corner)

Total power ~ 1.37 mW (post-layout)
These numbers demonstrate timing closure and realistic hardware metrics for a 4×4 systolic array.

5. Getting Started
Prerequisites

Icarus Verilog (for RTL simulation)

GTKWave (waveform viewer)

OpenLane / OpenROAD (ASIC flow)

SkyWater 130 nm PDK

Running the Flow
# Clone the repo
git clone https://github.com/Vedevil/Systolic-MAC-Array-for-CNN-Acceleration.git
cd Systolic-MAC-Array-for-CNN-Acceleration

# RTL Simulation
cd tb
iverilog -o tb.out ../rtl/mac_pe.v ../rtl/systolic_top.v tb_systolic.v
vvp tb.out
gtkwave tb_systolic_4x4.vcd

# ASIC Flow (via OpenLane)
cd openlane
make mount
./flow.tcl -design systolic_array

6. Technical Specifications

Parameterised architecture supports larger sizes (e.g., 8×8, 16×16)

Handshake protocol (valid/ready) avoids deadlock and ensures back-pressure handling

Full verification: identity matrices, zero matrices, max-value matrices, random matrices

Overflow protection: 32-bit accumulator handles 8-bit inputs without overflow

7. Future Enhancements

Extend to larger array sizes (8×8, 16×16)

Move to more advanced process nodes (28 nm, 14 nm)

Introduce clock gating for power savings in unused elements

Pipeline the MAC operations further to boost clock speed

Enhance memory interface (AXI-Stream) or support mixed-precision arithmetic (INT4/INT8/FP16)

8. Contributing

Contributions are welcome. If you’d like to contribute:

Fork the repository

Create a feature branch (e.g., git checkout -b feature/enhancement)

Commit your changes with descriptive message

Push to your fork and open a Pull Request

9. License

This project is released under the MIT License
. You’re free to use, modify, and distribute the work under its terms
