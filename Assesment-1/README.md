# Sequence Detector – Assessment 1

## Introduction

This repository contains the work completed for Assessment 1 on the design, simulation, synthesis, and verification of a Sequence Detector using Verilog HDL.

The work includes RTL design, RTL simulation, waveform analysis using GTKWave, logic synthesis using Yosys, Gate-Level Simulation (GLS), and comparison of RTL and GLS results.

## Objectives

- To design a sequence detector using Verilog HDL.
- To understand and implement a finite state machine (FSM).
- To perform RTL simulation using Icarus Verilog.
- To generate and analyze VCD waveform files using GTKWave.
- To synthesize the RTL design using Yosys.
- To analyze the synthesized netlist.
- To perform Gate-Level Simulation (GLS).
- To compare RTL and GLS simulation results.

## Tools and Technologies

- Verilog HDL
- Icarus Verilog
- GTKWave
- Yosys
- Linux / VSDSquadron Virtual Machine
- Git and GitHub

## Table of Contents

1. [Sequence Detector Design](#1-sequence-detector-design)
2. [RTL Simulation](#2-rtl-simulation)
3. [Waveform Analysis](#3-waveform-analysis)
4. [RTL Synthesis](#4-rtl-synthesis)
5. [Gate-Level Simulation](#5-gate-level-simulation)
6. [RTL vs GLS Comparison](#6-rtl-vs-gls-comparison)
7. [Overall Result](#7-overall-result)
8. [Conclusion](#8-conclusion)

## 1. Sequence Detector Design

The sequence detector was designed using Verilog HDL based on a finite state machine (FSM) approach.

### Design Files

- `sequence_detector.v`
- `tb.v`
- `synthesized.v`

## 2. RTL Simulation

The RTL design was simulated using Icarus Verilog to verify the functional behavior of the sequence detector.

The simulation output was observed for different input sequences and the `detected` output was verified.

## 3. Waveform Analysis

The generated VCD file was opened using GTKWave to analyze the simulation waveforms.





## 4. RTL Synthesis

The RTL design was synthesized using Yosys.

The synthesized design was successfully converted into a gate-level representation, and synthesis statistics were obtained.





## 5. Gate-Level Simulation

Gate-Level Simulation (GLS) was performed using the synthesized netlist.

The GLS waveform was analyzed using GTKWave to verify the behavior of the synthesized design.

### GLS Waveform




## 6. RTL vs GLS Comparison

The RTL and GLS waveforms were compared to verify that the synthesized design maintains the expected functional behavior.



## 7. Overall Result

The Sequence Detector was successfully designed, simulated, synthesized, and verified through Gate-Level Simulation.

The RTL simulation and GLS results were compared, and the expected sequence detection behavior was observed.

## 8. Conclusion

The Assessment 1 work successfully demonstrated the complete RTL-to-GLS flow for a Verilog-based Sequence Detector. The design was verified through RTL simulation, synthesized using Yosys, and validated through Gate-Level Simulation using the generated netlist.