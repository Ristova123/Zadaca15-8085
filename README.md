# Zadaca15-8085

Микропроцесорски систем базиран на 8085 служи за
контрола на температура. Контролата се врши секоја 0.5 s.
Доколку прочитаната температура е во интервалот помеѓу
две гранични температури, сместени на врвот на стекот, се
пали зелена сијаличка, а обратно се пали црвена сијаличка и
се запира работата на процесорот. Температурата доаѓа по
прекидна секвенца. 

**Resenie:**


![Screenshot (1)](https://github.com/Ristova123/Zadaca15-8085/blob/main/Diagram%2015.png)

Главна Програма:
```
3Ch: DCR B
RET 
MVI A, 11010011b ; 19, 5000/256=19 и ост 136 поворка кратки имплуси
OUT THB
MVI A, 10001000b ; 136
OUT TLB
MVI A,11XXXXXXb ; се стартува тајмерот
OUT CSR
INIT: MVI B,250d
PAK:MOV A,B
 ANI FFh THB EQU 00001 101
 JNZ PAK TLB EQU 00001 100
 POP D CSR EQU 00001 000
IN 01h
 CMP D
 JC STOP
 CMP E
 JNC STOP
 MVI A,11XXXXXXb
 SIM 
JMP INIT
STOP: MVI A,01XXXXXXb
 SIM
 HLT
 END 
```

 ![Screenshot (2)](https://github.com/Ristova123/Zadaca15-8085/blob/main/Code%2015.png)
 ![Screenshot (3)](https://github.com/Ristova123/Zadaca15-8085/blob/main/Code%2015.1.png)
 
**Develop by:**

[Tamara Ristova ](https://github.com/Ristova123)


**Subject**

Microcomputer's systems

**Built With**

This project is built using the following tools:

- [8085 simulator](https://github.com/8085simulator/8085simulator.github.io?tab=readme-ov-file): Assembler and emulator for the Intel 8085 microprocessor.

**Getting Started**

To get a local copy up and running, follow these steps.

**Prerequisites**

In order to run this project you need:

A working computer
Connection to internet
Setup

**How to Run**

To run the program, you need an 8085 emulator or assembler. You can use emulators like DOSBox or TASM (Turbo Assembler). Here's how to run the program using 8085 simulator:

1. Download and install 8085 simulator from [here](https://github.com/8085simulator/8085simulator.github.io?tab=readme-ov-file).
2. Clone this repository to your local machine.
3. Open 8085 simulator and load the `Zadaca15 code.asm` file.
4. Assemble the code by pressing the Assemble button.
5. Run the program by pressing the Run button or by pressing F10.
