# Day 2 – Standard Cell Library, PVT Characterization, Synthesis Strategies & Flip-Flops

This document covers standard cell libraries and PVT corners, hierarchical vs. flattened synthesis, submodule-level synthesis, and the role of flip-flops in eliminating glitches from combinational logic.

---

## Table of Contents

- [Standard Cell Library and PVT Characterization](#standard-cell-library-and-pvt-characterization)
- [Hierarchical Synthesis](#hierarchical-synthesis)
- [Flattening the Design](#flattening-the-design)
- [Submodule-Level Synthesis](#submodule-level-synthesis)
- [Flip-Flops and Their Role in Digital Circuits](#flip-flops-and-their-role-in-digital-circuits)
- [Glitches in Combinational Logic](#glitches-in-combinational-logic)
- [Module Hierarchy](#module-hierarchy)
- [Key Takeaways](#key-takeaways)

---

## Standard Cell Library and PVT Characterization

During logic synthesis, an RTL design cannot be directly converted into hardware without a **technology library**. A Standard Cell Library provides a collection of pre-designed, pre-characterized logic cells — gates, multiplexers, flip-flops, buffers — that serve as the fundamental building blocks for digital circuit implementation. Along with each cell's functional description, the library includes **timing, power, area, and drive-strength** information, enabling the synthesis tool to map the RTL design into an optimized gate-level netlist.

### Reading the Library Filename

The workshop used `sky130_fd_sc_hd__tt_025C_1v80.lib`. Each part of the filename represents a specific characterization condition:

| Field | Meaning |
|---|---|
| `tt` | **Typical-Typical** corner — nominal manufacturing conditions for both NMOS and PMOS transistors |
| `025C` | Characterized at an operating temperature of **25°C** |
| `1v80` | Characterized at a supply voltage of **1.80 V** |

### PVT Corners

These conditions are collectively known as **PVT (Process, Voltage, Temperature) corners**. Transistor behavior changes due to:

- **Process** — fabrication variations
- **Voltage** — supply voltage fluctuations
- **Temperature** — operating temperature changes

Because of this, the same digital circuit can exhibit different timing characteristics under different conditions. By using a library characterized for a specific PVT corner, synthesis and timing tools can estimate design performance more accurately and generate hardware that operates reliably across the intended operating range.

---

## Hierarchical Synthesis

A top-level module often consists of multiple submodules, each implementing specific functionality. In **hierarchical synthesis**, the synthesis tool preserves this module hierarchy while synthesizing the design — each submodule is synthesized independently, and the final netlist retains the same hierarchical structure as the original RTL.

**Benefits:**
- Easier to understand and debug
- Easier to reuse individual modules
- Well suited for large, complex projects

---

## Flattening the Design

The `flatten` command removes hierarchical boundaries between modules. Instead of keeping separate top and submodules, the synthesis tool merges all instantiated modules into a **single unified module**.

| Aspect | Effect of Flattening |
|---|---|
| Cross-module optimization | Enabled — can improve area, timing, and logic optimization |
| Module hierarchy | Lost |
| Netlist readability | Reduced — harder to interpret and debug |

### Commands Used

```bash
synth -top multiple_modules
write_verilog multiple_modules_hier.v

flatten

write_verilog multiple_modules_flat.v
```

- `multiple_modules_hier.v` → **Hierarchical** gate-level netlist
- `multiple_modules_flat.v` → **Flattened** gate-level netlist
---

## Submodule-Level Synthesis

Instead of synthesizing the complete design, an individual submodule can be synthesized **independently**. This allows designers to analyze the area, timing, and logic implementation of a particular module before integrating it into the top-level design.

**Useful for:**
- Debugging a specific block in isolation
- Verifying a submodule's implementation
- Understanding reusable design blocks before full integration

---

## Flip-Flops and Their Role in Digital Circuits

A **flip-flop** is a sequential storage element capable of storing a single bit of information. Unlike combinational logic — whose output changes immediately with input changes — a flip-flop updates its output only when a triggering event, typically a **clock edge**, occurs. This controlled behavior makes flip-flops essential in synchronous digital systems.

## Glitches in Combinational Logic

### How Glitches Occur

Consider a circuit built from **cascaded AND gates**, where the output of the first gate feeds into a second gate. Although the logic expression suggests the output should change instantaneously with the inputs, real hardware behaves differently:

- Every logic gate introduces a finite **propagation delay** — the time required for a signal to travel from input to output.
- Intermediate signals therefore reach subsequent gates at **different times**.
- This causes temporary, unintended output transitions before the circuit finally settles to its correct value.

These temporary transitions are called **glitches**. They occur because different signal paths have different propagation delays, letting the output momentarily assume an incorrect logic value even though the final steady-state output is correct.

In small circuits glitches may seem insignificant, but in complex digital systems they can cause **incorrect operation** if captured by downstream logic.

### How Flip-Flops Prevent Glitch Propagation

To stop unwanted transitions from propagating through a design, flip-flops are inserted between combinational logic blocks:

- A flip-flop samples its input **only at the active clock edge**.
- It holds that value constant until the next clock event.
- Since the output changes only at well-defined clock instants, glitches occurring within the combinational logic are **not propagated** to the next stage — provided the signals stabilize before the clock edge.

This approach improves the **reliability, predictability, and synchronization** of digital circuits.

---
## Module Hierarchy

The design is composed of multiple modules, where the top module instantiates lower-level submodules. This hierarchical organization improves readability, modularity, and code reuse.

The figure shows the hierarchical structure of the `multiple_modules` design. The top-level module instantiates `sub_module1` and `sub_module2`, which communicate through the intermediate signal `net1`. This demonstrates how a complex design can be divided into smaller, reusable modules while maintaining a clear hierarchical organization.

---

## Key Takeaways

- A standard cell library provides timing, power, area, and drive-strength data for every gate, enabling accurate RTL-to-gate mapping.
- The library filename encodes its PVT corner — e.g., `tt_025C_1v80` means Typical-Typical process, 25°C, 1.80 V.
- PVT corners exist because process variation, voltage fluctuation, and temperature all affect timing — synthesis must target the corner(s) relevant to the design's operating conditions.
- Hierarchical synthesis preserves module structure, aiding debug and reuse; flattening merges everything into one module, trading readability for potential cross-module optimization.
- Submodule-level synthesis lets a single block be analyzed for area/timing before full integration.
- Flip-flops sample inputs only at clock edges, blocking glitches generated by unequal propagation delays in combinational logic from propagating downstream.
- Separating combinational logic with flip-flops gives each block a full clock period to settle, simplifying timing analysis in synchronous design.