# CPU
* Control Unit 
   * retrieve/decode instructions
   * retrieve/store data in memory

* Execution Unit
    * the actual execution of the instructions happen here

* Registers
    * internal memory locations used as "variables"

* Flags
    * indicate various events during execution


---

## CPU Registers
* General Purpose Registers
    * EAX,EBX,ECX,EDX
    * ESI,EDI
    * ESP,EBP 
* Segment Registers
    * CS,DS,SS,ES,FS,GS
* Control Registers
    * CR0,CR1,CR2,CR3,CR4
* Instruction Pointer Register
    * EIP

---

## Registers explainedS
* EAX => Accumulator Register (storing operands and result dataS)
* EBX => Base Register (pointer to data)
* ECX => Counter Register (loop operations)
* EDX => Data Register (I/O pointer)
* ESI(Source Index)/EDI(Destination Index) => Data Pointer Registers (memory locations)
* ESP => Stack Pointer Register
* EBP => Stack Data POinter Register




Research:
* what are control registers and segment registers
* what does each segment register do
* easier explanation for General Purpose Registers
* put image with EXA,AX,AH,AL

---

# Memory
* every process is laid out in memory in the same virtual space
* every process thinks is alone and taht it enjoys all the memory

PICTURE WITH PROGRAM MEMORY (how the process is stored in memory)

## Stack
* it is LIFO
* from high memory to low memory (why?)
* ESP points to the top of the stack

---

## Virtual Memory Organisation
* find the process ID and look inside the **/proc** directory at the **maps** file for how the memory is organised
* every time a process is started, the segment's virtual addresses are randomised (from linux kernel 2.6) to protect from different buffer overflows