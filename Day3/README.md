# Day 3 – RTL Optimization and Synthesis

## Overview

Day 3 focuses on understanding how synthesis tools optimize an RTL design and convert it into an efficient gate-level implementation.

The experiments performed in this session cover basic logic optimization, constant propagation in D flip-flops, sequential logic optimization, and counter optimization.

The designs were synthesized using Yosys and the synthesized results were examined to understand how RTL descriptions are transformed into hardware.

---

## Table of Contents

- [Objective](#objective)
- [1. RTL Optimization](#1-rtl-optimization)
- [2. Logic Optimization](#2-logic-optimization)
  - [AND Logic](#and-logic)
  - [OR Logic](#or-logic)
  - [Three-Input AND Logic](#three-input-and-logic)
- [3. Constant Propagation](#3-constant-propagation)
- [4. D Flip-Flop Optimization](#4-d-flip-flop-optimization)
  - [DFF Constant 1](#dff-constant-1)
  - [DFF Constant 2](#dff-constant-2)
  - [DFF Constant 3](#dff-constant-3)
- [5. Counter Optimization](#5-counter-optimization)
- [6. Importance of Optimization](#6-importance-of-optimization)
- [Key Observations](#key-observations)
- [Conclusion](#conclusion)

---

## Objective

The main objectives of this session are:

- To understand the purpose of RTL optimization during synthesis.
- To understand how synthesis tools simplify digital logic.
- To observe how Boolean expressions are mapped into hardware cells.
- To study constant propagation in combinational and sequential circuits.
- To understand how redundant or unnecessary hardware can be eliminated.
- To examine synthesized gate-level representations.
- To study optimization in sequential circuits such as counters.
- To verify sequential circuits using simulation waveforms.

---

# 1. RTL Optimization

RTL optimization is the process of improving the hardware implementation of an RTL design without changing its intended functionality.

An RTL description specifies what the circuit should do, but several different hardware structures can implement the same function. The synthesis tool analyzes the RTL and selects an appropriate implementation based on the target technology and available standard-cell library.

During optimization, the synthesis tool can perform operations such as:

- Boolean simplification
- Constant propagation
- Removal of redundant logic
- Removal of unused signals
- Logic restructuring
- Technology mapping
- Sequential optimization

The objective is to obtain an implementation that performs the required function with efficient use of hardware resources.

Optimization can have a direct effect on important physical design parameters such as:

- Area
- Power consumption
- Timing
- Number of standard cells
- Switching activity

Therefore, RTL optimization is an important step between RTL design and physical implementation.

---

# 2. Logic Optimization

Logic optimization deals with simplifying combinational logic while preserving its logical behavior.

For example, a Boolean expression may contain constants or redundant terms that can be simplified before being implemented as hardware.

Some basic Boolean identities used during optimization are:

A AND 1 = A

A AND 0 = 0

A OR 0 = A

A OR 1 = 1

These identities allow synthesis tools to simplify logic.

The synthesis tool also maps the optimized logic into cells available in the selected technology library.

The following experiments demonstrate the synthesis of simple combinational logic.

---

## AND Logic

The first experiment deals with a basic AND operation.

An AND gate produces a logic HIGH at its output only when all of its inputs are HIGH.

For a two-input AND gate:

Y = A · B

The truth table is:

| A | B | Y |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

The RTL description is synthesized and mapped to the appropriate logic cell available in the target technology library.

### Synthesized Result

![AND Logic Optimization](images/opt_check.png)

The synthesized representation shows the hardware implementation obtained from the RTL description.

This demonstrates that a simple RTL Boolean expression can be represented by a corresponding standard cell after synthesis.

---

## OR Logic

The second experiment deals with an OR operation.

An OR gate produces a logic HIGH when at least one of its inputs is HIGH.

For a two-input OR gate:

Y = A + B

The truth table is:

| A | B | Y |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

During synthesis, the Boolean function is analyzed and mapped to the corresponding hardware cell.

### Synthesized Result

![OR Logic Optimization](images/opt_check2.png)

The result demonstrates how the RTL Boolean operation is represented at the synthesized level.

---

## Three-Input AND Logic

The third experiment uses three inputs for an AND operation.

The Boolean expression is:

Y = A · B · C

The output becomes HIGH only when all three inputs are HIGH.

The truth table is:

| A | B | C | Y |
|---|---|---|---|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 0 |
| 1 | 1 | 1 | 1 |

The synthesis tool identifies the required logic function and maps it to a suitable implementation from the target library.

### Synthesized Result

![Three Input AND Optimization](images/opt_check3.png)

This experiment shows how a multi-input Boolean operation is represented after synthesis.

---

# 3. Constant Propagation

Constant propagation is an optimization technique in which known constant values are propagated through the logic of a design.

If a signal is permanently known to be 0 or 1, the synthesis tool can use that information to simplify connected logic.

For example:

A AND 0 = 0

A AND 1 = A

A OR 0 = A

A OR 1 = 1

Therefore, if one input of an AND gate is permanently connected to 0, the gate does not need to perform an actual AND operation because its output will always be 0.

Similarly, if one input of an OR gate is permanently connected to 1, its output will always be 1.

Constant propagation is not limited to combinational logic. It can also be applied to sequential circuits when the synthesis tool can determine that the stored value is fixed.

This can reduce the amount of hardware required in the final implementation.

---

# 4. D Flip-Flop Optimization

The next set of experiments focuses on sequential logic.

A D flip-flop is a basic storage element used in synchronous digital circuits.

The D input represents the data to be stored, while the clock controls when the data is transferred to the output.

In a simplified positive-edge-triggered D flip-flop:

Q(next) = D

at the active clock edge.

If the D input is permanently connected to a constant value, the synthesis tool can determine the behavior of the flip-flop.

For example:

D = 0

means that after the appropriate clock operation, the stored value will be 0.

Similarly:

D = 1

means that the stored value will become 1.

This known information can be used by the synthesis tool to optimize the sequential circuit.

---

## DFF Constant 1

The first experiment investigates a D flip-flop with a constant input.

### Synthesized Circuit

![DFF Constant 1](images/dff_const1_diag.png)

### Simulation Waveform

![DFF Constant 1 Waveform](images/dff_const1.png)

The synthesized diagram shows the resulting sequential structure after synthesis.

This experiment demonstrates how a constant signal can be connected to the data input of a storage element.

---

## DFF Constant 2

The second experiment further examines the effect of a constant value on the D flip-flop.

When the synthesis tool identifies that a signal does not change, it can propagate that constant value through the surrounding logic.

### Synthesized Circuit

![DFF Constant 2](images/dff_const2_diag.png)

### Simulation Waveform

![DFF Constant 2 Waveform](images/dff_const2.png)

The waveform is used to observe the behavior of the sequential circuit with respect to the clock and output signals.

The simulation provides a functional check of the synthesized design.

---

## DFF Constant 3

The third experiment continues the study of constant propagation and sequential optimization.

At this stage, the effect of constant information on the synthesized sequential structure can be observed more clearly.

### Synthesized Circuit

![DFF Constant 3](images/dff_const3_diag.png)

### Simulation Waveform

![DFF Constant 3 Waveform](images/dff_const3.png)

The waveform helps verify that the optimized circuit continues to produce the expected behavior.

The experiment demonstrates the importance of checking both the synthesized structure and the functional simulation.

---

# 5. Counter Optimization

A counter is a sequential circuit that progresses through a predefined sequence of states.

A binary counter generally consists of multiple flip-flops along with combinational logic that determines the next state.

For an N-bit binary counter, the number of possible states is:

2^N

For example, a 3-bit counter can represent:

000 → 001 → 010 → 011 → 100 → 101 → 110 → 111

and then return to:

000

Counters are useful examples for studying sequential optimization because they contain both storage elements and next-state logic.

During synthesis, the tool analyzes the counter structure and determines an efficient implementation based on the required functionality.

### Original Counter

![Counter Optimization](images/counter_opt.png)

The synthesized representation shows the hardware generated for the counter design.

### Modified Counter

![Modified Counter Optimization](images/counter_opt_modified.png)

The modified version provides a comparison of the synthesized implementation after changes were made to the design.

The comparison helps demonstrate that even a small change in RTL can influence the resulting hardware structure.

---

# 6. Importance of Optimization

Optimization is important because the synthesized circuit directly affects the physical characteristics of the final chip.

### Area

Removing unnecessary logic reduces the number of standard cells required.

A smaller circuit can reduce the silicon area occupied by the design.

### Power

Every switching circuit consumes dynamic power.

Reducing unnecessary logic and switching activity can help reduce power consumption.

### Timing

The number and type of logic cells along a signal path affect propagation delay.

Optimization can help produce shorter or more efficient critical paths.

### Hardware Efficiency

Optimization allows the same functionality to be implemented using fewer or more suitable hardware resources.

Therefore, optimization is an important part of achieving a practical VLSI implementation.

---

# Key Observations

The experiments performed during Day 3 demonstrate the following:

1. RTL Boolean expressions can be converted into corresponding hardware cells during synthesis.
2. Different Boolean functions produce different synthesized structures.
3. Boolean identities can be used to simplify combinational logic.
4. Constant values can be propagated through sequential logic.
5. Synthesis can simplify unnecessary portions of a design.
6. The synthesized circuit can have a different structure from the original RTL while maintaining the required functionality.
7. Sequential circuits require special consideration because their behavior depends on stored state and clock events.
8. Counter designs contain both storage elements and combinational next-state logic.
9. Simulation waveforms are useful for verifying optimized sequential designs.
10. Optimization can influence area, power, timing, and overall hardware efficiency.

---

# Conclusion

Day 3 provided practical experience with RTL optimization and synthesis.

The combinational logic experiments demonstrated how basic Boolean operations are mapped into hardware. The constant propagation experiments showed how known values can be used to simplify logic, while the D flip-flop experiments demonstrated the application of optimization techniques to sequential circuits.

The counter experiment further demonstrated optimization in a larger sequential design containing storage elements and next-state logic.

These experiments helped demonstrate that synthesis is not simply a direct conversion of RTL into gates. The synthesis tool analyzes the design, applies optimization techniques, and produces an efficient hardware representation while maintaining the intended functionality.
