# 32-bit MIPS Pipelined Processor

This project implements a 32-bit MIPS pipelined processor in Verilog. It consists of multiple stages of the pipeline and handles basic ALU operations, memory load/store, and branching.

## Features
- **5-stage pipeline** (Instruction Fetch, Instruction Decode, Execute, Memory, Write-back)
- Support for:
  - ALU operations (ADD, SUB, MUL, AND, OR, SLT)
  - Load/Store instructions (LW, SW)
  - Immediate operations (ADDI, SUBI, SLTI)
  - Branching (BEQZ, BNEQZ)
  - Halt instruction (HLT)

## File Structure
- **MIPS32.v**: The main module implementing the pipelined MIPS processor.
- **test_mips32.v**: Testbench to simulate the processor. It initializes the registers and memory, runs a program, and prints the result.
- **mips.vcd**: The generated waveform file to visualize the pipeline behavior using a waveform viewer like GTKWave.
- **Verilog Simulator**: To simulate the Verilog code (e.g., Icarus Verilog).

## Instructions
- **Memory:** The memory is 1024 x 32 bits. The program and data are preloaded into the memory in the testbench.
- **Registers:** There are 32 general-purpose registers, initialized in the testbench.
- **Clock Phases:** The processor uses a two-phase clock, generated in the testbench.
  
## Sample Program
In the provided testbench (test2_mips32.v), the following MIPS assembly instructions are pre-loaded into memory:
1. **Assembly:**
   ```bash
   ADDI R1, R0, 120    // Load the value 120 into register R1
   LW   R2, 0(R1)      // Load the value at memory address 120 into register R2
   ADDI R2, R2, 45     // Add 45 to R2
   SW   R2, 1(R1)      // Store the result in memory address 121
   HLT                 // Halt the processor

- The value 85 is stored in memory at location 120. After the program runs, the value at memory location 121 will be updated to 130 (85 + 45).
less
2. **Output:**
  ```bash
  Mem[120]:   85
  Mem[121]:  130

