16-Bit Serial Multiplier Using Verilog HDL and ASIC Flow

This project builds a 16-bit serial multiplier using the shift-and-add technique. The design is written in Verilog, verified in Vivado, and taken through a full ASIC flow using Cadence Genus and Innovus. The goal is simple: multiply two 16-bit numbers while keeping hardware usage low by processing one bit per clock cycle.

📌 Overview

A serial multiplier trades speed for area. Instead of generating all partial products at once, it handles one bit each cycle. This makes it useful in low-power, area-constrained systems such as embedded DSP blocks and microcontrollers.

This design completes a full RTL-to-GDSII pipeline:

RTL design in Verilog

Functional simulation in Vivado

Synthesis in Cadence Genus

Place & route in Cadence Innovus

Layout export to GDSII for fabrication readiness

🧠 Working Principle

The multiplier uses the classic shift-and-add approach.

Inputs

A — 16-bit multiplicand (serial input)

B — 16-bit multiplier (serial input)

clk, rst

Output

product — 32-bit result (serial output)

How it works

A counter tracks the current bit position.

The least significant bit of the multiplier is checked.

If that bit is 1, the multiplicand is added to the partial sum.

Partial sum is shifted based on bit position.

After 16 cycles, the full 32-bit product is ready.

Simple idea: one bit each cycle, 16 cycles total.

🛠️ Tools Used
Stage	Tool
RTL Design	Verilog HDL
Simulation	Xilinx Vivado
Synthesis	Cadence Genus
Place & Route	Cadence Innovus
Output	GDSII
