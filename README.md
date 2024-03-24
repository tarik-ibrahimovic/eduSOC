# eduSOC
Flexible, hardware-accelerated RISC-V based SOC

## System Overview
This is a RISC-V based bare-metal C running SOC intended for DSP applications where FPGA hardware freedom might come in handy. Currently deploying only one DSP accelerator, FPGA fabric is still left laregly untouched, waiting it's call for AI inference, or be it any other kind of acceleration. At the heart of the SOC lies [eduBOS5](https://github.com/tarik-ibrahimovic/eduBOS5), our own custom RISC-V core, with **eduBUS**, a single-cycle synchronous bus tying it all together.
![SOC](FPGA-Block-Diagram.png)
## Software
Bare-metal is the current go to, with a plan on switching for FreeRTOS, when the need comes.
## Verification
## Build