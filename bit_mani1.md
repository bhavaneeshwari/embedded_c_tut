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
