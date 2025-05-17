# single-port-ram-verilog
Verilog implementation of a single-port RAM with waveform verification

## Overview
This project implements a **Single-Port RAM** using Verilog. The RAM allows both read and write operations through a single port controlled by a write-enable signal. It is a synchronous memory block commonly used in FPGA and ASIC designs.

## Features
- Memory size: 16 locations (4-bit address width)
- Data width: 8 bits
- Single clock synchronous read and write
- Write enable control for switching between read and write modes

## Ports Description

| Signal | Direction | Description                    |
|--------|-----------|-------------------------------|
| clk    | Input     | Clock signal                  |
| we     | Input     | Write enable (1 = write, 0 = read) |
| addr   | Input     | 4-bit address input           |
| din    | Input     | 8-bit data input for writing |
| dout   | Output    | 8-bit data output for reading|

## Files Included
- `single_port_ram.v` — Verilog implementation of the RAM module
- `testbench.v` — Testbench to verify the functionality of the RAM module

## Usage
1. Load the Verilog files into your preferred simulator or FPGA development environment.
2. Run the testbench to simulate and verify the RAM’s behavior.
3. Observe the waveform to ensure correct read/write operations.

## Applications
- Embedded system memory blocks
- Register files in processors
- Cache memory and buffers

## Author
Pavani Chepalle

Feel free to modify or expand the project as needed!




