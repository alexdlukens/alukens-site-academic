---
title: ECE 429 Final Project
subtitle: "ECE 429: Intro to VLSI Design"
date: 2020-11-29T20:24:30.121Z
draft: false
featured: false
tags:
  - VLSI
links: []
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
The final project for ECE 429 involved two case studies about a 32-bit pipelined CPU design. The first case study centered around implementing several different adder designs for the ALU unit of the CPU design (Carry-Ripple, Carry-Lookahead, Carry-Select, and Carry-Skip), and analyzing the impact each design has on the overall performance of the CPU design. Students were required to implement a standardized testbench to provide stimuli to the CPU to ensure correct functionality of the ALU.

In the second case study, a new logic module is to be added to the ALU design. This additional logic is to be a 32-bit comparator that will tell whether one operand is greater than, less than, or equal to a second operand. Students were required to implement a single-bit comparator and a 4-to-2 multiplexer using Verilog, and then use these several instances of these modules to create a 32-bit comparator that will be used in the ALU.

Performance of the CPU in all scenarios was compared after physical synthesis, with the maximum clock frequency for each design being calculated by determining the slack time available at a given clock frequency. It is important to note that if the parameters for logic synthesis were altered (each design was synthesized specifically for operation at 30MHz), it will be possible to greatly improve performance at the cost of increased synthesis time.