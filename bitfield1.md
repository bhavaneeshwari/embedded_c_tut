### 17. Clear Specific Bits in a 32-bit Register
You are given a 32-bit control register. Clear a group of bits (set them to 0) starting at a given position and length.

Other bits must stay untouched.


Example 1

Input: reg = 0b1111 1111, pos = 4, len = 4 
Output: 0b0000 1111
```c
#include <stdio.h>
#include <stdint.h>

uint32_t clear_bits(uint32_t reg, uint8_t pos, uint8_t len) {
    // Your code here
    uint32_t mask = 0;
    for (int i =0;i<len;i++)
    {
        mask |= (1<<pos+i);
    }
    reg &= ~(mask) ;
    return reg;
}

int main() {
    uint32_t reg;
    uint8_t pos, len;
    scanf("%u %hhu %hhu", &reg, &pos, &len);
    printf("%u", clear_bits(reg, pos, len));
    return 0;
}
```
## solution 
###  uint32_t mask = ((1U << len) - 1) << pos;

## 18. Replace Bit Field in a 32-bit Register
Given a 32-bit register, replace a few bits (starting at position pos) with a new value.
Only the targeted bits must change — others should stay unchanged.

 
Example 1

Input: reg = 0b1111 1111, val = 0b0000, pos = 4, len = 4  
Output: 0b0000 1111Copy
 ```c
#include <stdio.h>
#include <stdint.h>

uint32_t replace_field(uint32_t reg, uint32_t val, uint8_t pos, uint8_t len) {
    // Your code here
    uint32_t mask =0;
    mask = ((1U<<len)-1) <<pos;
    reg &= ~(mask);// clear 
    val = val &((1U<<len)-1);
    val <<=pos;
    reg |=val;
    return reg;
}

int main() {
    uint32_t reg, val;
    uint8_t pos, len;
    scanf("%u %u %hhu %hhu", &reg, &val, &pos, &len);
    printf("%u", replace_field(reg, val, pos, len));
    return 0;
}
```

## ```c
uint32_t mask = ((1U << len) - 1) << pos;
    reg &= ~mask;

    // Step 2: Shift the new value and OR it into position
    reg |= (val & ((1U << len) - 1)) << pos;
```
