---
title: csapp-01-datalab
categories: csapp
tags: csapp
description: datalab
show: true
date: 2022-04-25 04:24:34
---
# Environment

hp2570p running Ubuntu 22.04 LTS

with i7-3630QM and 16GB DDR3

```
➜  datalab-handout git:(master) ✗ make btest
gcc -O -Wall -m32 -lm -o btest bits.c btest.c decl.c tests.c
In file included from btest.c:16:
/usr/include/stdio.h:27:10: fatal error: bits/libc-header-start.h: No such file or directory
   27 | #include <bits/libc-header-start.h>
      |          ^~~~~~~~~~~~~~~~~~~~~~~~~~
compilation terminated.
In file included from decl.c:1:
/usr/include/stdio.h:27:10: fatal error: bits/libc-header-start.h: No such file or directory
   27 | #include <bits/libc-header-start.h>
      |          ^~~~~~~~~~~~~~~~~~~~~~~~~~
compilation terminated.
In file included from /usr/lib/gcc/x86_64-linux-gnu/11/include/limits.h:203,
                 from /usr/lib/gcc/x86_64-linux-gnu/11/include/syslimits.h:7,
                 from /usr/lib/gcc/x86_64-linux-gnu/11/include/limits.h:34,
                 from tests.c:3:
/usr/include/limits.h:26:10: fatal error: bits/libc-header-start.h: No such file or directory
   26 | #include <bits/libc-header-start.h>
      |          ^~~~~~~~~~~~~~~~~~~~~~~~~~
compilation terminated.
make: *** [Makefile:11: btest] Error 1
➜  datalab-handout git:(master) ✗ make clean
rm -f *.o btest fshow ishow *~
➜  datalab-handout git:(master) ✗ make btest
gcc -O -Wall -m32 -lm -o btest bits.c btest.c decl.c tests.c
In file included from btest.c:16:
/usr/include/stdio.h:27:10: fatal error: bits/libc-header-start.h: No such file or directory
   27 | #include <bits/libc-header-start.h>
      |          ^~~~~~~~~~~~~~~~~~~~~~~~~~
compilation terminated.
In file included from decl.c:1:
/usr/include/stdio.h:27:10: fatal error: bits/libc-header-start.h: No such file or directory
   27 | #include <bits/libc-header-start.h>
      |          ^~~~~~~~~~~~~~~~~~~~~~~~~~
compilation terminated.
In file included from /usr/lib/gcc/x86_64-linux-gnu/11/include/limits.h:203,
                 from /usr/lib/gcc/x86_64-linux-gnu/11/include/syslimits.h:7,
                 from /usr/lib/gcc/x86_64-linux-gnu/11/include/limits.h:34,
                 from tests.c:3:
/usr/include/limits.h:26:10: fatal error: bits/libc-header-start.h: No such file or directory
   26 | #include <bits/libc-header-start.h>
      |          ^~~~~~~~~~~~~~~~~~~~~~~~~~
compilation terminated.
make: *** [Makefile:11: btest] Error 
```

solved by running 

```bash
sudo apt install gcc-multilib
```

