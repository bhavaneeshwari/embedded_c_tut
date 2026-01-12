## 21. Data Transmission
You are preparing a 32-bit value to send over a communication bus. To ensure compatibility across platforms, you must convert the value into 4 bytes (big-endian order) and store them into a byte array.

 
Example 1

Input: value = 0x12345678
Output: arr[0] = 0x12, arr[1] = 0x34, arr[2] = 0x56, arr[3] = 0x78
```c
#include <stdio.h>
#include <stdint.h>

void convert_to_big_endian(uint32_t value, uint8_t arr[4]) {
    // Your code here
    
arr[3]=(value)&0xffff ;
arr[2]=(value>>8)&0xffff ;
arr[1]=(value>>16)&0xffff;
arr[0]=(value>>24)&0xffff;



    
}

int main() {
    uint32_t value;
    uint8_t arr[4];
    scanf("%u", &value);
    convert_to_big_endian(value, arr);
    for (int i = 0; i < 4; i++) {
        printf("%u", arr[i]);
        if(i<3){
            printf(" ");
        }
    }
    return 0;
}
```

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
