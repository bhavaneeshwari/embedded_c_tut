### Add Two Integers Using Void Pointers
Write a function that receives two void pointers, each pointing to an integer. Return sum of the two integer.

Note: Function arguments are passed as void * and can’t be changed.
```c
#include <stdio.h>

int add_two_void_pointers(void *a, void *b) {
    int n1 = *(int *)a;
    int n2 =*(int *)b;
    int sum =n1+n2;
    return sum;
}

int main() {
    int x, y;
    scanf("%d %d", &x, &y);

    int result = add_two_void_pointers(&x, &y);
    printf("%d", result);

    return 0;
}

```

### Function Pointer Dispatch Table
You are building a simple math command handler. You are given two integers and a command code:

0 → Add
1 → Subtract
2 → Multiply
3 → Divide (integer division, assume non-zero)
 

Your task:

Create an array of function pointers, each pointing to one of the above operations.
Based on the command code, use the function pointer to invoke the correct operation.
Return the result.

### // Array initialization with function addresses int (*math_ops[3])(int, int) = {add, subtract, multiply};

```c
#include <stdio.h>

int add(int a, int b) { return a + b; }
int sub(int a, int b) { return a - b; }
int mul(int a, int b) { return a * b; }
int divide(int a, int b) { return a / b; }

int execute_command(int a, int b, int cmd) {
    
int res;
int (*fp[4])(int,int)={add,sub,mul,divide};// array off function pointers
    
     res =(*fp[cmd])(a,b);
     return res;
}

int main() {
    int a, b, cmd;
    scanf("%d %d %d", &a, &b, &cmd);

    int result = execute_command(a, b, cmd);
    printf("%d", result);

    return 0;
}
```

### State Machine Using Function Pointers
You are simulating a system boot-up sequence using function pointers. 

There are 4 states:

void state_init()    { printf("Init"); }
void state_load()    { printf("Load"); }
void state_execute() { printf("Execute"); }
void state_exit()    { printf("Exit"); }Copy
Your Task

Implement the function run_state_sequence(int start)
It should execute three states in sequence, starting from the given start index:
If start = 1 → print Load, Execute, Exit
If start = 3 → wrap around → print Exit, Init, Load

```c
#include <stdio.h>

void state_init()    { printf("Init"); }
void state_load()    { printf("Load"); }
void state_execute() { printf("Execute"); }
void state_exit()    { printf("Exit"); }

// Your logic here
void run_state_sequence(int start) {
    // Implement using function pointer array
           void (*fp[4])()={state_init,state_load,state_execute,state_exit};
            
    
 
        for (int i =0;i<3;i++) // to print exactly three states 
        {    int wrap = (start+i)%4; //wrap condtion if start index is other than zeo then we can use wrap around
            (*fp[wrap])();

            printf("\n");
            
        }
    
}

int main() {
    int start;
    scanf("%d", &start);
    run_state_sequence(start);
    return 0;
}
```

### Simulate memcpy function Using Pointer Walk
You are given two memory buffers:

A source array of n integers
A destination array of the same size (pre-allocated, uninitialized)
Your task:

Implement the function simulate_memcpy() to copy all elements from the source to destination
```c
#include <stdio.h>

void simulate_memcpy(int *dest, int *src, int n) {
    // Your logic here
    for (int i =0;i<n;i++)
    {
        *(dest+i)=*(src+i); // pointer arithmetic to traversal the elements
    }

}

int main() {
    int n;
    scanf("%d", &n);

    int src[100], dest[100];

    for (int i = 0; i < n; i++) {
        scanf("%d", &src[i]);
    }

    simulate_memcpy(dest, src, n);

    for (int i = 0; i < n; i++) {
        printf("%d", dest[i]);
        if(i < n-1){
           printf(" "); 
        }
    }

    return 0;
}

```

###  Scan Memory for Three Consecutive Increasing Values
You are given a block of memory (as an integer array) of size n.

