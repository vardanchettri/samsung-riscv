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




