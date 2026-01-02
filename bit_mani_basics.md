## the ability to manipulate individual bits will become useful or even necessary

Saving memory by packing up to 8 true/false data values in a single byte.
Turning on/off individual bits in a control register or hardware port register.
Performing certain arithmetic operations involving multiplying or dividing by powers of 2.
### bitwise and 
## One of the most common uses of bitwise AND is to select a particular bit (or bits) from an integer value, often called masking.
For example, if you wanted to access the least significant bit in a variable x, and store the bit in another variable y
```c
int x = 5;       // binary: 101
    int y = x & 1;   // now y == 1
    x = 4;           // binary: 100
    y = x & 1;       // now y == 0
```
### bitwise or
 The bitwise OR of two bits is 1 if either or both of the input bits is 1, otherwise it is 0
<img width="1650" height="761" alt="image" src="https://github.com/user-attachments/assets/e0f38431-071b-4c89-9ece-37cbfc5c0878" />

 ### bitwise xor
for toggling operations

```c
int x = y^1; // toggles the lsb bit 
```

### bitwise not 
As an aside, it is interesting to note that for any integer x, ~x is the same as -x-1.
<img width="492" height="272" alt="image" src="https://github.com/user-attachments/assets/794384a5-a5cb-44d4-a5e6-dc27880d77fc" />


<img width="1555" height="581" alt="image" src="https://github.com/user-attachments/assets/9e7cf037-380f-4b73-93cb-63b1567ec9bf" />
### bitwise shift 

<img width="1715" height="831" alt="image" src="https://github.com/user-attachments/assets/5068930f-face-4096-b43e-196f3d0e0235" />
```c
int a = 5;        // binary: 0000000000000101
    int b = a << 14;  // binary: 0100000000000000 - the first 1 in 101 was discarded

```

### unsigned chars as the data type which can store numbers from 0 - 255. The %hhu format specifier is for unsigned chars:
An unsigned char is guaranteed to store a non-negative value from 0 to 255.
A signed char is guaranteed to store a value in the range from -128 to 127.
##  8-bit integer (0-255)
### declare the variable as unsigned char 

