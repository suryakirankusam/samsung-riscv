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


Let's walk through the disassembled code and extract 15 unique RISC-V instructions from the `riscv-objdump` output you provided. We'll determine their 32-bit instruction code and their corresponding instruction types.

### Disassembled Code:


```
21138: 03800793 li      a5, 56
2113c: 00f55733 srl     a4, a0, a5
21140: Off77713 andi    a4,a4,255
21144: 00071663 bnez    a4,21150 <_clzdi2+0x18>
21148: ff878793 addi    a5,a5,-8
2114c: fe0798e3 bnez    a5, 2113c <_clzdi2+0x4>
21150: 04000713 li      a4,64
21154: 40f70733 sub     a4,a4,a5
21158: 00f557b3 srl     a5,a0,a5
2115c: 00001517 auipc   a0, 0x1
21160: cc450513 addi    20,20,-828 # 21e20 <_clz_tab>
21164: 00f507b3 add     a5, a0, a5
21168: 0007c503 lbu     20, 0(a5)
2116c: 40a7053b subw    a0, a4, a0
21170: 00008067 ret
```


### Instructions and 32-bit Codes:

1. **`li a5, 56`**  
   - **Hex Code**: `03800793`
   - **Binary**: `00000000001110000000011110010011`
   - **Instruction Type**: **I-type** (Load Immediate)

2. **`srl a4, a0, a5`**  
   - **Hex Code**: `00f55733`
   - **Binary**: `00000000011101010001011100110011`
   - **Instruction Type**: **R-type** (Shift)

3. **`andi ...`**  
   - **Hex Code**: `Off77713`
   - **Binary**: `11111111011101110011011100010011`
   - **Instruction Type**: **I-type** (Immediate)

4. **`bnez ...`**  
   - **Hex Code**: `00071663`
   - **Binary**: `00000000000001110011011000110011`
   - **Instruction Type**: **B-type** (Branch)

5. **`addi ...`**  
   - **Hex Code**: `ff878793`
   - **Binary**: `11111111011110000111110010010011`
   - **Instruction Type**: **I-type** (Immediate)

6. **`bnez ...`**  
   - **Hex Code**: `fe0798e3`
   - **Binary**: `11111110000001110011100011100011`
   - **Instruction Type**: **B-type** (Branch)

7. **`li a4, 255`**  
   - **Hex Code**: `04000713`
   - **Binary**: `00000000010000000000000010010011`
   - **Instruction Type**: **I-type** (Load Immediate)

8. **`sub ...`**  
   - **Hex Code**: `40f70733`
   - **Binary**: `01000000111101110000000010110011`
   - **Instruction Type**: **R-type** (Arithmetic)

9. **`srl ...`**  
   - **Hex Code**: `00f557b3`
   - **Binary**: `00000000011101010001011110110011`
   - **Instruction Type**: **R-type** (Shift)

10. **`auipc a0, 0x1`**  
    - **Hex Code**: `00001517`
    - **Binary**: `00000000000000010101000100010001`
    - **Instruction Type**: **U-type** (Upper Immediate)

11. **`addi ...`**  
    - **Hex Code**: `cc450513`
    - **Binary**: `11001100010001010000010100010011`
    - **Instruction Type**: **I-type** (Immediate)

12. **`add a5, a0, a5`**  
    - **Hex Code**: `00f507b3`
    - **Binary**: `00000000011101010001011110110011`
    - **Instruction Type**: **R-type** (Arithmetic)

13. **`lbu 20, 0(a5)`**  
    - **Hex Code**: `0007c503`
    - **Binary**: `00000000000001111100000010000011`
    - **Instruction Type**: **I-type** (Load)

14. **`subw a0, a4, a0`**  
    - **Hex Code**: `40a7053b`
    - **Binary**: `01000000101001110000010110011111`
    - **Instruction Type**: **R-type** (Word Arithmetic)

15. **`ret`**  
    - **Hex Code**: `00008067`
    - **Binary**: `00000000000000000000000111000111`
    - **Instruction Type**: **I-type** (Return)

### Summary:

