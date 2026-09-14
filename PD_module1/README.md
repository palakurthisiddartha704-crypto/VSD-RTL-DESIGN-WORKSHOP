# Physical Design: RTL to GDSII using OpenLane

## Overview

This module introduced the fundamentals of Physical Design and the complete RTL-to-GDSII ASIC implementation flow.

The session covered the transformation of an RTL design into a physical chip layout using open-source EDA tools and the Sky130 PDK.

The major topics covered were RISC-V architecture, ASIC design flow, OpenLane, floorplanning, placement, clock tree synthesis, routing, static timing analysis, antenna rule checking, and design sign-off.

The PicoRV32 RISC-V processor core was used as an example design for understanding the practical OpenLane physical design flow.

---

## Table of Contents

1. [Introduction to Physical Design](#1-introduction-to-physical-design)
2. [RISC-V Architecture](#2-risc-v-architecture)
3. [RTL to GDSII Flow](#3-rtl-to-gdsii-flow)
4. [Open-Source ASIC Design](#4-open-source-asic-design)
5. [ASIC Physical Design Stages](#5-asic-physical-design-stages)
6. [Floorplanning and Power Planning](#6-floorplanning-and-power-planning)
7. [Placement](#7-placement)
8. [Clock Tree Synthesis](#8-clock-tree-synthesis)
9. [Routing](#9-routing)
10. [OpenLane](#10-openlane)
11. [Sky130 PDK](#11-sky130-pdk)
12. [PicoRV32 Implementation](#12-picorv32-implementation)
13. [OpenLane Setup](#13-openlane-setup)
14. [OpenLane Configuration](#14-openlane-configuration)
15. [Running the OpenLane Flow](#15-running-the-openlane-flow)
16. [Synthesis Results](#16-synthesis-results)
17. [Physical Design Reports](#17-physical-design-reports)
18. [Static Timing Analysis](#18-static-timing-analysis)
19. [Antenna Rule Violations](#19-antenna-rule-violations)
20. [Layout and Final Results](#20-layout-and-final-results)
21. [Summary](#21-summary)

---

# 1. Introduction to Physical Design

Physical Design is the process of converting a synthesized gate-level netlist into a physical layout that can be manufactured as an integrated circuit.

The main objective of physical design is to implement the logical design while satisfying constraints related to:

* Area
* Timing
* Power
* Routing
* Design rules
* Signal integrity

The physical design flow consists of several stages including floorplanning, placement, clock tree synthesis, routing, and sign-off.

---

# 2. RISC-V Architecture

RISC-V is an open Instruction Set Architecture (ISA) based on the Reduced Instruction Set Computer (RISC) concept.

Unlike proprietary processor architectures, RISC-V is an open standard that allows processor implementations to be designed and customized.

In this module, the PicoRV32 RISC-V processor core was used as an example RTL design.

The implementation process can be divided into three major parts:

* Part 1 – RISC-V Instruction Set Architecture
* Part 2 – RTL Design and Synthesis
* Part 3 – Physical Design and Implementation

---

# 3. RTL to GDSII Flow

The ASIC design flow starts with an RTL description of the hardware and ends with a physical layout represented by a GDSII file.

The simplified flow is:

```text
RTL
 ↓
Synthesis
 ↓
Floorplanning
 ↓
Power Planning
 ↓
Placement
 ↓
Clock Tree Synthesis
 ↓
Routing
 ↓
Sign-Off
 ↓
GDSII