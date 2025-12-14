### Control Register Using Nested Bitfields
You are given a control register represented using nested struct bitfields. The register is 8-bit wide and divided into the following layout:

Bits	Field	Description
0	enable	1 = ON, 0 = OFF
1	mode	0 = Normal, 1 = Sleep
2–3	priority	2-bit value (0–3)
4–7	reserved	Reserved (must be 0)

Your task is to:

Simulate this register using nested struct and bitfields
Implement a function that takes a pointer to the register and validates:
enable must be 1
priority must be less than or equal to 2
reserved must be all 0s
Return 1 if valid, else return 0.

 ```c
#include <stdio.h>

typedef union {
    unsigned char reg;
    struct {
        unsigned char enable : 1;
        unsigned char mode : 1;
        unsigned char priority : 2;
        unsigned char reserved : 4;
    } bits;
} ControlRegister;

// Write your logic here
int validate_register(ControlRegister *ctrl) {

    ControlRegister res=*ctrl;
    if ((res.bits.enable == 1)&&(res.bits.priority<=2)&&(res.bits.reserved==0))
   { return 1;}
    else {return 0;}
    
}

int main() {
    ControlRegister ctrl;// typedef union and its object to store the value in reg
    scanf("%hhx", &ctrl.reg);

    int result = validate_register(&ctrl);// address of the the union;
    printf("%d", result);

    return 0;
}
```