Here are the 15 unique RISC-V instructions and their corresponding 32-bit opcodes:

1. `li a5, 56` → `03800793`  
2. `srl a4, a0, a5` → `00f55733`  
3. `andi ...` → `Off77713`  
4. `bnez ...` → `00071663`  
5. `addi ...` → `ff878793`  
6. `bnez ...` → `fe0798e3`  
7. `li a4, 255` → `04000713`  
8. `sub ...` → `40f70733`  
9. `srl ...` → `00f557b3`  
10. `auipc a0, 0x1` → `00001517`  
11. `addi ...` → `cc450513`  
12. `add a5, a0, a5` → `00f507b3`  
13. `lbu 20, 0(a5)` → `0007c503`  
14. `subw a0, a4, a0` → `40a7053b`  
15. `ret` → `00008067`

Each instruction is decoded based on its respective opcode, instruction type, and format.

</details>


<details>
 <summary> Task 4: Task is to Use this RISC-V Core Verilog netlist and testbench for functional simulation experiment. </summary> 

# FUNCTIONAL SIMULATION 
***
#### ABOUT IVERILOG AND GTKWAWE 
Icarus Verilog (Iverilog) and GTKWave are popular open-source tools for Verilog digital design and simulation. Iverilog simulates Verilog code (modules and testbenches) and generates output like VCD (Value Change Dump) files. GTKWave then visualizes these files, providing an intuitive graphical view of signal changes for analysis and debugging. Together, they form a complete simulation and verification environment.

"FOR SIMULATION, WE USE A VERILOG NETLIST AND TESTBENCH, FOR WHICH a .VCD FILE IS GENERATED, AND THE OUTPUT WAVEFORMS ARE SIMULATED USING GTKwave

