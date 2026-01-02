## In C and C++, char *[] declares an array of pointers to characters (strings). It is commonly used for representing a list of strings, such as command-line arguments in the main function (e.g., char *argv[] or the equivalent char **argv). 
Key Characteristics
Data Structure: It is an array where each element is a pointer of type char *.
Purpose: It is an efficient way to store a list of strings because only the addresses (pointers) are stored in the array, while the actual string content resides elsewhere in memory (e.g., in read-only memory or on the heap).
Memory Management: The memory for the pointers themselves is allocated contiguously, but the strings they point to can be stored in different, non-contiguous memory locations. 
Example in C
A common use case is declaring an array of string literals: 
```c
const char *colors[] = {"Red", "Green", "Blue"};
```
In this example, colors is an array of three pointers to constant characters (const char *).
The string literals themselves ("Red", "Green", "Blue") are stored in a read-only memory segment.
You can access individual characters using double indexing (e.g., colors[0][1] would be 'e').
You can change which string a pointer in the array points to (e.g., colors[0] = "Cyan"; is valid), but you cannot modify the content of a string literal it points to (e.g., colors[0][0] = 'Y'; results in undefined behavior/segmentation fault). 
### Relation to char **
When used as a function parameter, char *[] is functionally identical to char **. This is due to a C language rule called "array decay," where an array name in most expression contexts (including function arguments) decays into a pointer to its first element. In this case, an array of char * decays into a pointer to the first char *, which has the type char **. 
```c
void print_strings(char *list_of_strings[]) { /* ... */ }
// is the same as
void print_strings(char **list_of_strings) { /* ... */ }
```


##  Decode Status Register into Human-Readable Flags
```c
#include <stdio.h>
#include <stdint.h>

const char *flag_names[8] = {
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
    for (int i = 0; i < 8; i++) {
        if ((status_reg >> i) & 1) {
            printf("%s\n", flag_names[i]);
        }
    }
}

int main() {
    uint8_t reg;
    scanf("%hhu", &reg);
    decode_status(reg);
    return 0;
}
```
What is this about?

You’re decoding an 8-bit status register, where each bit tells you whether a system condition is active — like flags from a sensor or peripheral.

Why it’s important in firmware?

Many peripherals return status in register bits
Developers need to interpret bit-level feedback quickly
This maps low-level binary data to user-meaningful outputs
## Solution Logic

# Use a lookup table (flag_names[])
# Shift each bit to LSB, check if set  (status_reg >> i) & 1
Print the corresponding name only if bit = 1

 
### Because %u stands for "unsigned", it well may be uint64_t and is architecture dependent. According to man 3 printf, you may want to use length modifier to get sought behaviour, i.e. %hu (uint16_t) and %hhu (uint8_t).

