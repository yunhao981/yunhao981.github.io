---
title: csapp-lec-05.md
categories: csapp
tags: csapp
description: loading save data from 2017
show: true
date: 2022-06-17 01:27:26
---

# Preface

想不起太多骑行在路上时的心里想法

反正就是想去看底层浪漫网课了

想看就去做作业了

四月的时候也重新开始过，碰到周末实在是难继续

迷茫啊

每天对着脚本都快 Burn Out 了

可能最近已经经历过一轮了吧

工作效率直线下降

与其浪费时间在纠结方向上，不如都去试试

反正就是先做起来了，这回能撑多久不知道

这回没有学分，没有GPA，没有DDL，没有自己在做与众不同的事情的蜜汁快感，对未来就业没有任何直接帮助

这甚至是大一的基础课…… 

我甚至当年还看过……

科班出身毕业两年的人要回头去看这些东西说出来甚至是耻辱好吧

但我现在完全不会

不会就是不会

那就读个档吧

# Lecture 05 Machine level Programming I Basics

assembly code == machine code

what the machine is trying to do

the core of the course

CISC Complex Instruction Set Computers

RISC Reduced Instruction Set Computers

RISC vs. CISC in 80s

## C, assembly, machine code

Architecture (ISA): compiler target, parts of processor design to write assembly code

Microarchitecture: implementation of the architecture

Program counter: 

    Address of next instruction

Registers

    program data, heavily used

Condition codes:

    store status information

Memory:

    byte addressable array
    
    code, user data

C program --- Compiler ---> ASM program --- Assembler ---> Object program --- Linker ---> Exceutable program

`gcc -Og -S sum.c` 

-S, stop at 
-Og, optimization at level g for debugging in recent versions of gcc
-O1, turn on the optimizer in the past, be more efficient

### disassembler 

`objdump -d sum`

referse engineers from object code to assembly code

var/func names are all lost at this assembly level, all of them are just machine code

### Assembly 

only do one thing per instruction

transfer data between memory and register

arithmetic functions

control flow

gdb can also disassemble function

## Assembly basics: registers, operands, move

### registers

%rxx, 64 bit

%exx, 32 bit, lower 32 bits of the 64 bit stuff

```
%rax, %rbx, %rcx, %rdx

%rsi, %rdi, %rsp, %rbp

%r8, %r9 ... %r15

```

rx-abcd

r8...r15

rsi, rdi

rsp, rbp

legacy purpose: 
```
accumulate

base

counter

data

si: source index

di: destination index

sp: stack pointer

bp: base pointer

```

### move

moving data

```
movq source dest
```

CANNOT MOVE value from MEMORY TO MEMORY

read value from memory

copy it to register

write it to memory

```
D(Rb, Ri, S)

MEM[MEM(Rb) + S * MRM(Ri) + D]

naturlly work with arrays

```

q mean 8 bytes

bwlq, 1248

## Arithmetic & logical operations


Address Computation Instruction

leaq Src, Dst

load effective address

compute address without a memory reference

compute x + k * y, k = 1, 2, 4, 8

addq, subq, imulq

salq: dest = dest << src

sarq: dest = dest >> src, arithmetic, add sign in the left

shrq: des = dest >> src, logical, add 0 in the left

xorq

andq

orq

src comes in the first

destination is the second


