# Samsung RISC-V Talent Development Internship Program
The program is based on the RISC-V architecture and uses open-source tools to teach people about VLSI chip design and RISC-V. Powered by Semiconductor India Research (SSIR) along with VLSI System Design (VSD) The instructor for this internship is Kunal Ghosh Sir.

# Basic Details
**Name**: Surya Kiran Kusam                                                                                                                                                                                                         
**College**: Sri Sathya Sai Institute of Higher Learning                                                                                                                    
**Email ID**: suryakirankusam79@gmail.com                                                                                                                                                                                               
**GitHub Profile**: https://github.com/suryakirankusam                                                                                                                                                                                
**LinkedIN Profile**: https://www.linkedin.com/in/suryakirankusam 

<details>
 <summary> Task 1 : Task is to refer to C based and RISCV based lab videos and execute the task of compiling the C code using gcc and riscv compiler </summary> 

 ## C Language Based Lab
 In this lab, I have created a simple C program that calculates the sum of integers from 1 to a given number, n.
Started by typing the following command in the terminal to make sure that i am in the home directory
Next, I have written my C program. Opened an editor, for example leafpad, and create a new file called sum1ton.c
Wrote the code for the sum of numbers from 1 to n

![Screenshot 2025-01-04 193219](https://github.com/user-attachments/assets/2909c488-715c-44dc-be5a-1b39873795ba)


Once the code was written, saved the file and close the editor.
To compile the program, used the gcc command. Ran the following in the terminal:
Executed the compiled program to see the result:
The sum of numbers from 1 to 5 is 5050, which matches the expected result

![Screenshot 2025-01-04 203234](https://github.com/user-attachments/assets/e6ba9e17-fd8d-4a55-9ff6-312937e1d4a6)


Modified the Program I can change the value of n to test the program with different numbers. For example, change n = 5 to n = 55 and recompile

![image](https://github.com/user-attachments/assets/ea089d83-e40c-4652-a421-574de48fd729)


Then saved the file and re-ran the compilation and execution steps.
This simple program demonstrates how to calculate the sum of integers from 1 to n using a for loop. I can now experiment with different values of n and observed the results.

![image](https://github.com/user-attachments/assets/12d47dbf-8725-4114-a727-f8395387fc00)

## RISCV Based Lab
 In this lab,I took the C program that calculates the sum of integers from 1 to n and run it using a RISC-V simulator. I first compiled it with the RISC-V GCC compiler, explored the assembly code generated, and analyze the instructions. Here’s a step-by-step guide to executing this task. First, ensured that the C program I wrote in the previous lab is saved. Now, compiled it using the RISC-V GCC compiler. Used the following command in the terminal: 
```
riscv64-unknown-elf-gcc -O1 -march=rv64i -mabi=lp64 -o sum_1_to_n.o sum_1_to_n.c
```

![image](https://github.com/user-attachments/assets/cc472e8b-de8f-4c34-899c-f9754cbd47af)


Viewed the assembly code generated for the program. Used the objdump command to disassemble the object file.  Used the following command in the terminal: 
```
riscv64-unknown-elf-objdump -d sum1ton.o
```

![image](https://github.com/user-attachments/assets/323a73cd-dec4-4220-844e-babe39a0526a)

This will output a list of assembly instructions. The code may be long, so you can pipe it to less for easier navigation:

Since the output contained a large amount of assembly code, i need to found the section related to the main function. To do this, press / to search within less, and type main to jump to the main function's assembly code. Press n to move through occurrences until you find the correct section.

![image](https://github.com/user-attachments/assets/1c0336a7-9ca2-4882-97d3-328ce5766b12)


Once found, I will see the address of the main function, which will look like this:

![image](https://github.com/user-attachments/assets/d2b5afed-e423-4c11-8dcc-d08ef0c19956)


Focused on the assembly instructions generated. I saw a series of instructions that correspond to the operations in your C program.
Determined the Number of Instructions to calculate the number of instructions in the main function:
Look at the address of the first instruction in the main function (e.g., 10184).
Look at the address of the next instruction after the main function ends (e.g., 101C0).
Since each instruction occupies 4 bytes in RISC-V, you can calculate the total number of instructions by subtracting the starting address of the next instruction from the address of the main function and dividing by 4.
For example:
101C0 - 10184 = 0x3C (or 60 in decimal).
Divided by 4 (since each instruction is 4 bytes):
60 / 4 = 15 instructions.
So, there are 15 instructions in the main function.
Confirmed the Calculation, you can confirm that the addresses increase by 4 bytes as you examine the assembly code. For example, after address 0x10184, the next instruction will be at 0x10188, then 0x1018C, and so on.

Conclusion
This exercise allowed me to:

Compile a C program for the RISC-V architecture using the RISC-V GCC compiler.
Disassemble the object file to view the generated assembly code.
Analyzed the instructions in the main function and calculate the number of instructions.
By modifying the compiler optimization options (e.g., -O1, -O2, -O3), you can observe how the generated assembly code changes. Make sure to research what each optimization option does to understand the impact on the assembly code.
</details>

<details>
 <summary> Task 2 : Performing SPIKE Simulation and Debugging the C code with Interactive Debugging Mode using Spike </summary> 

 The third lab. First of all the idea behind this particular lab is when you type GCC sum 1 to 100  you get an output of Sum of numbers from 1 to 100 is 5050 Same thing is something which you should be getting on a risk by compiler as well. 

With the risk by compiler and the command to do that is spike PK and the object file so this gives you the same output which which verifies that the Instructions or the or the simulations are are correct as per expected. 

Now, let's see. Let's try to debug this one. So we what we'll do is we'll debug in spike - D PK 
We are going to run manually. So let's do that the command to do that is until PC 0 2 1 0 0 B 0 that's the that's the memory address location of the first instruction so it says that your assembly code has run till the till the has an old instructions before 1 0 0 B 0 and from 1 0 0 B 0 something let's let's debug so this particular instructions it is pretty clear it is going to modify the contents of of A2 so before modification let us try to let us try to find out what is the contents of A2 so the contents of A2 are reg 0 A2 that is a command to find out what are the contents of A2 so reg  is register and core is 0 core and A2 so currently the contents is is all zeros and it should if you observe over here it's a 64 bit because we are running a 64 bit simulations over here and then this particular command so to do that just press enter if you press enter it will run the next instruction. 

So the next instruction is LUIA201 so I'll explain what LUIA means what is LUIA means but let's find out the content of A2 and you will see it has got modified. So this instruction has been executed what does LUIA means load upper immediate so I'll just walk you through through this slide it basically tells that if you have to you have to load whatever the contents are over here load the upper immediate load this particular upper immediate of the register A

![latest](https://github.com/user-attachments/assets/635238e5-8fd3-4dad-a251-7b6bc093e49b)


Then I have crated a hello.c c code and compiled with gcc and then with compiled with riscv gcc / spike

 
![Screenshot 2025-01-03 145511](https://github.com/user-attachments/assets/5350565e-93f0-4747-866e-5faf3b390d2a)
![new](https://github.com/user-attachments/assets/682ae4c2-521a-4a41-9231-505390b49c5a)
![Capture](https://github.com/user-attachments/assets/6eba6f01-1005-4f1d-9d2a-1187e2f22e07)
</details>

<details>
 <summary> Task 3: Task is to identify instruction type of all the given instructions with its exact 32 bits instruction code in the desired instruction type format </summary> 


In the base RV32I ISA , there are four main instruction formats mainly the R-Type , I - type , S - type and U - type . All are 32 bits long.The base ISA has IALIGN=32, meaning that instructions must be aligned on a four-byte boundary in memory. If there is an misalignment an exception is taken such it branches or there will occur an unconditional jump , techincally instruction-address-misaligned exception.

![image](https://github.com/user-attachments/assets/6c5a3623-b495-460f-a732-c97619d68e21)


As in the image there are source resistors termed as rs (These are the registers that hold the input values for a particular operation or instruction). and destination resisters rd (This register holds the result of the operation performed by the instruction.) . The funct3 is a 3-bit field (field refers to a specific segment or portion of an instruction that contains particular information necessary for the processor to execute that instruction) and funct7 a 7-bit field and opcode (an instruction that specifies the operation to be done by the processor) and imm[x:y] means that the immediate value (a constant data value embedded directly within an instruction) is derived from the bits in the instruction ranging from position y to position x. The RISC-V ISA keeps the source (rs1 and rs2) and destination (rd) registers at the same position in all formats to simplify decoding.

Immediate Encoding Variants
There are a further two variants of the instruction formats based on the handling of immediates namely B-Type and J-Type

![image](https://github.com/user-attachments/assets/5e1c5b71-2dc9-45c7-9f5f-fc609391d73f)


R-TYPE :

![image](https://github.com/user-attachments/assets/f7aa60e5-4ea8-47b9-9f60-ac77d2f400cd)

the R-Type is an instruction format in the RISC-V architecture to perform arithmetic and logical operations using registers. As from above

opcode(6-0) identifies the operation to be performed (add,subtract,etc) ,

rd(11-7) is the destination register where the result is stored ,

funct3(14-12) specifies the operation within the opcode category ,

rs1(19-15) indicates the first source register that contains one of the operands for the operation ,

rs2(24-20) indicates the 2nd source register that contains the other operand for the operation ,

funct7(31-25) provides the operation, aloowing for more variations of instructions that share the same opcode and funct3 values.

I-Type :

![image](https://github.com/user-attachments/assets/31a49c3a-74c9-485b-82be-357b4dc55b2f)

the I-Type instruction format in the RISC-V architecture is designed for operations that involve immediate values and registers.

opcode(6-0) identifies the operation to be performed (load,add immediate) ,

rd(11-7) is the destination register where the result is stored ,

funct3(14-12) specifies the operation within the opcode category ,

rs1(19-15) indicates the first source register that contains one of the operands for the operation ,

imm[11:0] (31:20) is a 12 bit immediate value which is a constant directly embedded in the instruction.

S-Type :

![image](https://github.com/user-attachments/assets/7c1bb8a4-603d-42ce-bb09-558525ece633)


the S-Type instruction format in the RISC-V architecture is specifically designed for store operations, which involve writing data from registers to memory.

opcode(6-0) identifies the operation to be performed (SW - for store word) ,

imm[4:0] (11-7) these 5 bits of the immediate value specifies an offset (an offset is an adjustment made to an address) to be added to the address in rs1 ,

funct3(14-12) specifies the type of storage operation ,

rs1(19-15) first source register that contains the base address where data will be stored ,

rs2(24-20) 2nd source register that contains the data to be stored in memory ,

imm[11:5] (31:25) 7 bits of upper immediate value which complete 12 bit immediate value used as an offset ,

U-Type :

![image](https://github.com/user-attachments/assets/cdf04f5c-a302-4f32-889a-2e1b325da069)


the U-Type instruction format in the RISC-V architecture is designed for operations that involve a 20-bit immediate value, primarily used for loading upper immediate values into registers.

opcode(6-0) identifies the operation to be performed (LUI - for loading an upper immediate value) ,

rd(11-7) destination register where the result of the operation will be stored ,

imm[31:12] (31:12) 20 bit immediate value which is loaded into the upper part of the destination structure

B-Type :

![image](https://github.com/user-attachments/assets/509c096b-7723-489a-8379-448ca184a1f5)


the B-Type instruction format in the RISC-V architecture is primarily used for branch instructions, which control the flow of a program based on certain conditions.

opcode(6-0) identifies the operation to be performed (BEQ - equals to , BNE - not equal to) ,

funct3(14-12) specifies the type of branch operation ,

rs1(19-15) is a first source register that contains one of the oprands for the comparision ,

rs2(24-20) the 2nd register that contains the operand for the comparision ,

imm[4:1] (11:7) the lower bits of the immediate value used as part of the offset ,

imm[10:5] (30:25) the middle bits of the immediate value which are also part of the offset for branching ,

imm(1 bit) sign bit of the immediate value, which is used to complete the 13-bit immediate offset for branching .

J-Type :

![image](https://github.com/user-attachments/assets/91bb1f5e-e64d-4bec-b86d-81ddfdd80650)

the J-Type instruction format in the RISC-V architecture is specifically used for jump instructions, which allow for unconditionally transferring control to a new instruction address.

opcode(6-0) identifies the operation to be performed (JAL - jump and link) ,

rd(11-7) destination register where the return address will be stored ,

imm[19:12] (31:12) middle bits of the immediate value which are part of the target address to jump to ,

imm(1 bit) sign bit of the immediate value,which helps in determining the direction of the jump ,

imm[10:1] (30:21) lower bits of the immediate value which are also part of the target address for jumping ,

imm(1 bit) this bit is included to help with sign extension when calculating the jump address .

</details>
