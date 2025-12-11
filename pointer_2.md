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