##### VERILOG NETLIST:
``` module iiitb_rv32i(clk,RN,NPC,WB_OUT);
input clk;
input RN;
//input EN;
integer k;
wire  EX_MEM_COND ;

reg 
BR_EN;

//I_FETCH STAGE
reg[31:0] 
IF_ID_IR,
IF_ID_NPC;                                

//I_DECODE STAGE
reg[31:0] 
ID_EX_A,
ID_EX_B,
ID_EX_RD,
ID_EX_IMMEDIATE,
ID_EX_IR,ID_EX_NPC;      

//EXECUTION STAGE
reg[31:0] 
EX_MEM_ALUOUT,
EX_MEM_B,EX_MEM_IR;                        

parameter 
ADD=3'd0,
SUB=3'd1,
AND=3'd2,
OR=3'd3,
XOR=3'd4,
SLT=3'd5,

ADDI=3'd0,
SUBI=3'd1,
ANDI=3'd2,
ORI=3'd3,
XORI=3'd4,

LW=3'd0,
SW=3'd1,

BEQ=3'd0,
BNE=3'd1,

SLL=3'd0,
SRL=3'd1;


parameter 
AR_TYPE=7'd0,
M_TYPE=7'd1,
BR_TYPE=7'd2,
SH_TYPE=7'd3;


//MEMORY STAGE
reg[31:0] 
MEM_WB_IR,
MEM_WB_ALUOUT,
MEM_WB_LDM;                      


output reg [31:0]WB_OUT,NPC;

//REG FILE
reg [31:0]REG[0:31];                                               
//64*32 IMEM
reg [31:0]MEM[0:31];                                             
//64*32 DMEM
reg [31:0]DM[0:31];   


//assign EX_MEM_COND = (EX_MEM_IR[6:0]==BR_TYPE) ? 1'b1 : 1'b0;
                     //1'b1 ? (ID_EX_A!=ID_EX_RD) : 1'b0;

always @(posedge clk or posedge RN) begin
    if(RN) begin
    NPC<= 32'd0;
    //EX_MEM_COND <=1'd0;
    BR_EN<= 1'd0; 
    REG[0] <= 32'h00000000;
    REG[1] <= 32'd1;
    REG[2] <= 32'd2;
    REG[3] <= 32'd3;
    REG[4] <= 32'd4;
    REG[5] <= 32'd5;
    REG[6] <= 32'd6;
    end
    //else if(EX_MEM_COND)
    //NPC <= EX_MEM_ALUOUT;

    //else if (EX_MEM_COND)begin
    //NPC = EX_MEM_COND ? EX_MEM_ALUOUT : NPC +32'd1;
    //NPC <= EX_MEM_ALUOUT;
    //EX_MEM_COND = BR_EN;
    //NPC = BR_EN ? EX_MEM_ALUOUT : NPC +32'd1;
    //BR_EN = 1'd0;
    //EX_MEM_COND <= 1'd0;
    //end
    else begin
    NPC <= BR_EN ? EX_MEM_ALUOUT : NPC +32'd1;
    BR_EN <= 1'd0;
    //NPC <= NPC +32'd1;
    //EX_MEM_COND <=1'd0;
    IF_ID_IR <=MEM[NPC];
    IF_ID_NPC <=NPC+32'd1;
    end
end

always @(posedge RN) begin
    //NPC<= 32'd0;
MEM[0] <= 32'h02208300;         // add r6,r1,r2.(i1)
MEM[1] <= 32'h02209380;         //sub r7,r1,r2.(i2)
MEM[2] <= 32'h0230a400;         //and r8,r1,r3.(i3)
MEM[3] <= 32'h02513480;         //or r9,r2,r5.(i4)
MEM[4] <= 32'h0240c500;         //xor r10,r1,r4.(i5)
MEM[5] <= 32'h02415580;         //slt r11,r2,r4.(i6)
MEM[6] <= 32'h00520600;         //addi r12,r4,5.(i7)
MEM[7] <= 32'h00209181;         //sw r3,r1,2.(i8)
MEM[8] <= 32'h00208681;         //lw r13,r1,2.(i9)
MEM[9] <= 32'h00f00002;         //beq r0,r0,15.(i10)
MEM[25] <= 32'h00210700;         //add r14,r2,r2.(i11)
//MEM[27] <= 32'h01409002;         //bne r0,r1,20.(i12)
//MEM[49] <= 32'h00520601;         //addi r12,r4,5.(i13)
//MEM[50] <= 32'h00208783;         //sll r15,r1,r2(2).(i14)
//MEM[51] <= 32'h00271803;         //srl r16,r14,r2(2).(i15) */

//for(k=0;k<=31;k++)
//REG[k]<=k;
/*REG[0] <= 32'h00000000;
REG[1] <= 32'd1;
REG[2] <= 32'd2;
REG[3] <= 32'd3;
REG[4] <= 32'd4;
REG[5] <= 32'd5;
REG[6] <= 32'd6;
REG[7] = 32'd7;
REG[6] = 32'd6;
REG[7] = 32'd7;
REG[8] = 32'd8;
REG[9] = 32'd9;
REG[10] = 32'd10;
REG[11] = 32'd11;
REG[12] = 32'd12;
REG[13] = 32'd13;
REG[14] = 32'd14;
REG[15] = 32'd15;
REG[16] = 32'd16;
REG[17] = 32'd17;*/
/*end
else begin
    if(EX_MEM_COND==1 && EX_MEM_IR[6:0]==BR_TYPE) begin
    NPC=EX_MEM_ALUOUT;
    IF_ID=MEM[NPC];
    end

    else begin
    NPC<=NPC+32'd1;
    IF_ID<=MEM[NPC];
    IF_ID_NPC<=NPC+32'd1;
    end
end*/
end
//I_FECT STAGE

/*always @(posedge clk) begin

//NPC <= rst ? 32'd0 : NPC+32'd1;

if(EX_MEM_COND==1 && EX_MEM_IR[6:0]==BR_TYPE) begin
NPC=EX_MEM_ALUOUT;
IF_ID=MEM[NPC];
end

else begin
NPC<=NPC+32'd1;
IF_ID<=MEM[NPC];
IF_ID_NPC<=NPC+32'd1;
end
end*/


//FETCH STAGE END

//I_DECODE STAGE 
always @(posedge clk) begin

ID_EX_A <= REG[IF_ID_IR[19:15]];
ID_EX_B <= REG[IF_ID_IR[24:20]];
ID_EX_RD <= REG[IF_ID_IR[11:7]];
ID_EX_IR <= IF_ID_IR;
ID_EX_IMMEDIATE <= {{20{IF_ID_IR[31]}},IF_ID_IR[31:20]};
ID_EX_NPC<=IF_ID_NPC;
end
//DECODE STAGE END

/*always@(posedge clk) begin
if(ID_EX_IR[6:0]== BR_TYPE)
EX_MEM_COND <= EN;
else
EX_MEM_COND <= !EN;
end*/


//EXECUTION STAGE

always@(posedge clk) begin

EX_MEM_IR <=  ID_EX_IR;
//EX_MEM_COND <= (ID_EX_IR[6:0] == BR_TYPE) ? 1'd1 :1'd0;


case(ID_EX_IR[6:0])

AR_TYPE:begin
    if(ID_EX_IR[31:25]== 7'd1)begin
    case(ID_EX_IR[14:12])

    ADD:EX_MEM_ALUOUT <= ID_EX_A + ID_EX_B;
    SUB:EX_MEM_ALUOUT <= ID_EX_A - ID_EX_B;
    AND:EX_MEM_ALUOUT <= ID_EX_A & ID_EX_B;
    OR :EX_MEM_ALUOUT <= ID_EX_A | ID_EX_B;
    XOR:EX_MEM_ALUOUT <= ID_EX_A ^ ID_EX_B;
    SLT:EX_MEM_ALUOUT <= (ID_EX_A < ID_EX_B) ? 32'd1 : 32'd0;

    endcase
    end
    else begin
        case(ID_EX_IR[14:12])
        ADDI:EX_MEM_ALUOUT <= ID_EX_A + ID_EX_IMMEDIATE;
        SUBI:EX_MEM_ALUOUT <= ID_EX_A - ID_EX_IMMEDIATE;
        ANDI:EX_MEM_ALUOUT <= ID_EX_A & ID_EX_B;
        ORI:EX_MEM_ALUOUT  <= ID_EX_A | ID_EX_B;
        XORI:EX_MEM_ALUOUT <= ID_EX_A ^ ID_EX_B;
        endcase
    end

end

M_TYPE:begin
    case(ID_EX_IR[14:12])
    LW  :EX_MEM_ALUOUT <= ID_EX_A + ID_EX_IMMEDIATE;
    SW  :EX_MEM_ALUOUT <= ID_EX_IR[24:20] + ID_EX_IR[19:15];
    endcase
end

BR_TYPE:begin
    case(ID_EX_IR[14:12])
    BEQ:begin 
    EX_MEM_ALUOUT <= ID_EX_NPC+ID_EX_IMMEDIATE;
    BR_EN <= 1'd1 ? (ID_EX_IR[19:15] == ID_EX_IR[11:7]) : 1'd0;
    //BR_PC = EX_MEM_COND ? EX_MEM_ALUOUT : 1'd0; 
end
BNE:begin 
    EX_MEM_ALUOUT <= ID_EX_NPC+ID_EX_IMMEDIATE;
    BR_EN <= (ID_EX_IR[19:15] != ID_EX_IR[11:7]) ? 1'd1 : 1'd0;
end
endcase
end

SH_TYPE:begin
case(ID_EX_IR[14:12])
SLL:EX_MEM_ALUOUT <= ID_EX_A << ID_EX_B;
SRL:EX_MEM_ALUOUT <= ID_EX_A >> ID_EX_B;
endcase
end

endcase
end


//EXECUTION STAGE END
		
//MEMORY STAGE
always@(posedge clk) begin

MEM_WB_IR <= EX_MEM_IR;

case(EX_MEM_IR[6:0])

AR_TYPE:MEM_WB_ALUOUT <=  EX_MEM_ALUOUT;
SH_TYPE:MEM_WB_ALUOUT <=  EX_MEM_ALUOUT;

M_TYPE:begin
case(EX_MEM_IR[14:12])
LW:MEM_WB_LDM <= DM[EX_MEM_ALUOUT];
SW:DM[EX_MEM_ALUOUT]<=REG[EX_MEM_IR[11:7]];
endcase
end

endcase
end

// MEMORY STAGE END


//WRITE BACK STAGE
always@(posedge clk) begin

case(MEM_WB_IR[6:0])

AR_TYPE:begin 
WB_OUT<=MEM_WB_ALUOUT;
REG[MEM_WB_IR[11:7]]<=MEM_WB_ALUOUT;
end

SH_TYPE:begin
WB_OUT<=MEM_WB_ALUOUT;
REG[MEM_WB_IR[11:7]]<=MEM_WB_ALUOUT;
end

M_TYPE:begin
case(MEM_WB_IR[14:12])
LW:begin
WB_OUT<=MEM_WB_LDM;
REG[MEM_WB_IR[11:7]]<=MEM_WB_LDM;
end
endcase
end



endcase
end
//WRITE BACK STAGE END

endmodule
 ```
