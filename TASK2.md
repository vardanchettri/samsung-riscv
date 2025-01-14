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

