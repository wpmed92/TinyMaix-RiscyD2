# Port TinyMaix to RiscyD2

## Chip

| Item         | Parameter          |
| ------------ | -------------------|
| Chip         | RiscyD2 (softcore) |
| Arch         | RV32IM             |
| Freq         | 20M                |
| Flash        | 48KB               |
| RAM          | 8KB                |

## Board 

Digilent Arty-A7 (with XC7A35TICSG324-1L FPGA)

## Development Environment

GCC (riscv64-unknown-elf-gcc)
Picolibc
riscyd2.h
Vivado

## Step/Project

Build the [core](https://github.com/wpmed92/RiscyD2) and load it to the board

Minor modifications in `tm_port.h`:
* `printf` is not used in favor of uart based printing (macro defined in `main.c`)
* `TM_GET_US` is not used in favor of cycles based time measurement (defined in `riscyd2.h`)

https://github.com/wpmed92/TinyMaix-RiscyD2

## Result

| config | mnist | Note |
| ------ | ----- | ---- |
| O0 CPU | 17    |      |
| O1 CPU | 12    |      |


## Author

[wpmed92](https://github.com/wpmed92)
