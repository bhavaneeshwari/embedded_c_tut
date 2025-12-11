### Set or Clear a Specific Bit in a Register
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

### Bit Toggle
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

### Check if K-th Bit is Set
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
