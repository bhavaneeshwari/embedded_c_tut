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

##  alternate 
```c
uint32_t mask = ((1U << len) - 1) << pos;
    reg &= ~mask;

    // Step 2: Shift the new value and OR it into position
    reg |= (val & ((1U << len) - 1)) << pos;
```

## 19. Extract Even Bits Only from 32-bit Register
From a 32-bit register, extract all even-positioned bits (0, 2, 4, …, 30).
Return the compressed value formed by only these bits (shifted to be consecutive).


Example 1

Input: reg = 0b0101 0101 
Output: 0b1111

```c
#include <stdio.h>
#include <stdint.h>

uint32_t extract_even_bits(uint32_t reg) {
    // Your code here
    uint32_t new_t=0;
 
    for (int i =0;i<16;i++)

    {    int pos = i*2;
      
       uint32_t out =  (reg>>pos)&1;
      
        new_t |= out<<i;
    }

    return new_t;
}

int main() {
    uint32_t reg;
    scanf("%u", &reg);
    printf("%u", extract_even_bits(reg));
    return 0;
}
```

## 20. Set Baud Rate Field in Control Register
You are working with a 32-bit UART control register. The baud rate is controlled by 4 bits located at position 8 (i.e., bits 8 to 11). 
Write a function to update the baud rate field with a new 4-bit value. All other bits in the register must remain unchanged.


Example 1

Input: reg = 0b0000 0000 0000 0000 0000 0000 0000 0000, baud = 0b1010  
Output: 0b0000 0000 0000 0000 0000 1010 0000 0000

```c
#include <stdio.h>
#include <stdint.h>

uint32_t set_baud_rate(uint32_t reg, uint8_t baud) {
    // Your code here

    uint32_t mask =0;
    mask = ((1U<<4)-1) <<8;
    reg &= ~(mask);// clear 
    uint32_t val =0;
      val = val | baud ;
      val<<=8;
    reg |=val;

    return reg;
}

int main() {
    uint32_t reg;
    uint8_t baud;
    scanf("%u %hhu", &reg, &baud);
    printf("%u", set_baud_rate(reg, baud));
    return 0;
}
```
