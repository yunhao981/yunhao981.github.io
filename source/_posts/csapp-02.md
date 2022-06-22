---
title: csapp-02.md
categories: csapp
tags: csapp
description: loading save data from 2017
show: true
date: 2022-06-21 02:55:47
---
# 02. BOMB LAB

notes and progress

## objdump -t

打印出 bomb 的 symbol table

里面会有所有用到的函数名以及全局变量

还有他们的地址

## objdump -d

把 bomb 拆成汇编代码

里面有用到的各个函数，慢慢刚汇编吧

## strings bomb

会列出所有 bomb 用到的 string

里面有一行画风清奇

```
➜  bomb git:(master) ✗ strings bomb
/lib64/ld-linux-x86-64.so.2
&i#P`
__gmon_start__
libc.so.6
socket
fflush
strcpy
__printf_chk
exit
fopen
__isoc99_sscanf
connect
signal
puts
__stack_chk_fail
stdin
strtol
fgets
__errno_location
read
__fprintf_chk
stdout
__memmove_chk
__ctype_b_loc
getenv
stderr
alarm
gethostbyname
__memcpy_chk
close
sleep
__sprintf_chk
__libc_start_main
write
GLIBC_2.3
GLIBC_2.7
GLIBC_2.3.4
GLIBC_2.4
GLIBC_2.2.5
%z$
%r$
%j$
%b$
%Z$
%R$
%J$
UH-@7`
UH-@7`
AVAUATUSH
Tt H
\$ H
D$(H
t$PH
P[]A\A]A^
=m$
ATUSH
t%:E
[]A\
***truncH
ated***
D$h1
D$hdH3
AWAVAUATUSH
D$/A
H;D$
8[]A\A]A^A_
AWAVAUATUSH
Error: CI
lient unI
able to I
create sI
F ockefA
Error: DI
NS is unI
able to I
resolve I
server aI
F(ddrefA
F,ssA
t$0D
Error: UI
nable toI
 connectI
 to the I
F servfA
F$erA
Error: RI
esult stI
ring tooI
 large. I
IncreaseI
 SUBMITRI
_MAXBUF
*t#A
Error: CI
lient unI
able to I
write toI
 the serI
F(ver
t$@H
Error: CI
lient unI
able to I
read firI
st headeI
r from sI
F0ervefA
L$,H
D$,A
t$@H
Error: CI
lient unI
able to I
read heaI
ders froI
m serverI
t$@H
Error: CI
lient unI
able to I
read staI
tus messI
age fromI
 server
t$@L
Error: RI
esult stI
ring conI
tains anI
 illegalI
 or unprI
intable I
characteI
F8fA
F@r.A
[]A\A]A^A_
Error: CH
lient unH
able to H
create sH
E ockef
Error: DH
NS is unH
able to H
resolve H
server aH
E(ddref
E,ss
l$ L
t$(L
|$0H
%s: Error: Couldn't open %s
Usage: %s [<input_file>]
That's number 2.  Keep going!
Halfway there!
Good work!  On to the next...
Welcome to my fiendish little bomb. You have 6 phases with
which to blow yourself up. Have a nice day!
Phase 1 defused. How about the next one?
So you got that one.  Try this one.
Border relations with Canada have never been better.
Wow! You've defused the secret stage!
flyers
maduiersnfotvbylSo you think you can stop the bomb with ctrl-c, do you?
Curses, you've found the secret phase!
But finding it and solving it are quite different...
Congratulations! You've defused the bomb!
Well...
OK. :-)
Invalid phase%s
BOOM!!!
The bomb has blown up.
%d %d %d %d %d %d
Error: Premature EOF on stdin
GRADE_BOMB
Error: Input line too long
%d %d %s
DrEvil
greatwhite.ics.cs.cmu.edu
angelshark.ics.cs.cmu.edu
makoshark.ics.cs.cmu.edu
Program timed out after %d seconds
Error: HTTP request failed with error %d: %s
GET /%s/submitr.pl/?userid=%s&lab=%s&result=%s&submit=submit HTTP/1.0
Error: Unable to connect to server %s
%%%02X
%s %d %[a-zA-z ]
changeme.ics.cs.cmu.edu
AUTORESULT_STRING=%s
csapp
;*3$"
GCC: (Ubuntu 4.8.1-2ubuntu1~12.04) 4.8.1
GCC: (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3
/usr/include/x86_64-linux-gnu/bits
/usr/lib/gcc/x86_64-linux-gnu/4.8/include
/usr/include
bomb.c
stdio2.h
stddef.h
types.h
stdio.h
libio.h
<built-in>
stdlib.h
phases.h
support.h
printf
__off_t
_IO_read_ptr
_chain
size_t
_shortbuf
_IO_buf_base
long long unsigned int
read_line
/usr0/home/droh/ics3/im/labs/bomblab/src
long long int
phase_defused
_fileno
_IO_read_end
_flags
_IO_buf_end
_cur_column
__printf_chk
_old_offset
infile
initialize_bomb
_IO_marker
stdin
_IO_write_ptr
_sbuf
short unsigned int
_IO_save_base
GNU C 4.8.1 -mtune=generic -march=x86-64 -ggdb -O1 -fstack-protector
_lock
_flags2
_mode
__builtin_puts
stdout
sizetype
_IO_write_end
_IO_lock_t
_IO_FILE
fopen
_pos
_markers
unsigned char
short int
_vtable_offset
exit
bomb.c
input
_next
__off64_t
_IO_read_base
_IO_save_end
__fmt
__pad1
__pad2
__pad3
__pad4
__pad5
_unused2
argv
phase_1
phase_2
phase_3
phase_4
phase_5
phase_6
_IO_backup_base
argc
main
_IO_write_base
.symtab
.strtab
.shstrtab
.interp
.note.ABI-tag
.note.gnu.build-id
.gnu.hash
.dynsym
.dynstr
.gnu.version
.gnu.version_r
.rela.dyn
.rela.plt
.init
.text
.fini
.rodata
.eh_frame_hdr
.eh_frame
.init_array
.fini_array
.jcr
.dynamic
.got
.got.plt
.data
.bss
.comment
.debug_aranges
.debug_info
.debug_abbrev
.debug_line
.debug_str
.debug_loc
call_gmon_start
crtstuff.c
__JCR_LIST__
deregister_tm_clones
register_tm_clones
__do_global_dtors_aux
completed.6976
__do_global_dtors_aux_fini_array_entry
frame_dummy
__frame_dummy_init_array_entry
bomb.c
phases.c
array.3449
support.c
sig_handler
driverlib.c
rio_readlineb
__FRAME_END__
__JCR_END__
__init_array_end
_DYNAMIC
__init_array_start
_GLOBAL_OFFSET_TABLE_
__libc_csu_fini
skip
getenv@@GLIBC_2.2.5
phase_defused
__errno_location@@GLIBC_2.2.5
_ITM_deregisterTMCloneTable
stdout@@GLIBC_2.2.5
data_start
input_strings
strcpy@@GLIBC_2.2.5
puts@@GLIBC_2.2.5
stdin@@GLIBC_2.2.5
write@@GLIBC_2.2.5
_edata
_fini
__stack_chk_fail@@GLIBC_2.4
num_input_strings
phase_5
initialize_bomb_solve
blank_line
submitr
phase_3
phase_1
invalid_phase
init_driver
alarm@@GLIBC_2.2.5
close@@GLIBC_2.2.5
node3
read@@GLIBC_2.2.5
__libc_start_main@@GLIBC_2.2.5
fgets@@GLIBC_2.2.5
explode_bomb
node1
__data_start
signal@@GLIBC_2.2.5
gethostbyname@@GLIBC_2.2.5
node5
__memmove_chk@@GLIBC_2.3.4
__memcpy_chk@@GLIBC_2.3.4
__gmon_start__
strtol@@GLIBC_2.2.5
fun7
__dso_handle
_IO_stdin_used
host_table
func4
string_length
__libc_csu_init
fflush@@GLIBC_2.2.5
__isoc99_sscanf@@GLIBC_2.7
_end
_start
secret_phase
infile
sigalrm_handler
init_timeout
__bss_start
main
__printf_chk@@GLIBC_2.3.4
read_line
strings_not_equal
phase_4
fopen@@GLIBC_2.2.5
phase_6
scratch
_Jv_RegisterClasses
driver_post
phase_2
exit@@GLIBC_2.2.5
bomb_id
connect@@GLIBC_2.2.5
__TMC_END__
__fprintf_chk@@GLIBC_2.3.4
_ITM_registerTMCloneTable
node2
node4
sleep@@GLIBC_2.2.5
node6
_init
read_six_numbers
initialize_bomb
__ctype_b_loc@@GLIBC_2.3
stderr@@GLIBC_2.2.5
__sprintf_chk@@GLIBC_2.3.4
socket@@GLIBC_2.2.5
```

那个就是 phase 1

`Border relations with Canada have never been better.`

# Phase 2

开始刚汇编吧

```asm
0000000000400efc <phase_2>:
  400efc:	55                   	push   %rbp
  400efd:	53                   	push   %rbx
  400efe:	48 83 ec 28          	sub    $0x28,%rsp
  400f02:	48 89 e6             	mov    %rsp,%rsi
  400f05:	e8 52 05 00 00       	call   40145c <read_six_numbers>
  400f0a:	83 3c 24 01          	cmpl   $0x1,(%rsp)
  400f0e:	74 20                	je     400f30 <phase_2+0x34>
  400f10:	e8 25 05 00 00       	call   40143a <explode_bomb>
  400f15:	eb 19                	jmp    400f30 <phase_2+0x34>
  400f17:	8b 43 fc             	mov    -0x4(%rbx),%eax
  400f1a:	01 c0                	add    %eax,%eax
  400f1c:	39 03                	cmp    %eax,(%rbx)
  400f1e:	74 05                	je     400f25 <phase_2+0x29>
  400f20:	e8 15 05 00 00       	call   40143a <explode_bomb>
  400f25:	48 83 c3 04          	add    $0x4,%rbx
  400f29:	48 39 eb             	cmp    %rbp,%rbx
  400f2c:	75 e9                	jne    400f17 <phase_2+0x1b>
  400f2e:	eb 0c                	jmp    400f3c <phase_2+0x40>
  400f30:	48 8d 5c 24 04       	lea    0x4(%rsp),%rbx
  400f35:	48 8d 6c 24 18       	lea    0x18(%rsp),%rbp
  400f3a:	eb db                	jmp    400f17 <phase_2+0x1b>
  400f3c:	48 83 c4 28          	add    $0x28,%rsp
  400f40:	5b                   	pop    %rbx
  400f41:	5d                   	pop    %rbp
  400f42:	c3                   	ret    
```

TO BE CONTINUED...
