---
title: 2-input AND gate hierarchical design using Cadence Virtuoso
subtitle: ECE 429 - Intro to VLSI Design
date: 2020-10-26T18:34:32.124Z
draft: false
featured: false
categories:
  - VLSI
links: []
image:
  filename: lab-5.pdf
  focal_point: Smart
  preview_only: false
---
In this project, I utilized Cadence Virtuoso and Formality ESP to design and test a 2-input AND gate. This gate was created using a 2-input NAND gate and an Inverter, both of which were created as independent cells. The AND gate's physical layout was created by matching the height of the NAND and Inverter layout cellviews, and linking them together using the Metal 1 layer in Cadence Virtuoso. After the design was verified to pass all design rules and constraints, the design was compared in functionality to a Verilog file performing a logical AND operation-using Formality ESP-to ensure correctness. Finally, the design was simulated in SPICE to calculate the rising and falling propagation delays of the completed AND gate.