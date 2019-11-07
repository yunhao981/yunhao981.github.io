---
title: pintos初探
show: true
date: 2019-11-07 14:07:01
categories: pintos
tags: OS
description:
---

# Installation

[Official Instruction](https://web.stanford.edu/class/cs140/projects/pintos/pintos_1.html)

# Install Dependencies

Check this [Installing Pintos](https://web.stanford.edu/class/cs140/projects/pintos/pintos_12.html).


We don't want to install Bochs.

We are going to run pintos with QEMU.
# Fix undefined reference to 'floor'

```
setitimer-helper.o: In function `main':
setitimer-helper.c:(.text+0xcb): undefined refernce to `floor'
collect2: error: ld returned 1 exit status
<builtin>: recipe for target 'setitimer-helper' failed
make *** [setitimer-helper] Error 1
```
## utils/Makefile

Line 5: 

``` perl
LDFLAGS = -lm
```
Change `LDFLAGS` to `LDLIBS`

# Fix $^V problem
```
Unrecognized character \x16; marked by <-- HERE after if ($<-- HERE near column 7 at ~/code/pintos/src/utils/pintos line 911.
```
## utils/pintos

Line 911: 

```perl
if ($^V ge 5.8.0)
```
Delete `$^V` and type it again.

# Fix SIGVTALRM problem
```
Prototype mismatch: sub main::SIGVTALRM () vs none at /usr/bin/pintos line 949.

Constant subroutine SIGVTALRM redefined at /usr/bin/pintos line 941.
```
## utils/pintos

Line 930:

Comment out the whole SIGVTALRM function.


# Modifing files to run with QEMU
```
squish-pty bochs -q
exec: No such file or directory
```


## threads/Make.vars

Line 7:

```perl
SIMULATOR = --bochs
```

Change `bochs` to `qemu`

## utils/pintos

Line 103: 

```perl
$sim = "bochs" if !defined $sim;
```
Change `bochs` to `qemu`

Line 259:

```perl
my $name = find_file ('kernel.bin');
```
Change `kernel.bin` to the explicit location of kernel.bin in `$ProjectFolder/threads/build/`

e.g. `/home/parallels/Project/pintos/src/threads/build/kernel.bin`


## utils/Pintos.pm

Line 362:

```perl
$name = find_file ("loader.bin") if !defined $name;
```

Change `loader.bin` to the explicit location of loader.bin in `$ProjectFolder/threads/build/`

e.g. `/home/parallels/Project/pintos/src/threads/build/loader.bin`

# BOOTLOOP

cannot find memory?

cannot print init_ram_page in init.c

finnally find it impossible to work on PD with qemu due to PD's lack of vmx support

so either changing to bochs or running ubuntu in VMware

damn fuck

why not trying to run pintos simulator on macOS ?

Unix-like with VT-x support


maybe i should just follow the guide provided by JHU or SJTU ?