***

#### TESTBENCH CODE:

```  module iiitb_rv32i_tb;

reg clk,RN;
wire [31:0]WB_OUT,NPC;

iiitb_rv32i rv32(clk,RN,NPC,WB_OUT);


always #3 clk=!clk;

initial begin 
RN  = 1'b1;
clk = 1'b1;

$dumpfile ("iiitb_rv32i.vcd"); //by default vcd
$dumpvars (0, iiitb_rv32i_tb);
  
  #5 RN = 1'b0;
  
  #300 $finish;

end
endmodule
```
###### BOTH THE FILES ARE SAVED IN .v FORMAT
***
###### INSTALLATION STEPS  


###### (1)  Installing:
```
sudo apt-get update
sudo apt-get install iverilog gtkwave
```
###### (2) Generating files:
```
MAKE TWO FILES IN .v FORMAT AS SAID EARLIER FOR VERILOG NETLIST AND FOR THE TESTBENCH

(my files were v.v and vtb.v)

```


###### (3) Compiling the iverilog:
```
iverilog -o my_simulation.vvp v.v vbt.v
```
###### (4) To run the simulation:
```
vvp my_simulation.vvp

```
###### Waveform Using GTKWave:
```
gtkwave iiitb_rv32i.vcd
```

##### [it will give the simulation] 
###### [ if the vcd file is not found to be in directory then give commant : "ls -1" and see the .vcd file in the directory and run the command for GTKwave]
***
***
### SNAPSHOTS 

