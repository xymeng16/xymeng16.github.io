---
layout: post
title:  "16-bit Registers in 8086 microprocessor"
date:   2016-10-28 14:07:12 +0800
categories: ASM
---
Register play an important role in the computer. Each register is equal to a memory unit in the ALU, while the speed is much faster than the storer. The register is used to store the information during the process of calculating. Now I will introduce them briefly below.  
<h2>Category</h2>
The register can be classified into 2 categories:**User-Accessible Register**(UAR) and **Internal Register**(IR). UARs can be read or written by machine instructions, and IRs are not accessible by instructions, which  is used internally for processor operations. This article will introduce the UARs in 8086 microprocessor.  
UAR is made up with **general register**, **dedicated register** and **segment register**.  
<h2>User-Accessible Register</h2>  
<h3>General Register</h3>  
8 general registers are built in the 8086 microprocessor, and all of them are 16-bit long. They are:<strong>AX,BX,CX,DX,SP,BP,SI,DI</strong>.  
<strong>AX,BX,CX,DX</strong> can be called as data register. And they can be accessed both byte-by-byte(8-bit) and WORD-by-WORD(16-bit). All of the first 4 registers are general registers, but they also have their special function.  
<strong>AX</strong> can be used as accumulator, so that it is the main register of arithmetic calculating. The operands are stored in AX when multiplying and dividing. What's more, AX is also a buffer when communicating with peripherals.  
<strong>BX</strong> works as a general register, meanwhile it usually serves as base address register when calculating the address of the memory.  
<strong>CX</strong> also have its special usage. It's a hidden <strong>counter</strong> in a loop, bit shifting and string handling.  
<strong>DX</strong> ,<strong>data</strong> register, can store the high-order WORD when doing double-WORD  
<img src="https://raw.githubusercontent.com/xymeng16/xymeng16.github.io/master/_pics/8086_regs.png" align="center" alt="Intel 8086 Registers">  
Being different with [A-D]X, the remaining general registers can be only accessed WORD-by-WORD(16-bit). Besides acting as data register, their more common usage is to provide offset address when addressing, that is to say, they should be called Pointer Register.  
<strong>SP</strong> is stack pointer, and <strong>BP</strong> is base pointer. They can work together with stack segment register SS to confirm the address of a memory unit in SS. SP stores the offset address from the top of the stack. BP contains a base address of the stack area.  
<strong>SI</strong> means source index, and <strong>DI</strong> means destination index. They usually work together with data segment register DS to confirm the address of a memory unit in DS. These two registers can automatically increase and decrease, which make them convenient to change the address.  
<h3>Dedicated Register</h3>  
There are 3 dedicated registers, IP, SP and FLAGS.  
IP is instruction pointer register. It's used to store the offset address in CS. During the runtime, IP always keeps its pointer to the next instruction.  
SP is stack pointer register. This is the same register as that SP mentioned above. What should to be emphasize is that if stack segment exists in the program, the SP can't be used as a general register.  
Also, 8086 has a 16-bit flags register. Nine of these condition code flags are active, and indicate the current state of the processor: Carry flag (CF), Parity flag (PF), Auxiliary carry flag (AF), Zero flag (ZF), Sign flag (SF), Trap flag (TF), Interrupt flag (IF), Direction flag (DF), and Overflow flag (OF).  
<img src="https://raw.githubusercontent.com/xymeng16/xymeng16.github.io/master/_pics/8086_regs_flag.gif" align="center" alt="Intel 8086 Flag Registers"> 
<h3>Segment Register</h3>  
There are also four 16-bit segment registers ([CS, DS, SS, ES],have a look at the figure above) that allow the 8086 CPU to access one megabyte of memory in an unusual way. Rather than concatenating the segment register with the address register, as in most processors whose address space exceeded their register size, the 8086 shifts the 16-bit segment only four bits left before adding it to the 16-bit offset (16×segment + offset), therefore producing a 20-bit external (or effective or physical) address from the 32-bit segment:offset pair. As a result, each external address can be referred to by 2<sup>12</sup> = 4096 different segment:offset pairs.