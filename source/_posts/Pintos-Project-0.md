---
title: Pintos-Project-0
show: true
date: 2021-04-07 13:24:06
categories: pintos
tags: OS
description:
---
# Get the things real

I was too young & too simple last year, thinking just install bochs via system default package manager will work.

Make sure install the exact same version of bochs-2.6.2, and compile it from source code. 

Folowing the setup guides [HERE](https://cs.jhu.edu/~huang/cs318/fall17/project/setup.html) to compile bochs-2.6.2 with source code on SourceForge.

On Fedora, packages such as `libX11-devel`, `libXrandr-devel` and `ncurses-devel` are needed.

# PC Bootstrap

bootstrapping: process of loading OS into MEM

helpers:
    1. BIOS
    2. booloader

power on -> BIOS -> BL -> OS

BIOS tests Hardware and finds bootable Devices

IA32: fits within 512B in MEM for partition 436Bytes for MBR

Low Memory: `0x00000000` to `0x000A0000`, 640KB

VGA Display: `0x000A0000` to `0x000C0000`, 768KB

16-bit devices: `0x000C0000` to `0x000F0000`, 960KB

BIOS ROM: `0x000F0000` to `0x00100000`, 1MB

Extended Memory & 32-bit memory mapped devices: `0x00100000` to `0xFFFFFFFF`, 4GB

# The Boot Loader

sector: the disk's minimum transfer granularity for Read or Write operations

boot sector: the first sector of a bootable disk

BIOS finds a bootable HD

-> load 512B boot sector into MEM at `0x7c00` through `0x7dff`

-> set CS:IP to `0000:7c00`

CS: Code Segment Register

IP: Instructor Pointer

SS: Stack Segment

DS: Data Segent

ES: moving data around

IA32 Bootloaders runs in real-addressing mode

CS are used to compute the addresses of memory accesses

```
    address = 16 * segment + offset
```

Each segment is 64KB. 

The kernel is 512KB, 1024 sectors, must be loaded into memory starting at `0x20000`.

The loader reads no more than 512KB. More data than this will cross into other regions for BIOS and Hardware.

# The Kernel

The BL transfers contorl to the kernel's entry point.

The `start()` in `threads/start.S` switches the CPU from 'legacy mode' to 'protected mode'.

A20 line: the CPU's address line numbered 20.
enable it to access more memory than the first 1MB.

# Debugging

## 1. Use GDB to trace the QEMU BIOS


run pintos like:
```
pintos --gdb -- run mytest
```

then run this in another terminal:
```
pintos-gdb kernel.o
```

in Pintos-GDB, run this to connect it to the pintos running:
```
target remote localhost:1234
```

use `c` to continue til the end, use `si` to run one step
use `b` to set breakpoints, like `b *0x7c00`.



### 1.1 What is the first instruction that gets executed?

```asm
[f000:fff0]    0xffff0:	ljmp   $0x3630,$0xf000e05b
0x0000fff0 in ?? ()
```

ljmp: transfer execution control to a different point in the instruction stream.

### 1.2 At which physical address is this instruction located?

This instruction is located in `0x0000fff0`.

### 1.3 Can you guess why the first instruction is like this?

Maybe it was trying to find the initial point for bootloader.


### 1.4 What are the next three instructions?

```asm
[f000:e05b]    0xfe05b:	cmpw   $0xffc8,%cs:(%esi)
0x0000e05b in ?? ()

[f000:e062]    0xfe062:	jne    0xd241d08c
0x0000e062 in ?? ()

[f000:e066]    0xfe066:	xor    %edx,%edx
0x0000e066 in ?? ()
```

## Tracing Pintos Bootloader


### 2.1 How does the bootloader read disk sectors? In particular, waht BIOS interrupt is used?


### 2.2 How does the bootloader decides whether it finds the Pintos kernel?


### 2.3 What happens when the bootloader could not find the Pintos kernel?


### 2.4 At what point does the bootloader transfer control to the Pintos kernel?
