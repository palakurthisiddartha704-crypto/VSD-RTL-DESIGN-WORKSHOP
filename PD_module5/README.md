# MODULE-5
# SKY130 Physical Design – Routing, DRC, Parasitic Extraction & TritonRoute

## Overview

This module covers the major stages involved in the physical design flow using the SKY130 technology and OpenLane-based tools.

The work includes:

- Global and detailed routing
- Maze routing using Lee's Algorithm
- Design Rule Checking (DRC)
- Wire-width and via-spacing verification
- Parasitic extraction
- SPEF generation
- TritonRoute
- Preprocessed route guides
- Intra-layer and inter-layer routing
- Routing topology optimization
- Connectivity handling
- OpenLane routing and synthesis results
- Physical design flow verification

---
# Table of Contents

- [Introduction](#introduction)
- [Overview](#overview)
- [Tools and Technologies](#tools-and-technologies)
- [1. Routing](#1-routing)
  - [1.1 Route](#11-route)
- [2. Maze Routing – Lee's Algorithm](#2-maze-routing--lees-algorithm)
- [3. Design Rule Checking](#3-design-rule-checking)
  - [3.1 DRC Clean Layout](#31-drc-clean-layout)
- [4. DRC – Wire Width](#4-drc--wire-width)
- [5. DRC – Via Spacing](#5-drc--via-spacing)
- [6. Parasitic Extraction](#6-parasitic-extraction)
- [7. OpenLane Physical Design Flow](#7-openlane-physical-design-flow)
- [8. Floorplanning and Power Planning](#8-floorplanning-and-power-planning)
- [9. OpenLane Physical Design Execution](#9-openlane-physical-design-execution)
- [10. OpenLane Configuration Parameters](#10-openlane-configuration-parameters)
- [11. Routing Output](#11-routing-output)
- [12. Fast Route and Detailed Route](#12-fast-route-and-detailed-route)
- [13. TritonRoute](#13-tritonroute)
- [14. Preprocessed Route Guides](#14-preprocessed-route-guides)
- [15. Intra-Layer Parallel and Inter-Layer Sequential Routing](#15-intra-layer-parallel-and-inter-layer-sequential-routing)
- [16. TritonRoute Problem Statement](#16-tritonroute-problem-statement)
- [17. Handling Connectivity](#17-handling-connectivity)
- [18. Routing Topology Algorithm](#18-routing-topology-algorithm)
- [19. OpenLane TritonRoute Execution](#19-openlane-tritonroute-execution)
- [20. Routing Data Generation](#20-routing-data-generation)
- [21. SPEF / Parasitic Extraction](#21-spef--parasitic-extraction)
- [22. OpenLane Synthesis and Routing Results](#22-openlane-synthesis-and-routing-results)
- [Physical Design Flow Summary](#physical-design-flow-summary)
- [Key Learning Outcomes](#key-learning-outcomes)
- [Tools and Technologies](#tools-and-technologies)
- [Conclusion](#conclusion)

# Tools and Technologies

| Tool / Technology | Purpose |
|---|---|
| **OpenLane** | Automated RTL-to-GDSII physical design flow |
| **SKY130** | Open-source 130 nm semiconductor process technology |
| **TritonRoute** | Detailed routing and design-rule-aware routing |
| **OpenROAD** | Physical design implementation and optimization |
| **OpenSTA** | Static Timing Analysis (STA) |
| **Magic** | Layout viewing and physical verification |
| **LEF** | Library Exchange Format containing physical library information |
| **DEF** | Design Exchange Format containing physical design information |
| **SPEF** | Standard Parasitic Exchange Format for extracted parasitic data |
| **Linux / Ubuntu** | Execution environment for the physical design tools |
| **Oracle VM VirtualBox** | Virtual machine environment used to run the Linux-based flow |
| **GitHub** | Version control and documentation of the workshop work |

# Introduction

Physical Design is an important stage in the VLSI design flow where the synthesized circuit is converted into a physical layout that can be fabricated on silicon.

In this module, the SKY130 technology and OpenLane-based physical design flow are explored with a focus on routing and post-routing analysis. The module covers global and detailed routing, maze routing using Lee's Algorithm, Design Rule Checking (DRC), wire-width and via-spacing verification, parasitic extraction, SPEF generation, and detailed routing using TritonRoute.

The practical work also covers route-guide preprocessing, intra-layer parallel routing, inter-layer sequential routing, connectivity handling, routing topology optimization, and inspection of OpenLane-generated synthesis and routing results.

The objective of this module is to understand how routing is performed while satisfying physical design rules, maintaining connectivity, and preparing the design for post-layout timing and physical verification.

# 1. Routing

Routing is the process of establishing physical connections between the placed standard cells, pins, and other circuit components while satisfying design rules.

The routing process consists mainly of:

- Global routing
- Fast routing
- Detailed routing
- Design-rule-aware routing
- Connectivity verification

## 1.1 Route

The routing stage connects the input and output pins through physical metal layers using buffers, flip-flops, and routing tracks.


The routed layout contains:

- Flip-flops
- Buffers
- Decap cells
- Standard-cell blocks
- Metal interconnects
- Clock and data paths

---

# 2. Maze Routing – Lee's Algorithm

Maze routing is a grid-based routing technique used to find a valid path between two points while avoiding obstacles.

Lee's algorithm works by:

1. Starting from the source point.
2. Expanding the routing grid.
3. Assigning distance values to reachable cells.
4. Continuing until the destination is reached.
5. Backtracking through the minimum-distance path.


The routing grid is explored systematically and numbered according to the distance from the source.

This approach guarantees a valid shortest-path solution when a path exists, although it can require significant memory for large routing grids.

---

# 3. Design Rule Checking

Design Rule Checking (DRC) verifies whether the physical layout satisfies the manufacturing rules defined by the selected technology.

Typical design rules include:

- Minimum wire width
- Minimum spacing
- Via spacing
- Metal enclosure
- Layer-specific restrictions
- Connectivity constraints

## 3.1 DRC Clean Layout



The image shows the routed design after DRC verification.

A DRC-clean design indicates that the layout satisfies the checked physical design rules.

---

# 4. DRC – Wire Width

Wire width is an important physical design constraint.

If a metal wire is narrower than the minimum allowed width, it may violate the manufacturing rules and can affect the reliability of the interconnect.


# 5. DRC – Via Spacing

Vias provide electrical connections between different metal layers.

Correct spacing between vias and surrounding metal structures is necessary to prevent manufacturing violations and unintended shorts.


# 6. Parasitic Extraction

After routing, parasitic elements introduced by physical interconnects must be extracted.

Parasitic extraction identifies effects such as:

- Resistance
- Capacitance
- Interconnect delay
- Coupling effects

These parasitic values are later used for accurate timing analysis.


The extracted parasitic information can be used for post-layout timing analysis and sign-off activities.

---

# 7. OpenLane Physical Design Flow

OpenLane automates several stages of the RTL-to-GDSII physical design flow.

A simplified flow is:

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
CTS
 ↓
Routing
 ↓
DRC / LVS
 ↓
Parasitic Extraction
 ↓
Timing Analysis
 ↓
GDSII
```

## 8. Floorplanning and Power Planning
Floorplanning determines the overall physical organization of the design.
Important elements include:
Core area
Die area
Standard-cell rows
I/O placement
Power rings
Power straps
Macro placement

## 9. OpenLane Physical Design Execution
The OpenLane flow generates intermediate and final physical-design files during different stages.
9th Image – OpenLane Execution Output


## 10. OpenLane Configuration Parameters
OpenLane uses configuration parameters to control different stages of the physical design flow.
Important categories include:
Placement
Clock Tree Synthesis (CTS)
Routing
Magic
Density
Timing
Routing optimization
10th Image – OpenLane Configuration

These parameters influence:
Cell placement density
Clock-tree generation
Routing layers
Routing optimization
Layout generation

## 11. Routing Output
After the routing stage, the generated routing information can be inspected from the OpenLane run directories.
11th Image – Routing Output


## 12. Fast Route and Detailed Route
Routing can be divided into different stages.
Fast Route
Fast routing provides an initial routing solution and generates route guides.
Detailed Route
Detailed routing converts the initial routing information into actual physical routing while satisfying detailed design rules.

## 13. TritonRoute
TritonRoute is a detailed routing engine used in modern physical design flows.
It performs detailed routing while considering:
Routing guides
Design rules
Connectivity
Metal layers
Via placement
Routing constraints
13th Image – TritonRoute

TritonRoute performs the initial detailed routing while attempting to follow the preprocessed route guides.

## 14. Preprocessed Route Guides
Route guides provide information about the preferred regions and directions in which nets should be routed.
Preprocessing can simplify the routing problem by transforming the original routing guides into a form suitable for detailed routing.
14th Image – Preprocessed Route Guides

The image demonstrates the preprocessing of route guides.
Important requirements include:
Route guides should have unit width.
Route guides should follow the preferred routing direction.


## 15. Intra-Layer Parallel and Inter-Layer Sequential Routing
Routing can be performed using different strategies across and within metal layers.
Intra-Layer Parallel Routing
Multiple routing tasks can be handled in parallel within the same metal layer.
Inter-Layer Sequential Routing
Routing can proceed sequentially across different metal layers to establish complete connectivity.
15th Image – Intra-Layer Parallel & Inter-Layer Sequential Panel Routing


The image illustrates the panel-based routing approach involving:
Intra-layer parallel routing
Inter-layer sequential routing
Multiple metal layers
Panel decomposition

## 16. TritonRoute Problem Statement
The detailed routing problem can be formulated using input design information, route guides, and routing constraints.
16th Image – TritonRoute Problem Statement

Inputs
LEF
DEF
Preprocessed route guides
Output
A detailed routing solution with optimized:
Wire length
Via count
Constraints
The routing solution must satisfy:
Route-guide constraints
Connectivity constraints
Design rules

## 17. Handling Connectivity
Connectivity is a critical requirement during detailed routing.
Every net must be physically connected to all required pins and routing segments without introducing unwanted shorts.
17th Image – Handling Connectivity

An Access Point is an on-grid point on the metal layer of a route guide used to connect lower-layer segments, upper-layer segments, pins, or I/O ports.
Access Point Cluster (APC)
An Access Point Cluster is a union of access points derived from the same lower-layer segment, upper-layer guide, pin, or I/O port.

## 18. Routing Topology Algorithm
Routing topology determines how multiple connection points of a net are connected efficiently.
The topology optimization process attempts to minimize routing cost while maintaining complete connectivity.
18th Image – Routing Topology Algorithm


## 19. OpenLane TritonRoute Execution
The TritonRoute stage can be executed from the OpenLane working directory.
19th Image – TritonRoute/OpenLane Terminal


## 20. Routing Data Generation
After routing, routing-related information is stored in the corresponding OpenLane run directories.
20th Image – Routing Output Data


## 21. SPEF / Parasitic Extraction
Standard Parasitic Exchange Format (SPEF) is used to represent extracted parasitic information.
SPEF contains information related to:
Resistance
Capacitance
Nets
Interconnect parasitics
Connectivity
21st Image – SPEF Extraction

The extraction script processes the routed DEF and generates parasitic information required for post-layout analysis.

## 22. OpenLane Synthesis and Routing Results
OpenLane stores results from different stages of the physical design flow in separate directories.
Important result directories include:
results/
├── synthesis/
├── routing/
├── placement/
├── cts/
├── floorplan/
└── signoff/
22nd Image – OpenLane Results

The generated files can be inspected to verify the completion of the corresponding physical design stages.
Physical Design Flow Summary
The complete physical design process covered in this module can be summarized as:
RTL Design
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
Global Routing
    ↓
Fast Route
    ↓
Route Guide Generation
    ↓
Route Guide Preprocessing
    ↓
Detailed Routing
    ↓
TritonRoute
    ↓
DRC Verification
    ↓
Parasitic Extraction
    ↓
SPEF Generation
    ↓
Timing Analysis
    ↓
Physical Verification

# Key Learning Outcomes
-Through this module, the following concepts were studied and demonstrated:
-Understanding physical design routing
-Understanding maze routing and Lee's Algorithm
-Understanding global and detailed routing
-Understanding fast routing and detailed routing
-Understanding TritonRoute
-Understanding route guides and route-guide preprocessing
-Understanding intra-layer and inter-layer routing
-Understanding access points and access point clusters
-Understanding routing topology optimization
-Understanding DRC verification
-Understanding wire-width and via-spacing constraints
-Understanding parasitic extraction
-Understanding SPEF generation
-Understanding OpenLane routing results
-Understanding OpenLane physical-design directories and outputs


# Conclusion
This module provided practical exposure to the physical design stages following placement, with particular emphasis on routing, detailed routing, design-rule verification, and parasitic extraction.
The experiments demonstrated how OpenLane and TritonRoute can be used to generate and verify physical routing while considering connectivity, design rules, routing guides, wire width, via spacing, and parasitic effects.
The generated routing, DRC, parasitic extraction, and OpenLane result files provide the necessary information for subsequent timing analysis and final physical-design verification.
