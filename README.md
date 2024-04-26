# eduSOC
Flexible, hardware-accelerated RISC-V based SOC

This project provides RTL for a custom-made, RISC-V based DSP intended SOC, designed to run on Gowin FPGAs. Along with the hardware comes the packed-in software, C wrappers for handling hardware modules such as UART, ADCs and similar included components; functions to test the proper operation of hardware modules; and the toolchain required to build the associated applications. While FPGA synthesis and place-and-route are done using Gowin's proprietary tools, verification is powered by open-source tools. The source files are not public yet, therefore the build steps are not included.

## System Overview
**eduSOC** is a SystemVerilog RISC-V based bare-metal C running SOC intended for DSP applications where FPGA hardware freedom might come in handy. Currently deploying a single DSP accelerator, FPGA fabric is still left largely untouched, waiting it's call for AI inference, or be it any other kind of acceleration. Handling control, and lighter computational tasks is the [eduBOS5](https://github.com/tarik-ibrahimovic/eduBOS5), our own custom RISC-V core, with **eduBUS**, a single-cycle synchronous bus, tying it all together. Another feature is that the CPU is fully interchangeable with [picoRV32](https://github.com/YosysHQ/picorv32), adding another layer of customization to the design.
![SOC](/0.doc/FPGA-Block-Diagram.png)
## Software
Tightly coupled software and hardware in this project deliver excellent performance and give you complete control over execution. Currently, the platform primarily uses bare-metal C to maximize the benefits of the specifically designed hardware, supplemented with wrappers to simplify the management of hardware modules. Future plans include transitioning to a low-level RTOS, such as FreeRTOS, to utilize its scheduling capabilities and achieve a higher level of abstraction in coding.
## Verification
Static (formal) methods are employed initially to verify clock domain crossings, logic equivalence, and assorted properties using open-source (SymbiYosys)[https://github.com/YosysHQ/sby]. Functional verification is done simulating with (Verilator)[https://github.com/verilator/verilator] and analyzing waveforms. Although it's not yet UVM, Verilator's C++ testbench is masked away with a SystemVerilog one.

An upcoming feature involves integrating a CPU/System emulator, facilitating embedded software developers in running and debugging software on a simulated model of given hardware, bypassing the complexities of full hardware functional simulation. Additionally, it can be utilized to conduct more comprehensive and in-depth verification.