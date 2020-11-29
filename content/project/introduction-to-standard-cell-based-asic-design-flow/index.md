---
title: Introduction to Standard Cell Based ASIC Design Flow
subtitle: "ECE 429: Intro to VLSI Design"
date: 2020-11-29T20:06:13.060Z
draft: false
featured: true
tags:
  - VLSI
links:
  - url: https://alukens.com/project/Introduction-to-Standard-Cell-Based-ASIC-Design-Flow/lab-9.pdf
    name: Full Report Link
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
This laboratory is the penultimate laboratory project for the Introduction to VLSI Design course at Illinois Institute of Technology. In this project, I was introduced to the "ASIC Design Flow", or "RTL-to-GDSII Design Flow" that is commonly used to create custom silicon/FPGA designs in an industry setting. In this laboratory, a simple 8-bit accumulator and related testbench were created using Verilog HDL. Synopsys Design Compiler was utilized to perform logic synthesis on this Verilog design. Specifically, the cell was synthesized in terms of the GSCL45nm library. Physical Synthesis/Place-and-Route was performed on the synthesized design using Cadence Encounter. The design was tested for logical equivalence, and the results of the testbench simulation compared at each stage in the ASIC Design Flow. Equivalence checking was performed using Formality, and simulations were performed using Cadence Verilog-XL.

After the functionality of the placed-and-routed design, the resultant GDSII database file was imported into Cadence Virtuoso and the physical layout of the design was examined.