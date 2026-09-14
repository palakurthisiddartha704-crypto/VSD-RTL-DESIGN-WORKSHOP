# Session 1 – RISC-V Simulation and Verification

## Introduction

In Session 1, we worked with a RISC-V based design using GitHub Codespaces.
The session involved compiling the program, running it using the Spike RISC-V
simulator, examining the generated RISC-V instructions, and observing the
simulation waveform using GTKWave.

The main objective was to understand the basic flow from source code to
simulation and waveform analysis.

---
## 1. Disassembly of the Compiled Program

In this step, the compiled `sum1ton.o` object file was examined using the
`objdump` command.

Disassembly converts the machine-code instructions stored in the object file
into a human-readable assembly language representation. This helps us
understand what instructions the processor will execute.

The screenshot shows different sections of the program, including the
`.plt` and `.text` sections. The `.text` section contains the executable
instructions of the program.

The output contains assembly instructions such as `mov`, `push`, `pop`,
`call`, `cmp`, `je`, `jmp`, and `ret`. These instructions are used by the
processor to perform operations and control the flow of the program.

### What I learned

- How to inspect a compiled object file.
- How machine code is represented as assembly instructions.
- How the `.text` section contains executable code.
- How `objdump` can be used for disassembly and debugging.
- How high-level C programs are translated into low-level instructions.

### Screenshot

<img width="796" height="859" alt="image" src="https://github.com/user-attachments/assets/c90e4f93-2c32-4e93-b5a6-f5bde7198419" />


## 2. Compiling and Running the Program

The first step was to compile the source program and generate the required
executable/output files.

Commands were executed in the GitHub Codespaces terminal to compile the
program and run the generated executable.

### What is Compilation?

Compilation converts the source code written in a programming language into
machine-level instructions that can be executed by the target processor.

For a RISC-V based application, the compiler generates RISC-V instructions
from the source program.

### What I learned

- How to use the terminal in GitHub Codespaces.
- How to compile a RISC-V program.
- How to execute the generated program.
- How to check the output of a program from the terminal.

### Screenshot

<img width="951" height="526" alt="image" src="https://github.com/user-attachments/assets/d90b2681-51c2-4ec7-9a06-c90bdb05817a" />

---

## 3. Running the Program Using Spike

Spike is a RISC-V ISA simulator. It is used to simulate the execution of
RISC-V instructions on a virtual RISC-V processor.

The program was executed using Spike to observe how the RISC-V instructions
behave during execution.

### What is Spike?

Spike, also known as the RISC-V ISA Simulator, is a functional simulator
for RISC-V processors. It helps us understand and verify RISC-V instruction
execution without requiring a physical RISC-V processor.

### What I learned

- How to run a RISC-V program using Spike.
- How an ISA simulator is used for processor verification.
- How program execution can be observed without physical hardware.

### Screenshot

<img width="304" height="543" alt="image" src="https://github.com/user-attachments/assets/5e7c9727-6854-4a86-a339-dcd9cd703ec5" />


---

## 4. RISC-V Program Execution and Output

In this step, the RISC-V program was executed and the generated instructions
were observed in the terminal. The program performs an addition operation
and produces the final output as:

**Sum = 45**

The output confirms that the program executed correctly and the expected
result was obtained.

The terminal also displays the corresponding RISC-V assembly instructions
used during program execution, such as `li`, `add`, `addi`, `sub`, `and`,
`sll`, `srl`, and `bne`.

### What I learned

- How a program is converted into RISC-V instructions.
- How RISC-V instructions are executed.
- How to verify the output of a RISC-V program.
- The program successfully produced the expected **sum of 45**.

### Screenshot

<img width="962" height="538" alt="image" src="https://github.com/user-attachments/assets/469d94d3-1484-43c9-b202-203c927fd5f3" />

## 5. Viewing the Simulation Waveform

After simulation, the generated waveform was opened using GTKWave.

GTKWave is a waveform viewer used to examine digital simulation signals
with respect to time.

The waveform allows us to observe how signals such as clock, reset, input,
and output change during simulation.

### What is a Waveform?

A waveform is a graphical representation of signal values over time.

It is useful for checking whether a digital circuit is behaving as expected.

### What I learned

- How to open a simulation waveform.
- How to identify different signals.
- How signal values change with time.
- How waveforms are used for debugging digital designs.

### Screenshot

<img width="960" height="544" alt="image" src="https://github.com/user-attachments/assets/1867dd35-47c4-4f6c-95d4-d5789b0fddba" />

---

## 6. Waveform Analysis Using GTKWave

GTKWave was used to analyze the generated simulation signals in more detail.

The horizontal axis represents time, while the individual signal traces
show the logic values of the corresponding signals.

Digital signals normally have logic values such as:

- `0` – Logic LOW
- `1` – Logic HIGH
- `X` – Unknown
- `Z` – High impedance

By observing the transitions in the waveform, we can verify whether the
design produces the expected output for the given inputs.

### What I learned

Waveform analysis is an important part of RTL verification because it helps
identify incorrect logic, timing problems, and unexpected signal behavior.

### Screenshot

<img width="548" height="603" alt="image" src="https://github.com/user-attachments/assets/8970d869-a703-4b9d-86ca-d22de8e5a38a" />


---

## 7. Viewing the Synthesized Design / Layout

The final screenshot shows the generated digital design in a graphical
view. It represents the hardware structure obtained after processing the
design.

Synthesis converts RTL (Register Transfer Level) code into a gate-level
representation using standard logic cells.

The resulting design can be examined to understand how the RTL description
is transformed into actual hardware structures.

### What is Synthesis?

Synthesis is the process of converting RTL code into a gate-level circuit
using logic gates and standard cells.

The synthesized design can then be used for further physical design steps
such as placement and routing.

### What I learned

- How RTL code can be converted into hardware.
- How synthesis produces a hardware representation.
- How the generated design can be visually inspected.
- The connection between RTL code, simulation, synthesis, and physical
  implementation.

### Screenshot

<img width="339" height="557" alt="image" src="https://github.com/user-attachments/assets/50564238-e3f0-42e8-8994-90439ca19431" />


---

# Conclusion

In Session 1, I learned the basic RISC-V design and verification flow using
GitHub Codespaces. I compiled and executed a RISC-V program, used Spike for
instruction-level simulation, examined RISC-V assembly instructions, and
analyzed simulation waveforms using GTKWave.

This session helped me understand how software instructions are executed
and how digital hardware designs can be simulated, verified, and synthesized.