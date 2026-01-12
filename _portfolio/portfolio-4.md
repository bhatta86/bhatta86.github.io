---
title: "8-Bit Dual-Mode Ripple-Carry Adder (CMOS VLSI Design)"
excerpt: "A transistor-level static CMOS adder optimized for power and performance through logical effort–driven sizing and critical path analysis."
collection: portfolio
---

### 8-Bit Dual-Mode Ripple-Carry Adder: Transistor-Level CMOS Design

This project involved the full transistor-level design, simulation, and optimization of an 8-bit dual-mode ripple-carry adder implemented in static CMOS. The design supports both standard addition and accumulator modes, with an integrated reset path, and was developed entirely in Cadence Virtuoso with Spectre-based verification.

**Technical Context**: EECS 312 — Digital Integrated Circuits (IBM 65 nm PDK)

**Architecture + Design Choices**  
The adder is built from a custom 1-bit full-adder cell using an XNOR-based sum path and NAND/NOR-based carry logic rather than conventional XOR/AND structures. This topology was chosen to reduce logical effort, avoid deep NMOS stacks, and improve rise/fall symmetry along the critical carry-propagation path.

All primary inputs were constrained to pass through minimum-sized inverters, forcing performance improvements to come from internal logic optimization rather than brute-force drive strength.

**Methodology**
- Designed a complete 1-bit full-adder cell using static CMOS (XNOR, NAND, NOR, INV) and tiled it into an 8-bit ripple-carry architecture.
- Parameterized every transistor device to enable rapid iteration on sizing without rebuilding lower-level schematics.
- Identified the worst-case critical path (XNOR → NAND → NOR → MUX → register) through transient simulation and timing analysis.
- Developed two optimized variants:
  - **Power-optimized design** targeting 1 GHz operation by selectively upsizing only critical full-adder gates.
  - **Speed-optimized design** targeting multi-GHz operation by strengthening all gates along the carry path, including inverters and multiplexers.
- Built clocked testbenches with worst-case vectors to validate timing closure, functional correctness, accumulator behavior, and reset stability.
- Analyzed transient waveforms to study glitch behavior and non-monotonic carry settling in ripple-carry architectures.

**Performance**
- Power-optimized design achieved correct operation at **1 GHz** with minimal area growth and measured dynamic power of approximately **260 µW**.
- Speed-optimized design achieved stable operation at **2.0 GHz**, demonstrating correct carry propagation under worst-case conditions with acceptable area and power tradeoffs.
- Transient analysis revealed realistic carry-chain glitches that settled within the clock window, reinforcing timing margin robustness.

**Further Thoughts**
Future improvements include exploring carry-lookahead or prefix adder topologies for reduced latency, investigating keeper or glitch-reduction techniques, and performing layout-aware extraction to study parasitic effects on timing and power at higher frequencies.

