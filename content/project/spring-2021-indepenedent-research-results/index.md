---
title: Spring 2021 Independent Research Results
date: 2021-07-25T17:28:54.408Z
draft: false
featured: false
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
During the Spring 2021 semester, I conducted reasearch into FPGA prototyping of RISC-V SoCs with [Karl Hallsby](https://karl.hallsby.com/). Specifically, during the course of this project we setup and experimented with the [Chipyard SoC design framework](https://chipyard.readthedocs.io/en/latest/) and the Xilinx Arty A7-35T FPGA in order to generate SoCs with dynamically configurable IO. The majority of the semester long project was spend on understanding how Chipyard was laid out, however in the end we were successful in uploading and running bare-metal C programs on the generated RISC-V SoC and creating step-by-step documentation to reproduce our results. The purpose of generating this documentation was to familiarize ourselves with the production of high-quality publications using LaTeX, as is used in many professional journals.

This project was successful in introducing us to several aspects of SoC design, including programming languages like [Scala](https://www.scala-lang.org/) and [Chisel HDL](https://www.chisel-lang.org/), improved my personal debugging and codebase exploration abilities, and tested our abilities to add to large, open-source repositories.

See our complete documentation for this project [here](https://github.com/KarlJoad/ece497)