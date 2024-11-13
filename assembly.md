## Assembly Table

## Instruction Address Register
Loads instructions from the RAM into the CONTROL UNIT.  
4 Higher Bits -> Action to perform.  
4 Lower Bits -> Accessing common Registers, or Flags 

|__IAR__|0|0|0|0|0|0|0|0|
|:-----------:|--|--|--|--|--|--|--|--|
|__*Register  A*__|||||-|-|||
|*REG 0* |||||0|0|||
|*REG 1* |||||0|1|||
|*REG 2* |||||1|0|||
|*REG 3* |||||1|1|||
|__*Register  B*__|||||||-|-|
|*REG 0* |||||||0|0|
|*REG 1* |||||||0|1|
|*REG 2* |||||||1|0|
|*REG 3* |||||||1|1|

### Instructions
- LOAD - Load contents from RAM Address at RA into RB  

|__*LD*__|0|0|0|0|RAH|RAL|RBH|RBL|
|:-------:|--|--|--|--|--|--|--|--|


- STORE - Store content from RAM Address at RA  into RB

|__*ST*__|0|0|0|1|RAH|RAL|RBH|RBL|
|:-------:|--|--|--|--|--|--|--|--|

- DATA - Load 8 bits from the next RAM Address into RB

|__*DATA*__|0|0|1|0|n/a|n/a|RBH|RBL|
|:-------:|--|--|--|--|--|--|--|--|

- JUMP REGISTER - Jump To Address in RB

|__*JMPR*__|0|0|1|1|n/a|n/a|RBH|RBL|
|:-------:|--|--|--|--|--|--|--|--|

- JUMP ADDRESS - Jump To next byte in RAM

|__*JMP ADDR*__|0|1|0|0|n/a|n/a|n/a|n/a|
|:-------:|--|--|--|--|--|--|--|--|

- JUMP IF - Jump to address in next RAM location if FLAG is set
    - Flags
        - C - Carry in
        - A - A Larger
        - E - Equal
        - Z - Zero
    - Jumps
        - JZ    - 
        - JE    -
        - JEZ   -
        - JA    -
        - JAZ   -
        - JAE   -
        - JAEZ  -
        - JC    -
        - JCZ   -
        - JCE   -
        - JCEZ  -
        - JCA   -
        - JCAZ  -
        - JCAE  -
        - JCAEZ -

|__*J---*__  |0|1|0|1|C|A|E|Z|
|:---------:|--|--|--|--|--|--|--|--|
|*JZ*       |0|1|0|1|0|0|0|1|
|*JE*       |0|1|0|1|0|0|1|0|
|*JEZ*      |0|1|0|1|0|0|1|1|
|*JA*       |0|1|0|1|0|1|0|0|
|*JAZ*      |0|1|0|1|0|1|0|1|
|*JAE*      |0|1|0|1|0|1|1|0|
|*JAEZ*     |0|1|0|1|0|1|1|1|
|*JC*       |0|1|0|1|1|0|0|0|
|*JCZ*      |0|1|0|1|1|0|0|1|
|*JCE*      |0|1|0|1|1|0|1|0|
|*JCEZ*     |0|1|0|1|1|0|1|1|
|*JCA*      |0|1|0|1|1|1|0|0|
|*JCAZ*     |0|1|0|1|1|1|0|1|
|*JCAE*     |0|1|0|1|1|1|1|0|
|*JCAEZ*    |0|1|0|1|1|1|1|1|

- CLEAR FLAGS- Clear All Flags

|__*CLF*__|0|1|1|0|0|0|0|0|
|:-------:|--|--|--|--|--|--|--|--|

- ALU - Performs operations with the Registers  

ADD - Addition  
SHR - Shift Right  
SHL - Shift Left  
NOT - NOT Operator   
AND - AND Operator  
OR  - OR Operator  
XOR - XOR Operator  
CMP - Comparision Operator  

|__*ALU*__|1|-|-|-|RAH|RAL|RBH|RBL|
|:-------:|--|--|--|--|--|--|--|--|
|*ADD*   |1|0|0|0|RAH|RAL|RBH|RBL|
|*SHR*   |1|0|0|1|RAH|RAL|RBH|RBL|
|*SHL*   |1|0|1|0|RAH|RAL|RBH|RBL|
|*NOT*   |1|0|1|1|RAH|RAL|RBH|RBL|
|*AND*   |1|1|0|0|RAH|RAL|RBH|RBL|
|*OR*    |1|1|0|1|RAH|RAL|RBH|RBL|
|*XOR*   |1|1|1|0|RAH|RAL|RBH|RBL|
|*CMP*   |1|1|1|1|RAH|RAL|RBH|RBL|

- END - End of the program

|__*END*__|1|1|0|0|1|1|1|1|
|:-------:|--|--|--|--|--|--|--|--|
