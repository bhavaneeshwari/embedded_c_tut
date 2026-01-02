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
### 15. Set Multiple Bits in 8-bit Register
You are given an 8-bit register. Set all bits between position start and end (inclusive).

Use 0-based indexing and assume start <= end.


Example 1

Input: reg = 0b00000000, start = 1, end = 3 
Output: 0b00001110Copy
 ```c
#include <stdio.h>
#include <stdint.h>

uint8_t set_range(uint8_t reg, uint8_t start, uint8_t end) {
    // Your code here
    
        for (int i =0;i<=end-start;i++){
         reg |= (1<< start+i);
        }
     
    
    
    return reg;
}

int main() {
    uint8_t reg, start, end;
    scanf("%hhu %hhu %hhu", &reg, &start, &end);
    printf("%u", set_range(reg, start, end));
    return 0;
}
```

## The C expression uint8_t mask = ((1 << (end - start + 1)) - 1) << start; generates a bitmask within an 8-bit unsigned integer type with a contiguous sequence of 1s between the bit positions specified by start and end, inclusive.
<img width="913" height="684" alt="image" src="https://github.com/user-attachments/assets/b29056c1-5a62-400f-9a04-b4680520a3b8" />


## 16. Extract a Bit Field from a 32-bit Register
You are working with a 32-bit hardware status register. Extract a few bits from it, starting from a given bit position and covering a given length. Return the extracted value as an unsigned integer.


Use 0-based indexing (LSB = position 0).


Example 1

Input: reg = 0b1011 0110 0111 0000 0000 0000 0000 0000, pos = 28, len = 4 
Output: 0b1011Copy
```c
#include <stdio.h>
#include <stdint.h>

uint32_t extract_field(uint32_t reg, uint8_t pos, uint8_t len) {
    // Your code here
    uint32_t mask =((1<<(len))-1) ;
    reg  >>=pos;
    return reg &=mask ;
}

int main() {
    uint32_t reg;
    uint8_t pos, len;
    scanf("%u %hhu %hhu", &reg, &pos, &len);
    printf("%u", extract_field(reg, pos, len));
    return 0;
}
```
