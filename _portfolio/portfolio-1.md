---
title: "16-Bit RISC Processor with 4×4 Systolic Array Accelerator"
excerpt: "A custom ASIC implementing a pipelined 16-bit RISC processor integrated with a systolic-array accelerator, designed through a complete RTL-to-GDSII flow using Verilog, Cadence Virtuoso, Synopsys Design Compiler, and Cadence Innovus."
collection: portfolio
---

**Paper:** [View Full Project Report](/files/paper4.pdf)

### 16-Bit RISC Processor with 4×4 Systolic Array Accelerator

This project involved the architectural design, RTL development, custom VLSI implementation, and physical design of a 16-bit RISC processor enhanced with a dedicated 4×4 systolic-array accelerator for matrix multiplication workloads. The system was developed through a complete ASIC design flow spanning custom transistor-level layout, digital synthesis, place-and-route, and post-layout analysis.

The goal of the project was to explore hardware acceleration for matrix operations while gaining experience with both full-custom and standard-cell VLSI methodologies within a unified processor system.

**Technical Context**: EECS 427 — VLSI Design I (TSMC 65 nm Technology)

### Architecture Overview

The baseline processor consists of a 2-stage pipelined 16-bit RISC architecture containing:

- Program Counter (PC)
- Instruction Decoder
- Control Unit
- Register File
- Arithmetic Logic Unit (ALU)
- Logarithmic Shifter
- Data Memory Interface

To accelerate matrix multiplication, a dedicated 4×4 systolic-array accelerator was integrated directly into the processor datapath. Custom ISA instructions were added to allow software-controlled invocation of accelerator operations without requiring external hardware control.

The final architecture formed a tightly-coupled compute system in which the processor, memory subsystem, and accelerator shared data through a unified datapath and SRAM interface.

### Systolic Array Accelerator

The accelerator consists of sixteen processing elements arranged in a 4×4 mesh. Each processing element performs signed multiply-accumulate (MAC) operations while propagating operands to neighboring cells according to systolic dataflow principles.

Key architectural features included:

- Signed 4-bit multiply-accumulate arithmetic
- Local north-west operand propagation between processing elements
- Shift-register based operand staggering to create diagonal data movement
- Parallel execution of matrix multiplication workloads
- Integrated result collection and writeback into the processor datapath

By exploiting hardware parallelism, the systolic architecture dramatically reduced execution time compared to sequential processor-based matrix multiplication.

### RTL Design and Processor Integration

A significant portion of the project focused on integrating the accelerator into the existing processor architecture.

This required:

- Developing Verilog RTL for accelerator control and datapath integration
- Extending the processor ISA with custom accelerator instructions
- Designing FSM-based control logic to coordinate processor and accelerator execution
- Implementing program counter stalling during multi-cycle accelerator operations
- Integrating memory interfaces between the accelerator and processor register file
- Managing data movement through a shared SRAM-based storage architecture

The resulting design allowed software running on the processor to transparently invoke accelerator operations through custom instructions while maintaining correct processor execution flow.

### Memory System

A dual-port 16×16 SRAM was incorporated into the architecture to support efficient communication between the processor and accelerator.

The memory subsystem enabled:

- Simultaneous read and write operations
- Data buffering between matrix computation stages
- Circular data movement through the accelerator datapath
- Reduced processor overhead during matrix execution

### Custom VLSI Design

Several processor blocks were implemented using full-custom VLSI techniques in Cadence Virtuoso.

Custom layouts were created for:

- Register File
- Arithmetic Logic Unit (ALU)
- Logarithmic Shifter

The design process included:

- Schematic capture
- Transistor-level CMOS implementation
- Layout generation
- DRC verification
- LVS verification
- Physical optimization for area and routability

This portion of the project provided direct exposure to transistor-level design and physical layout methodologies commonly used in ASIC development.

### Digital ASIC Flow

In addition to full-custom blocks, the processor controller and program counter were implemented using a standard-cell design methodology.

The digital implementation flow included:

- Verilog RTL development
- Logic synthesis using Synopsys Design Compiler
- Scan-chain insertion for design-for-testability
- Floorplanning and placement
- Clock-tree synthesis
- Routing and optimization
- Post-layout timing analysis

Cadence Innovus was used to perform place-and-route and generate the final physical implementation of synthesized digital logic.

### Verification and Validation

Verification occurred throughout multiple levels of abstraction.

Verification activities included:

- RTL simulation of processor execution
- Functional validation of custom ISA instructions
- Datapath verification
- Accelerator correctness testing
- SRAM integration validation
- DRC/LVS verification of custom layouts
- Post-layout timing evaluation

### Performance

The completed architecture demonstrated substantial performance gains over the baseline processor implementation.

Key results included:

- Approximately **8× speedup** for matrix multiplication workloads
- Successful integration of processor and accelerator execution
- Correct operation across RTL, synthesized, and physical design stages
- Completion of a full RTL-to-GDSII ASIC implementation flow

The project highlighted how domain-specific hardware acceleration can dramatically improve performance while exposing the tradeoffs between architectural complexity, area, timing, and power.

### Further Thoughts

Future iterations of the design could significantly improve performance and scalability by incorporating:

- Larger systolic-array dimensions (8×8 or 16×16)
- Wider datapaths and operands
- DMA-based memory transfers
- Cache integration
- More advanced pipeline architectures
- RISC-V compatibility
- Tensor-oriented instruction extensions
- Physical design optimization targeting higher clock frequencies

This project provided end-to-end experience across computer architecture, RTL design, custom VLSI layout, ASIC implementation, verification, and hardware acceleration—closely mirroring many of the workflows used in modern processor and accelerator development.
