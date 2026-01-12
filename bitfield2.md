## 22. Pack Multiple Fields into a 16-bit Control Register
In embedded systems, multiple configuration fields are often packed into a single register using bit-level operations.

You are given the following field specifications to be packed into a 16-bit control register:

Field	Bits	Position (LSB-first)
Mode	3	Bits 0–2
Speed	5	Bits 3–7
Reserved	2	Bits 8–9 (must be 0)
Status	6	Bits 10–15
Your task is to:

Read mode, speed, and status from input
Pack them into a uint16_t register following the given bit layout
Ensure reserved bits (8–9) remain 0
Print the resulting packed value
```c
#include <stdio.h>
#include <stdint.h>

uint16_t pack_register(uint8_t mode, uint8_t speed, uint8_t status) {
    // Your logic here
    uint16_t reg;
    
     reg =  mode |reg;
 reg = ((speed&0x001f)<<3)|  reg&(~(((1<<5)-1)<<3)) ;

 reg =  ((status&0x003f)<<10) |  reg&(~(((1<<6)-1)<<10)) ;

     reg  =    reg&(~(((1<<2)-1)<<8)) ;
    return reg;
}

int main() {
    uint8_t mode, speed, status;
    scanf("%hhu %hhu %hhu", &mode, &speed, &status);

    uint16_t reg = pack_register(mode, speed, status);
    printf("%u", reg);
    return 0;
}
```

## 23. Extract and Modify Field in a 32-bit Register
In embedded systems, a 32-bit configuration register often contains several packed fields. 

Your task is to extract a 5-bit field located at bit positions 10 to 14 from a 32-bit register value. 

If this field’s value is less than 31, increment it by 1. Then write the updated value back to the same bit positions in the register, leaving all other bits unchanged.

Use only bitwise operations to extract, modify, and update the register.

Bit layout example (bit 0 is LSB):

Register: [31 ... 15 | 14 13 12 11 10 | 9 ... 0]
                        ↑  ↑  ↑  ↑  ↑ (target field)

```c
#include <stdio.h>
#include <stdint.h>

uint32_t update_register(uint32_t reg) {
    // Your logic here
    uint32_t ans ;
    
uint32_t mask =0x00007C00;
ans = reg & mask;
uint32_t temp = (ans >>10)&(0x0000001f);
    if(temp < 0x0000001f)
       
       {temp +=0x00000001; // i did bitwise or didnt reallize my mistake 
       } 
       reg &= ~(mask);
       reg |=(temp<<10);
    return reg;
}

int main() {
    uint32_t reg;
    scanf("%u", &reg);
    uint32_t updated = update_register(reg);
    printf("%u", updated);
    return 0;
}
```
