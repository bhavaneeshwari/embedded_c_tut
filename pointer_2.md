### Find Maximum Element Using Pointer Walk
You are given an array of integers and its size n.
Using only pointer arithmetic:

Traverse the array
Find and print the maximum element in the array.

```c
#include <stdio.h>
#include<limits.h>
int find_max_element(int *ptr, int n) {
    int max=INT_MIN;
    for(int i =0; i<n;i++)
    {
        if( max<*(ptr+i))
        {
            max=*(ptr+i);
        }
    }
   
    return max;
}

int main() {
    int n;
    scanf("%d", &n);

    int arr[100];
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    int result = find_max_element(arr, n);
    printf("%d", result);

    return 0;
}
```


### Double Pointer
You are given two integer variables: n1 and n2.

Task:

Initially, a pointer points to n1.
Pass the address of this pointer (int **pp) to a function.
Inside the function, decide:
If the value at pointer is even, reassign it to point to n2.  
### int * n1_ptr =*pp; //first deferencing double pointer to get address of n1_ptr;
### int val = *n1_ptr; // now deference n1 pointer to get that value stored in that address 
### val is even then *pp double pointer get the &n2_ptr address
If the value is odd, keep pointing to n1.
Finally, print the value where pointer points.

```c
#include <stdio.h>

void reassign_based_on_value(int **pp, int *n2_ptr) {
   
   int *n1_ptr= *pp; // deferencing the double pointer to n1 ptr
   int val = *n1_ptr;// deferencong the n1ptr to val
   if(val%2== 0)
   {
    *pp = n2_ptr;// update the double pointer to point t0 n2 *pp points to n1 which is updtaed to n2
   }
   
}

int main() {
    int n1, n2;
    scanf("%d %d", &n1, &n2);

    int *p = &n1;
    
    reassign_based_on_value(&p, &n2);

    printf("%d", *p);

    return 0;
}
```


 ### Swap Two Pointers Using Double Pointers
You are given two pointers, each pointing to different integer variables.

Task:

Write a function that swaps the pointers themselves (not the values).
After swapping, each pointer should now point to the other’s original variable.
 You must use double pointers (int **p1, int **p2) to swap addresses.

 ```c
#include <stdio.h>

void swap_pointers(int **p1, int **p2) {
    int *temp =*p1;// pointer temp to point the address p1 deferenced by double pointer
    *p1 = *p2;//copying the address of p2 to address of p1 by deference the double pointer
    *p2 =temp;//then temp is the pointer which means the variable that sores the adress of p1 is copied to adress of p3

}

int main() {
    int a, b;
    scanf("%d %d", &a, &b);

    int *p1 = &a;
    int *p2 = &b;

    swap_pointers(&p1, &p2);

    printf("%d %d", *p1, *p2);

    return 0;
}
```
