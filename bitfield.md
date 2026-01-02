### 14. Extract the Nibble from an 8-bit Register
Write a C program to extract a nibble (4-bit value) from an 8-bit register.

The user provides an 8-bit integer (register value) and a nibble position (0 for lower nibble, 1 for upper nibble).
Your task is to extract and print the nibble’s decimal value.
Input Format

An 8-bit integer (0-255) representing the register value.
A nibble position (0 for lower, 1 for upper).
Output Format

The extracted 4-bit value (0-15).
```c
#include <stdio.h>

unsigned char extractNibble(unsigned char reg, int pos) {
    // Write your code here
   
    if (pos)
   { return (reg>>4);}
    else 
    { return reg & 0x0f;}
     
}

int main() {
    unsigned char reg;// 8bit 1 byte 
    int pos;
    scanf("%hhu %d", &reg, &pos);
    printf("%hhu", extractNibble(reg, pos));
    return 0;
}
```
