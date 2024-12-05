# subleq_bit-reversal_CPU
A SUBLEQ (subtract and branch if less than or equal to zero) based CPU Verilog implementation

This CPU design implements the theoretical CPU described by [this paper](https://janders.eecg.toronto.edu/pdfs/esl.pdf). The CPU has two instructions: SUBLEQ and SUBLEQ-, where SUBLEQ- is a bit-reversal version of the standard SUBLEQ instruction. The supposed benefits of such a design include those of a One Instruction Set Architecture (OISA) and the speed boost from the included second instruction type (SUBLEQ-) that improves certain higher-complexity operations which are normally inefficient in instruction-count with the SUBLEQ instruction alone.

Instruction operation:
```
Bit reversal: brev[A], where A = n-bit binary big-endian number
return (A converted to little-endian)

SUBLEQ A B C
mem[B] = mem[B] - mem[A]
if(mem[B] <= 0):
  goto mem[C]

SUBLEQ- A B C
mem[B] = brev[brev[mem[B]] - brev[mem[A]]]
if(mem[B] <= 0):
  goto mem[C]
```