#### (1)
![Screenshot 2025-01-17 202444](https://github.com/user-attachments/assets/2828acb5-7b57-4d0f-8e35-bb85e2da8083)


#### (2)

![Screenshot 2025-01-18 155126](https://github.com/user-attachments/assets/71bb2506-3b87-4874-9afb-6445fb5e8302)

#### (3)
![Capture](https://github.com/user-attachments/assets/cda6c347-1f16-45b0-b7cb-300401d4e626)

***

# THE SIMULATION (PIPELINES)



![4](https://github.com/user-attachments/assets/35fda0c4-312a-43a0-9c41-301cf3435a57)


***
***
#### ABOUT PIPELINE
###### This is typical 5-stage RISC pipeline, which consists of the following stages:

###### Instruction Fetch (IF): Signals: IF_ID_IR, IF_ID_NPC Instruction is fetched from memory and the next program counter (NPC) is calculated.
  
###### Instruction Decode (ID): Signals: ID_EX_A, ID_EX_B, ID_EX_IMMEDIATE, ID_EX_IR  .The fetched instruction is decoded, and the register values are read.

###### Execute (EX): Signals: EX_MEM_ALUOUT, EX_MEM_IR .The instruction is processed, and ALU operations are performed.
###### Memory Access (MEM): Signals: MEM_WB_ALUOUT, MEM_WB_LDM .Memory operations like loads and stores are performed.
###### Write Back (WB): Signals: WB_OUT .Results from the ALU or memory are written back to the register file.

###### These represent the five stages of the pipeline:

#### Instruction Fetch (IF)
#### Instruction Decode (ID)
#### Execute (EX)
#### Memory Access (MEM)
#### Write Back (WB)
