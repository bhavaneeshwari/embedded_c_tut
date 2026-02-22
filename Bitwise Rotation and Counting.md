## 25. Count Set Bits in an Integer
Write a C program to count the number of set bits (1s) in the binary representation of an integer N.

Input Format

A single integer N.
Output Format

Print the count of set bits.
Here are the examples for Count Set Bits in an Integer:

 ```c
#include <stdio.h>

int countSetBits(unsigned int n) {
    // Write your code here
    int ans = 0;
    while (n!=0){
    if (n&1 ==1)
    { ans ++;}
     n= n>>1;
    }
return ans ;


}

int main() {
    int n;
    scanf("%d", &n);
    printf("%d", countSetBits(n));
    return 0;
}
```
### 26. Rotate Left in an 8-bit Register
You are given an 8-bit register and a number of positions n. Rotate the register to the left by n bits. The rotation must be circular, meaning the leftmost bits wrap around to the right.

Use 0-based indexing, and return the result as an 8-bit value.
```c
#include <stdio.h>
#include <stdint.h>

uint8_t rotate_left(uint8_t reg, uint8_t n) {
    // Your code here

    uint8_t temp = reg<<n;
    uint8_t wrap = reg >> (8-n);
    reg  = temp | wrap;
    return reg;
}

int main() {
    uint8_t reg, n;
    scanf("%hhu %hhu", &reg, &n);
    printf("%u", rotate_left(reg, n));
    return 0;
}
```
### 27. Rotate Right in a 32-bit Register
You are given a 32-bit hardware register and a number n. Rotate the register to the right by n bits in a circular fashion.
The bits shifted out on the right should reappear on the left.
```c
#include <stdio.h>
#include <stdint.h>

uint32_t rotate_right(uint32_t reg, uint8_t n) {
    // Your code here
    uint32_t temp = reg >>n;
    uint32_t wrap = reg <<(32-n);
    reg = temp|wrap;
    
    return reg;
}

int main() {
    uint32_t reg;
    uint8_t n;
    scanf("%u %hhu", &reg, &n);
    printf("%u", rotate_right(reg, n));
    return 0;
}
```
### 28. Detect Circular Pattern Match
You are given a 16-bit register and a target pattern (also 16-bit). Check if the target pattern can be matched by any circular rotation of the register.
```c
#include <stdio.h>
#include <stdint.h>

uint8_t is_circular_match(uint16_t reg, uint16_t target) {
    // Your code here
    int n =15;
    while (n!=0){
 uint16_t left_cir_match = reg <<n | reg >>(16-n);
 uint16_t rig_cir_match = reg >>n |reg <<(16-n);
   if(left_cir_match==target || rig_cir_match == target)
    return 1;
  n--;
    }
   

    return 0;
}

int main() {
    uint16_t reg, target;
    scanf("%hu %hu", &reg, &target);
    printf("%hhu", is_circular_match(reg, target));
    return 0;
}
```

### 29. Count Set Bits in an 8-bit Register
You are given an 8-bit register. Count how many bits are set to 1 (i.e., high) in the register.
```c
#include <stdio.h>
#include <stdint.h>

uint8_t count_set_bits(uint8_t reg) {
    // Your code here
    uint8_t res =0;
    while(reg){
         res += (reg&1);
         reg >>=1;
    }
       
     
    return res;
}

int main() {
uint8_t reg;
    scanf("%hhu", &reg);
    printf("%u", count_set_bits(reg));
    return 0;
}
```
 ### 30. Check If a Number Is a Power of Two
Write a function to check if a given positive integer is a power of 2. Do not use loops, multiplication, division, or library functions.
You must solve it using bitwise logic only.
```c
#include <stdio.h>
#include <stdint.h>

// Complete the function
const char* is_power_of_two(uint32_t n) {
    // Your logic here
    if(n!=0 && (n&(n-1)) ==0)
    return "YES";
    else
    return "NO";
}

int main() {
    uint32_t n;
    scanf("%u", &n);

    const char* result = is_power_of_two(n);
    printf("%s", result);
    return 0;
}


```
### 31. Bit Reversal in an 8-bit Value
You are given an 8-bit unsigned integer. Your task is to:

Reverse the order of its bits
Print the resulting 8-bit value (in decimal)
You must not use any lookup table or standard library function. Use pure bitwise logic.
```c
#include <stdio.h>
#include <stdint.h>


uint8_t reverse_bits(uint8_t val) {
    // Your logic here
    uint8_t temp =0;
    for (int i=0;i<8;i++)
    {  
        temp =  (temp <<1)| (val&1);
         
        val = val >>1;
       
    }
 
    return  temp;
}

int main() {
    uint8_t val;
    scanf("%hhu", &val);

    uint8_t result = reverse_bits(val);
    printf("%u", result);
    return 0;
}
```

### 32. Compress Interleaved Bits Reverse Bit Spreading
In the previous problem, we interleaved an 8-bit number into a 16-bit value by inserting 0s between each bit. Now your task is to:

Reverse the interleaving process
Extract only the bits from even-numbered positions in a 16-bit number
Reconstruct the original 8-bit value

 ```c
#include <stdio.h>
#include <stdint.h>

uint8_t compress_bits(uint16_t val) {
    // Your logic here
    uint8_t res;
    for(int i =0;i<8;i++)
    {
        uint8_t temp=0;
         temp |= (val>>(2*i))&1;
        res |= temp<<i;
    }
    return res;
}

int main() {
    uint16_t val;
    scanf("%hu", &val);

    uint8_t result = compress_bits(val);
    printf("%u", result);
    return 0;
}

Solving Appro
```

