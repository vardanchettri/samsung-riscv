<details>
<summary><b>Task 1:RISC-V-objdmp of compiled C code </b> </summary>   
<br>

# Samsung-Riscv
***program was written as follows***
```
   leafpad vardan.c
```
***
```
    #include <stdio.h>
    int main() {
        int i, sum = 0, n = 200;
        for (i = 1; i <= n; ++i) {
            sum += i;
        }
        printf("Sum of number from 1 to %d is %d\n", n, sum);
        return 0;
    } 
```
# Step 1

![aaas](https://github.com/user-attachments/assets/a81739e7-e58d-446b-994d-45e56a3484c4)


# Step 2

**after that the code was compiled using**   


```gcc vardan.c```


**the programme ./a.out was then used to execute the programme to add integer from 1 to 200**


# Step 3
``` cat vardan.c ``` 

# step 4 
![image](https://github.com/user-attachments/assets/b5bd5b82-02f7-4905-9d2f-53ead8e12a26)

# Step 5

![image](https://github.com/user-attachments/assets/11595826-44db-4e77-9eb8-6c6bc1ce2df8)

# step 6

![asss2](https://github.com/user-attachments/assets/464a570b-61d6-40ea-bd3b-94fc4bda5c1d)


***
***
</details>

---------------------------------------------------
<details>
<summary><b>Task 2 :Debugging using SPIKE </b> </summary>   
<br>

# Internship_Task_2
**IN this task we debug the Assembly code(which is)**
```
Disassembly of section .text:

00000000000100b0 <main>:
   100b0:       00021537                lui     a0,0x21
   100b4:       ff010113                addi    sp,sp,-16
   100b8:       00f00613                li      a2,15
   100bc:       00500593                li      a1,5
   100c0:       18050513                addi    a0,a0,384 # 21180 <__clzdi2+0x48>
   100c4:       00113423                sd      ra,8(sp)
   100c8:       340000ef                jal     ra,10408 <printf>
   100cc:       00813083                ld      ra,8(sp)
   100d0:       00000513                li      a0,0
   100d4:       01010113                addi    sp,sp,16
   100d8:       00008067                ret

```
***
***this is the snapshot of the code***
***
![image](https://github.com/user-attachments/assets/4b3d94b7-903d-4902-a27f-76f05d9e60c8)


***
**A DEBUGGER WAS RUN** 
***
``` spike -d pk vardan.c ``` 

![image](https://github.com/user-attachments/assets/ff38a1b4-df93-46b9-bbaa-b3771cd2cf71)



**.**


This code helps us to debug the code in assembly for every a and how many times it was used eg. a0,0x21,and for each reg we get the values

***

***
**CHECK FOR REG SP BEFORE AND AFTER -16**
***
***as in code , sp has its own reg and it has got -16, we check for the hexa decimal befor and after -16***

***the code***


``` 100b4:       ff010113                addi    sp,sp,-16 ```


![image](https://github.com/user-attachments/assets/9a1cd17a-dd4b-4bd2-9fb3-3a5e472d0aa5)


***
***

***calculation for sp***
* 1


![taskkkkkkkkkk](https://github.com/user-attachments/assets/fbe3ff99-192a-402a-8743-5ca0c45e10ff)
***
* 2


![image](https://github.com/user-attachments/assets/35024aec-ea27-40aa-bfeb-1dccea227fe3)

***
* 3



![image](https://github.com/user-attachments/assets/ffb54d10-3edb-40bc-9247-92669b2f08a8)



----------------------------------------------------------------------------------------------------------------------------
***
**CREATING A NEW C CODE AND RUNNING THROUGH RISCV COMPILER**
***
**CHECKING CODE FIRST USING ./A.OUT** 

![image](https://github.com/user-attachments/assets/3f37c5dc-f1cf-4043-8d13-9b2b6ad81efa)


***

**COMPILING THROUGH RISCV**

![image](https://github.com/user-attachments/assets/8c559dc0-e7cf-41ba-bfa1-f5bb9e375c0a)




``` spike pk v2.o ``` **was the code used**


***

**DOING DEBUG**

![image](https://github.com/user-attachments/assets/2a779d06-acb1-450e-a4f7-bbea177897bf)

</details>

------------------------------------------------------------------
<details>
<summary><b>Task 3 :RISC-V INSTRUCTION TYPES </b> </summary>   
<br>  


  # RISC-V INSTRUCTION TYPES

There are various types of instruction formats, which can be categorized into two main types: ***base instruction formats*** **&** ***immediate encoding variants***

but before that what is a instruction format.
***
**Instruction format:** The instruction formats are a sequence of bits (0 and 1) which when grouped, are known as fieldsand each field of the machine provides 
specific information to the CPU related to the operation and location of the data.They refer to the specific structure or layout of binary instructions used by a processor to perform operations and define how the bits in an instruction are divided 
and allocated to represent various components, such as the operation code (opcode), registers, memory addresses, and other relevant data.
***
***
### (1) BASE INSTRUCTION FORMATS:

In the RV32I (RISC-V 32-bit Integer) base Instruction Set Architecture (ISA), 
all instructions are 32 bits long and are classified into four formats: **R-type, I-type,  
S-type, and U-type**, each serving different operations like arithmetic, logic, memory access, and 
loading upper immediate values. Instructions must be aligned on a four-byte boundary, meaning 
their memory addresses should be multiples of 4. If an instruction is placed at an address 
like 0x1001 or 0x1003, which is not divisible by 4, it is considered misaligned, triggering an 
Instruction-Address-Misaligned Exception. This exception signals an error, and the processor 
either raises an exception to handle it or takes an unconditional jump to correct the address. 

![a](https://github.com/user-attachments/assets/56fa2e47-95b4-4d79-bd3c-c831fe0c2a6a)

###### In the RISC-V architecture, the instruction format consists of several fields, each serving a specific purpose. The source registers are denoted as rs1 and rs2 (these registers hold the input values required for an operation). The destination register is rd, which holds the result of the operation performed by the instruction. The funct3 is a 3-bit field within the instruction that helps determine the specific variant of an operation, while funct7 is a 7-bit field providing additional information about the operation. The opcode specifies the type of operation to be performed by the processor. The imm[x:y] notation refers to an immediate value, which is a constant value embedded directly within the instruction; the value is derived from the bits in the instruction from position y to position x. To simplify decoding, the RISC-V instruction set architecture (ISA) keeps the positions of the source registers (rs1 and rs2) and the destination register (rd) consistent across all instruction formats. This uniformity in layout allows the processor to quickly decode and execute instructions, enhancing efficiency.
***
### (2) Immediate Encoding Variants :

There are a further two variants of the instruction 
formats based on the handling of immediates namely B-Type and J-Type
  
  [ B-type and J-type immediate encodings are often discussed more frequently because 
of their use in branch and jump operations, respectively. However, immediates 
exist in various other instruction formats (I-type, S-type, U-type) 
as well, and each has its own way of encoding the immediate value.]




![b](https://github.com/user-attachments/assets/b29efb41-09e0-4834-9d68-1392293f4544)
![c](https://github.com/user-attachments/assets/934f0c58-f008-47c7-9fb8-780c3c7ef429)


***
***
**(i) R- TYPE**

The R-Type is an instruction format in the RISC-V architecture used for performing arithmetic and logical operations between registers. It is structured as follows:

* opcode (6-0): This field identifies the operation to be performed, such as addition, subtraction, AND, OR, etc.

* rd (11-7): This field specifies the destination register where the result of the operation will be stored after execution.

* funct3 (14-12): This 3-bit field helps specify the exact operation within the given opcode category (e.g., distinguishing between ADD and SUB operations).

* rs1 (19-15): The first source register that holds one of the operands for the operation.

* rs2 (24-20): The second source register, which contains the other operand for the operation.

* funct7 (31-25): This 7-bit field provides additional operation details, allowing for variations of instructions that share the same opcode and funct3 values.


![r](https://github.com/user-attachments/assets/01175c2f-96ad-4fb0-b294-f78f0cce23b6)




***This format allows RISC-V to execute a wide range of arithmetic and logical operations efficiently, using different combinations of the fields to define the exact operation.***
***
**(ii) I-TYPE**

The I-Type instruction format in RISC-V is used for operations that involve a combination of immediate values and registers. The format is organized as follows:

*opcode (6-0): This field determines the specific operation to execute, such as loading data or adding an immediate value.

* rd (11-7): This indicates the destination register where the result of the operation will be stored after execution.

* funct3 (14-12): A 3-bit field that specifies the type of operation within the broader opcode category (for example, differentiating between ADDI and LW operations).

* rs1 (19-15): The first source register that holds one of the operands used in the operation.

* imm[11:0] (31:20): A 12-bit immediate value, which is a constant directly embedded within the instruction. This constant serves as one of the operands in the instruction.

  ![i](https://github.com/user-attachments/assets/8e67643e-1e77-4e32-9075-0104c3ce2151)


  ***This instruction format enables RISC-V to execute
  operations that involve immediate values, such as adding
  a constant to a register or performing memory load operations,
  efficiently integrating constants within the instruction itself***.
***
**(iii) S-TYPE**

  he S-Type instruction format in RISC-V is used for operations involving store instructions, where data is written to memory. The structure is as follows:

* opcode (6-0): Specifies the operation to be performed, such as store word or store half-word.

* funct3 (14-12): A 3-bit field that defines the specific store operation (e.g., distinguishing between SW and SH).

* rs1 (19-15): The source register containing the base address for memory access.

* rs2 (24-20): The source register containing the data to be stored in memory.

* imm[11:5] (31:25) and imm[4:0] (11:7): The immediate value is split into two parts. The immediate represents the offset to the memory address and is used in combination with the base address from rs1.

   ![ss](https://github.com/user-attachments/assets/d89c614d-ee6e-40c4-8969-26512364e815)


  ***The S-Type format is specifically designed for memory store operations, where an immediate offset is added to the address in rs1, and the data in rs2 is written to the resulting address in memory.***
***
**(iv) U-TYPE**

The U-Type instruction format in RISC-V is used for operations that involve large immediate values. The structure is as follows:

* opcode (6-0): Specifies the operation to be performed, such as Load Upper Immediate (LUI) or Add Upper Immediate to PC (AUIPC).

* rd (11-7): The destination register where the result of the operation will be stored.

* imm[31:12] (31:12): A 20-bit immediate value used for loading large constants. This value is shifted left by 12 bits and placed in the upper portion of the register.

  ![uu](https://github.com/user-attachments/assets/da3322b7-b0fd-4d38-a924-d7e9b51edd0a)


  ***The U-Type format is primarily used for operations that require large constant values, allowing the instruction to load a large immediate value into the upper 20 bits of a register (e.g., LUI).***
***
**(v) B-TYPE**
The B-Type instruction format in RISC-V is used for branch operations that determine the control flow of a program. The structure is as follows:

* opcode (6-0): Specifies the branch operation, such as branch if equal (BEQ) or branch if not equal (BNE).

* funct3 (14-12): A 3-bit field that specifies the condition of the branch (e.g., comparing equality, inequality, etc.).

*  rs1 (19-15): The first source register, which is compared to the second source register for the branch condition.

* rs2 (24-20): The second source register, which is compared to rs1 for the branch decision.

* imm[12] (31:31), imm[10:5] (30:25), imm[4:1] (11:8), and imm[11] (7:7): The immediate value is used to calculate the offset for the branch. The instruction uses these fields to construct the target address for the branch.

   ![uu](https://github.com/user-attachments/assets/27712275-0bef-41e6-9482-b8a26928d50a)

  ***The B-Type format is used for conditional branching, where the program’s control flow depends on a condition involving two registers, and the target address is calculated using an immediate offset.***

***
**(vi) J-TYPE**

The J-Type instruction format in RISC-V is used for unconditional jump operations. The structure is as follows:

* opcode (6-0): Specifies the jump operation, such as Jump and Link (JAL).

* rd (11-7): The destination register, where the return address (the address of the next instruction) is stored.

* imm[20] (31:31), imm[10:1] (30:21), imm[11] (20:20), and imm[19:12] (19:12): The immediate value used to calculate the target address for the jump. The instruction fields are combined to form the full 20-bit immediate value, which is then used to determine the jump target relative to the current instruction.

  ![j](https://github.com/user-attachments/assets/b9b44e0e-e5b5-4623-9169-d40e1dc817e6)

  ***The J-Type format is primarily used for unconditional jumps, such as the JAL instruction, which allows for long-range jumps by using a large immediate value to calculate the jump address.***
***
***
# INDENTIFYING INSTRUCTIONS

  **IDENTIFYING ABOVE INSTRUCTIONS FROM THE OBJECT DUMP RESULTS FROM PREVIOUS TASK GIVEN BELOW**
  
  ```
Disassembly of section .text:

00000000000100b0 <main>:
   100b0:       00021537                lui     a0,0x21
   100b4:       ff010113                addi    sp,sp,-16
   100b8:       00f00613                li      a2,15
   100bc:       00500593                li      a1,5
   100c0:       18050513                addi    a0,a0,384 # 21180 <__clzdi2+0x48>
   100c4:       00113423                sd      ra,8(sp)
   100c8:       340000ef                jal     ra,10408 <printf>
   100cc:       00813083                ld      ra,8(sp)
   100d0:       00000513                li      a0,0
   100d4:       01010113                addi    sp,sp,16
   100d8:       00008067                ret
```

***
***

**1. ``` lui a0, 0x21``` (Address: 100b0)**
Instruction Type: U-Type
Explanation: Loads the immediate value 0x21 into the upper 20 bits of the register a0.
  
**2. ```addi sp, sp, -16 ``` (Address: 100b4)**
Instruction Type: I-Type
Explanation: Adds an immediate value -16 to the sp register, effectively reserving 16 bytes of space on the stack.
  
**3.``` li a2, 15 ``` (Address: 100b8)**
Instruction Type: I-Type
Explanation: Loads the immediate value 15 into register a2. Internally, it is equivalent to addi a2, x0, 15.
  
**4.``` li a1, 5 ```(Address: 100bc)**
Instruction Type: I-Type
Explanation: Loads the immediate value 5 into register a1. Internally, it is equivalent to addi a1, x0, 5.
  
**5.``` addi a0, a0, 384 ```(Address: 100c0)**
Instruction Type: I-Type
Explanation: Adds the immediate value 384 to the value in register a0.
**6.``` sd ra, 8(sp) ```(Address: 100c4)**
Instruction Type: S-Type
Explanation: Stores the value in register ra at the memory address sp + 8. This is used for storing data to memory.
  
**7.``` jal ra, 10408 ```(Address: 100c8)**
Instruction Type: J-Type
Explanation: The jal instruction jumps to the target address 10408 and stores the return address in register ra.
  
**8.``` ld ra, 8(sp) ```(Address: 100cc)**
Instruction Type: I-Type
Explanation: Loads data from the memory address sp + 8 into the register ra.
  
**9.``` li a0, 0 ```(Address: 100d0)**
Instruction Type: I-Type
Explanation: Loads the immediate value 0 into register a0. It is equivalent to addi a0, x0, 0.
  
**10.``` addi sp, sp, 16 ```(Address: 100d4)**
Instruction Type: I-Type
Explanation: Adds the immediate value 16 to the sp register, effectively restoring the stack pointer after reserving space.
  
**11.``` ret ```(Address: 100d8)**
Instruction Type: I-Type (mapped to jalr)
Explanation: Returns from the function by jumping to the address stored in ra, equivalent to jalr x0, ra, 0.
  
**12.``` beq a0, a1, target ```(Example Branch Instruction)**
Instruction Type: B-Type
Explanation: If the values in a0 and a1 are equal, this performs a branch to the target address.
  
**13.``` bne a0, a1, target ```(Example Branch Instruction)**
Instruction Type: B-Type
Explanation: If the values in a0 and a1 are not equal, this performs a branch to the target address.
  
**14.``` jal x1, target ```(Example Jump Instruction)**
Instruction Type: J-Type
Explanation: This performs an unconditional jump to the target address and stores the return address in register x1.
  
**15.``` slli a0, a0, 1 ```(Example Shift Instruction)**
Instruction Type: R-Type
Explanation: Shifts the value in register a0 left by 1 bit, storing the result back in a0.


###### [Branch Instructions (e.g., beq and bne) control program flow by checking conditions between two registers. beq branches to a target if the registers are equal, while bne branches if they are not. These allow for loops and conditional jumps in the program. Jump Instruction (jal) performs an unconditional jump to a specified target address and stores the return address in a register (x1), facilitating function calls and returns. Shift Instruction (slli) shifts the bits in register a0 to the left, effectively multiplying the value by 2, commonly used in operations requiring bit manipulation or efficient scaling.]

***
/* End__Task_3 */
***


</details>

----------------------------------------------------------------------------------------------------------

<details>
<summary><b>Task 4 : FUNCTIONAL SIMULATION uisng GTKWave </b> </summary>   
<br>

  # FUNCTIONAL SIMULATION 
***
#### ABOUT IVERILOG AND GTKWAWE 

###### ***Icarus Verilog*** (Iverilog) and ***GTKWave*** are powerful, open-source tools commonly used for Verilog-based digital design and simulation. Iverilog serves as a Verilog simulator, allowing users to compile and run simulations of their Verilog code, including modules and testbenches. It generates simulation output in formats like VCD (Value Change Dump), which can then be visualized using GTKWave. GTKWave is a waveform viewer that displays the simulation results in an intuitive graphical format, helping users analyze signal changes over time, zoom in on specific events, and debug their designs. Together, these tools provide a complete simulation and verification environment, with Iverilog handling the simulation and GTKWave making it easier to interpret the results. 
***
###### "FOR SIMULATION, WE USE A VERILOG NETLIST AND TESTBENCH, FOR WHICH a .VCD FILE IS GENERATED, AND THE OUTPUT WAVEFORMS ARE SIMULATED USING GTKwave
***
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

(my files were sv.v and stb.v)

```


###### (3) Compiling the iverilog:
```
iverilog -o my_simulation.vvp sv.v sbt.v
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
![1111111](https://github.com/user-attachments/assets/e7fc2e25-0fb3-44a9-82e7-231fd008cfdb)

#### (2)
![1112](https://github.com/user-attachments/assets/80962eaa-51ef-4f3e-826a-f6ab720c08e0)

#### (3)
![1113](https://github.com/user-attachments/assets/1e411742-f732-4575-9561-22b278891707)

***

# THE SIMULATION (PIPELINES)



![task 4 2](https://github.com/user-attachments/assets/dfd2229e-15c8-4d6c-8e5b-d8b2caff87b9)

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
***
##### [END_TASK_4]
***
</details>


----------------------------------------------------------------------------------------------------------------------
<details>
<summary><b>Task 5 :"SMART ULTRASONIC PROXIMITY DETECTOR WITH LED ALERT"  </b> </summary>   
<br>  

# Overview

#### This project uses an ultrasonic sensor to measure distance and control an LED based on object proximity. The TRIG_PIN sends a pulse, while the ECHO_PIN measures the reflection time to calculate distance. If an object is within 10 cm, the LED turns ON instantly; otherwise, it remains OFF. The use of pulseIn() ensures fast and accurate measurements, while a 30ms timeout prevents delays, making the system highly responsive.

#### This system is useful for object detection, obstacle avoidance, and safety applications. It can be implemented in robotics, smart parking systems, automated doors, and security alarms to detect nearby objects and trigger actions accordingly. The fast response ensures real-time decision-making, making it ideal for critical applications. The project runs on the CH32V003F4U6 microcontroller, which features a 32-bit RISC-V core based on the RV32EC instruction set, ensuring efficient performance and low power consumption. 
***
# COMPONENTS REQUIRED TO BUILD SMART ULTRASONIC PROXIMITY DETECTOR WITH LED ALERT:
*  VSD SQUADRON MINI (CH32V003F4U6 chip with 32-bit RISC-V core based on RV32EC instruction set)
* HC-SRO4 sensor


* Bread Board
* Jumper Wires


##### The SMART ULTRASONIC PROXIMITY DETECTOR WITH LED ALERT is built using essential electronic components to ensure accurate distance measurement and quick response. The VSD SQUADRON MINI, powered by the CH32V003F4U6 microcontroller with a 32-bit RISC-V core (RV32EC instruction set), serves as the brain of the system, handling sensor data and controlling outputs efficiently. The HC-SR04 ultrasonic sensor is used to detect object proximity by measuring the time delay between transmitted and received sound waves. A breadboard provides a flexible platform for assembling the circuit without soldering, while jumper wires ensure seamless electrical connections between the components. Together, these components create a fast, reliable, and responsive proximity detection system suitable for automation and safety applications. 


***
# Table for Pin connection:




## HC-SRO4 sensor to CH32V003x
|  HC-SRO4 sensor  | CH32V003x Pin |
|--------------|--------------|
| VCC         | 5 volts          |
|GND          | ground           |
| TRIGGER     | PD2          |
| ECHO        | PD5
| LED       |   PD6  |

# WORKING OF THE  CODE

The code utilizes an ultrasonic sensor to measure the distance to an object and control an LED based on that distance. In the setup() function, the necessary pins are configured: TRIG_PIN (PD2) for sending the trigger pulse, ECHO_PIN (PD5) for receiving the reflected echo, and LED_PIN (PD6) to control the LED. In the loop() function, the TRIG_PIN sends a pulse to the ultrasonic sensor, causing it to emit an ultrasonic wave. The ECHO_PIN then listens for the echo and measures the time it takes for the wave to return. This duration is converted into a distance using the speed of sound. If the distance is less than 10 cm, the LED_PIN is set HIGH, turning on the LED; otherwise, it is set LOW to turn the LED off. This process repeats every 500 milliseconds, continuously monitoring the distance and adjusting the LED based on proximity. This setup can be used for proximity sensing, such as in obstacle detection or distance measurement applications.

# PROGRAMME CODE
```
#include Arduino.h

#define TRIG_PIN PD2  
#define ECHO_PIN PD5  
#define LED_PIN  PD6  

void setup() {
    pinMode(TRIG_PIN, OUTPUT);
    pinMode(ECHO_PIN, INPUT);
    pinMode(LED_PIN, OUTPUT);
}

void loop() {
    uint16_t duration;
    int distance;

     Send trigger pulse
    digitalWrite(TRIG_PIN, LOW);
    delayMicroseconds(2);
    digitalWrite(TRIG_PIN, HIGH);
    delayMicroseconds(10);
    digitalWrite(TRIG_PIN, LOW);

     Wait for Echo pin (with timeout)
    unsigned long startTime = millis();
    while (digitalRead(ECHO_PIN) == LOW) {
        if (millis() - startTime  100) return;   Exit if timeout
    }

     Measure Echo duration
    duration = 0;
    while (digitalRead(ECHO_PIN) == HIGH) {
        duration++;
        delayMicroseconds(1);
    }

     Convert to distance (integer math)
    distance = (duration  34)  2000;

     LED logic
    if (distance  0 && distance  10) {
        digitalWrite(LED_PIN, HIGH);
    } else {
        digitalWrite(LED_PIN, LOW);
    }

    delay(500);
}



```





</details>

----------------------------------------------------------------------------
<details>
<summary><b>Task 5 :"SMART ULTRASONIC PROXIMITY DETECTOR WITH LED ALERT"  </b> </summary>   
<br>  

https://github.com/user-attachments/assets/b8f7b0cc-caa6-40f3-84d9-da3c9a27a058
</details>




