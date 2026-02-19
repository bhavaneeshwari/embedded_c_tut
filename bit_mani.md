# Bitwise Operations
### 1 Set or Clear a Specific Bit in a Register
Write a C program to set or clear a specific bit in an 8-bit register based on user input.

The user provides an 8-bit integer (register value), a bit position (0-7), and a mode (0 for clear, 1 for set).
Your task is to modify the register value accordingly and print the updated value.
 

Input Format

An 8-bit integer (0-255) representing the register value.
An integer (0-7) representing the bit position.
An integer (0 or 1) representing the operation (1 to set, 0 to clear the bit).
Output Format

The modified register value after setting/clearing the bit.

```c
#include <stdio.h>

unsigned char modifyBit(unsigned char reg, int pos, int mode) {
    // Write your code here
    unsigned char a;
    if(mode ==0)
    {
        //clear 
        a = reg & ~(1<<pos);
       return a;
    }
    else if(mode ==1 )
    {
        a = reg | (1<<pos);
        return a;
    }
}

int main() {
    unsigned char reg;
    int pos, mode;
    scanf("%hhu %d %d", &reg, &pos, &mode);
    printf("%d", modifyBit(reg, pos, mode));
    return 0;
}
```

### 2 Bit Toggle
Write a C program to toggle the 5th bit (0-based index) of a given integer.

The program should take an integer N as input.
It should toggle the 5th bit of N (i.e., flip the bit at position 5: if 0, make it 1; if 1, make it 0).
Note: The 5th bit is at position 5(0-based indexing). For example, in the binary number 100100, the 5th bit is 1.

```c
#include <stdio.h>

int toggleFifthBit(int n) {
    // Write your code here

    int res = n ^ (1<<5);
    return res;
}

int main() {
    int n;
    scanf("%d", &n);
    printf("%d", toggleFifthBit(n));
    return 0;
}
```

### 3 Check if K-th Bit is Set
Write a C program to check if the K-th bit (0-based index) of an integer N is set (1) or not (0).

Input Format

Two integers N and K.
Output Format

Print 1 if the K-th bit of Integer N is set (1), otherwise print 0.
```c
 #include <stdio.h>

int isKthBitSet(int n, int k) {
    // Write your code here

    int res = n & (1<<k);
    if (!res)
    {return 0;}
    else return 1;
}

int main() {
    int n, k;
    scanf("%d %d", &n, &k);
    printf("%d", isKthBitSet(n, k));
    return 0;
}
```

### 4. Set the Bit in an 8-bit Register
You are working with an 8-bit control register. Write a function to set the bit at a given position without affecting other bits.

Use 0-based indexing for bit positions (0 = LSB, 7 = MSB).
```c
#include <stdio.h>
#include <stdint.h>

uint8_t set_bit(uint8_t reg, uint8_t pos) {
    reg = reg | 1<<pos;
    return reg;
}

int main() {
    uint8_t reg, pos;
    scanf("%hhu %hhu", &reg, &pos);  // Accept register value and position
    uint8_t result = set_bit(reg, pos);
    printf("%u", result);         // Output the result as an integer
    return 0;
}
```

### 5. Clear the Bit in an 8-bit Register
You are working with an 8-bit control register. Write a function to clear (set to 0) the bit at a given position without affecting other bits.

Use 0-based indexing for bit positions (0 = LSB, 7 = MSB).

```c
#include <stdio.h>
#include <stdint.h>

uint8_t clear_bit(uint8_t reg, uint8_t pos) {
    // Your code here
    reg =reg & ~(1<<pos);
    return reg;
}

int main() {
    uint8_t reg, pos;
    scanf("%hhu %hhu", &reg, &pos);
    uint8_t result = clear_bit(reg, pos);
    printf("%u", result);
    return 0;
}
```
### 6. Toggle the Bit in an 8-bit Register
In your firmware, you want to toggle a specific bit in an 8-bit register. Toggle means to invert the bit: if 1 → 0, and if 0 → 1.
Use 0-based indexing for bit positions (0 = LSB, 7 = MSB).
 ```c
#include <stdio.h>
#include <stdint.h>

uint8_t toggle_bit(uint8_t reg, uint8_t pos) {
    // Your code here
    reg = reg ^ 1<<pos;
    return reg;
}

int main() {
    uint8_t reg, pos;
    scanf("%hhu %hhu", &reg, &pos);
    uint8_t result = toggle_bit(reg, pos);
    printf("%u", result);
    return 0;
}
```
### 7. Is the Bit Set
Given an 8-bit register, check whether the bit at a specific position is set (i.e., equals 1).

Return 1 if the bit is set, otherwise return 0.
```c
#include <stdio.h>
#include <stdint.h>

uint8_t is_bit_set(uint8_t reg, uint8_t pos) {
    // Your code here
    reg = reg>>pos;
    if(reg & 0b00000001)
 return 1;

    return 0;
}

int main() {
    uint8_t reg, pos;
    scanf("%hhu %hhu", &reg, &pos);
    printf("%u", is_bit_set(reg, pos));
    return 0;
}

```

### 8. Set Specific Bits in a 32-bit Register
You are working with a 32-bit configuration register. Set a few bits starting from a given position and covering a specific length. The bits must be set to 1 (ON), without affecting other bits in the register.