Your task is to write a function that scans the memory using pointers and detects the first occurrence of three consecutive increasing integers — for example: [4, 5, 6] or [10, 11, 12].

Return the starting index of the first such pattern. If no such pattern is found, return -1.You must use pointer logic only, not array indexing.

```c
#include <stdio.h>

int find_pattern(int *mem, int n) {
    // Write your pointer-based logic here
    for(int i =0; i<n;i++)
    {
      int  a =*(mem+i);
       int b=*(mem+i+1);
       int c=*(mem+i+2);
       if (a == b-1 && a==c-2)
       {
        return i;
       }
    }
    return -1;
}

int main() {
    int n, arr[100];
    scanf("%d", &n);

    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    int res = find_pattern(arr, n);
    printf("%d", res);

    return 0;
}
```

### Detect Alternating Pattern
You are given a memory block as an integer array of size n. 

Your task is to check if a segment of size k starting from the beginning of the array follows an alternating pattern — e.g., 1 0 1 0 ... or 0 1 0 1 ....

Return:

1 if the segment follows an alternating pattern
0 if not
You must use pointer arithmetic only, not array indexing.

```c
#include <stdio.h>

int is_alternating_pattern(int *mem, int k) {
    // Write your pointer logic here
    for (int i =0; i<k;i++)
    {
        int a = *(mem+i);
        int b = *(mem+i+2)%6;
       if (a == b) {return 1;}
       else return 0;
    }
   
}

int main() {
    int n, k, arr[100];
    scanf("%d %d", &n, &k);

    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    int res = is_alternating_pattern(arr, k);
    printf("%d", res);

    return 0;
}
```

### Event-Based Triggers Using Function Pointer Array
You are building a simple event handling system where different event codes (0 to 4) trigger different actions.

Each event type corresponds to a specific function:

Event Code	Trigger Type	Function
0	Button Press	on_button()
1	Timer Expire	on_timer()
2	UART Received	on_uart()
3	Power On	on_power()
4	Error Detected	on_error()
You must:

Implement a function pointer array
Trigger the correct function based on the input event code
If the code is outside the 0–4 range, print "Unhandled Event"
 ```c
#include <stdio.h>

void on_button() {
    printf("Button Pressed");
}
void on_timer() {
    printf("Timer Expired");
}
void on_uart() {
    printf("UART Received");
}
void on_power() {
    printf("Power On");
}
void on_error() {
    printf("Error Detected");
}

// Write your event dispatcher logic here
void handle_event(int event_code) {
    void (*fp[5])()={on_button,on_timer,on_uart,on_power,on_error};
    if (event_code>=0 && event_code<5)
    {
       (*fp[event_code]) ();
    }
    else printf("Unhandled Event");
}

int main() {
    int event;
    scanf("%d", &event);
    handle_event(event);
    return 0;
}

```

### void pointer and Casting
You are writing a utility function that adds two values — but the values can be either:

int, or
float
You will be given void* pointing to the first and second value and a char type specifier: 'i' for int, 'f' for float.

Your task is to:

Cast the void* to appropriate type based on the specifier
Perform the addition
Print the result (as integer or float)
Use proper void* casting and dereferencing logic

```c
#include <stdio.h>

void add_and_print(void *a, void *b, char type) {
    // Write your logic here using type casting
    if (type == 'i')
    {
        int n1 = *(int*)a;
        int n2 = *(int*)b;
        int sum = n1+n2;
        printf("%d",sum);

    }
    else if (type =='f')
    {
        float n1 =*(float*)a;
        float n2 =*(float*)b;
        printf("%.1f",n1+n2);
    }
}

int main() {
    char type;
    scanf(" %c", &type);

    if (type == 'i') {
        int x, y;
        scanf("%d %d", &x, &y);
        add_and_print(&x, &y, type);
    } else if (type == 'f') {
        float x, y;
        scanf("%f %f", &x, &y);
        add_and_print(&x, &y, type);
    }

    return 0;
}
```
