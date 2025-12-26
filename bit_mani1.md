### Set Specific Bits in a 32-bit Register
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
### Keep Only the Highest Set Bit
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


### In embedded systems, modifying specific bits of control or status registers is a frequent task. You’re given an 8-bit register (uint8_t) and must perform the following bit operations on it:

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

### Decode Status Register into Human-Readable Flags
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
#include <stdio.h>
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