Use 0-based indexing.
```c
#include <stdio.h>
#include <stdint.h>

uint32_t set_bits(uint32_t reg, uint8_t pos, uint8_t len) {
    // Your code here
    for (int i = 0;i<len;i++)
    { reg = reg | (1<<pos+i);}
   
    return reg;
}

int main() {
    uint32_t reg;
    uint8_t pos, len;
    scanf("%u %hhu %hhu", &reg, &pos, &len);
    printf("%u", set_bits(reg, pos, len));
    return 0;
}
```
### 9. Keep Only the Highest Set Bit
You are given a 16-bit register (uint16_t).
Your task is to:

Return a value where only the highest (leftmost) set bit is retained
All other bits must be cleared
```c
#include <stdio.h>
#include <stdint.h>

// Complete the function
uint16_t highest_set_bit(uint16_t reg) {
    // Your logic here
     int max =0;
for(int n =0;n<16;n++){
   
    if(reg & (1<<n))// to check n bit set 
     
      if(max <n) max =n; //update the max with set bit position
      else max =max;
    

}
   if (reg ==0 ) return reg;
   else
    reg = reg&0x0000;
    reg =reg| (1<<max);
    return reg;
}

int main() {
    uint16_t reg;
    scanf("%hu", &reg);

    uint16_t result = highest_set_bit(reg);
    printf("%hu", result);
    return 0;
}
```

### 10. Bit Operations using Macros
In embedded systems, modifying specific bits of control or status registers is a frequent task. You’re given an 8-bit register (uint8_t) and must perform the following bit operations on it:

Set bits 2 and 7
Clear bit 3
Toggle bit 5
Your task is to implement a function that:

Accepts a uint8_t reg as input
Applies all the above operations in the given order
Returns the updated register value
Use proper bitwise macros for maintainability.

```c
#include <stdio.h>
#include <stdint.h>

// Define bitwise macros here
#define SET(r,b)  ((r)|=(1<<(b)))
#define CLEAR(r,b) ((r)&=~(1<<(b)))
#define TOGG(r,b) ((r)^=(1<<(b)))

uint8_t modify_register(uint8_t reg) {
    // Apply operations in order

   SET(reg,2);
   SET(reg,7);
   CLEAR(reg,3);
   TOGG(reg,5);
    return reg;
}

int main() {
    uint8_t reg;
    scanf("%hhu", &reg);
    printf("%u", modify_register(reg));
    return 0;
}
```
### 11. Decode Status Register into Human-Readable Flags
In embedded systems, status registers often represent multiple flags using each bit. You are given an 8-bit status register. Each bit corresponds to a different condition.

Bit-to-Flag Mapping

Bit	Meaning
0	Power On
1	Error
2	Tx Ready
3	Rx Ready
4	Overheat
5	Undervoltage
6	Timeout
7	Reserved
You must write a function that:

Accepts a uint8_t status_reg
Decodes which flags are set (bits = 1)
Prints only the enabled flag names, one per line, in the order of bits from LSB to MSB (0 to 7)
```c
#include <stdint.h>





const char*name[]={
     "Power On",

        "Error",

        "Tx Ready",

        "Rx Ready",

        "Overheat",

        "Undervoltage",

        "Timeout",

        "Reserved"
};
   
void decode_status(uint8_t status_reg) {
    // Your logic here
    
for (int n =0;n<8;n++)
{
    if(status_reg&(1<<n))
    
    printf("%s\n",name[n]);
   
}

}

int main() {
    uint8_t reg;
    scanf("%hhu", &reg);
    decode_status(reg);
    return 0;
}
```

### 12. Bit Spreading Interleave Bits with Zeros
In some protocols or hardware applications (e.g. graphic rendering, signal encoding), bit spreading or interleaving is used to insert 0s between the bits of a value for purposes like data alignment or transmission.

You are given an 8-bit number, and your task is to:

Spread the bits such that each bit is followed by a 0
The result will be a 16-bit number where each original bit occupies even positions (0, 2, 4…)
All odd positions are 0s 
```c
#include <stdio.h>
#include <stdint.h>

uint16_t spread_bits(uint8_t val) {
    // Your logic here
    uint16_t res =0X0000;
    
    
        for (int i=0;i<8;i++)
        {
            uint8_t bit = (val>>i)&1;
             res = res | (bit<<(2*i));
        }
       

  
    return res;
}

int main() {
    uint8_t val;
    scanf("%hhu", &val);

    uint16_t result = spread_bits(val);
    printf("%u", result);
    return 0;
}
```

### 13. Macro-Based Register Config Helper
In embedded systems, registers are often configured by setting specific bits. To make the code cleaner and reusable, firmware developers use macros to set fields in a register.

You are given a 16-bit control register layout:

Field	Bits	Position (LSB-first)
ENABLE	1	Bit 0
MODE	2	Bits 1–2
SPEED	3	Bits 3–5
RESERVED	2	Bits 6–7 (must be 0)
Your task is to:

Write macros to:
Set the ENABLE bit
Set the MODE field
Set the SPEED field
Read ENABLE, MODE, SPEED from input
Use the macros to pack a final 16-bit register value
RESERVED bits (6–7) must be left 0
```c

// Define macros here
#define SET(r,b) ((r)|=((b)<<0))
#define ENA(r,b)  ((r)|=((b)<<1))
#define SPEED(r,b) ((r)|=((b)<<3))

uint16_t build_register(uint8_t enable, uint8_t mode, uint8_t speed) {
    // Use macros to set fields
    uint8_t reg =0;
    SET(reg, enable);
    ENA(reg,mode);
    SPEED(reg,speed);
    return reg;
}

int main() {
    uint8_t enable, mode, speed;
    scanf("%hhu %hhu %hhu", &enable, &mode, &speed);

    uint16_t reg = build_register(enable, mode, speed);
    printf("%u", reg);
    return 0;
}
```
