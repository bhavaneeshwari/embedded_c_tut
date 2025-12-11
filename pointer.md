### Print Sum of Even Numbers
You are given an array of integers and its size. Using only pointer arithmetic:

Traverse the array
Find the sum of all even numbers
Print the sum 
```c
#include <stdio.h>

int sum_even_numbers(int *ptr, int n) {
    int sum =0;

    for(int i=0;i<n;i++)
    {  if(*(ptr+i)%2==0){
            sum +=*(ptr+i);}
       
    }
    return sum;
}

int main() {
    int n;
    scanf("%d", &n);

    int arr[100];
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    int result = sum_even_numbers(arr, n);

    printf("Sum = %d", result);

    return 0;
}
```


### Reverse an Array Using Only Pointers
You are given an array of integers and its size n.
Using only pointer arithmetic:

Reverse the array elements in-place.
Print the reversed array.

```c

#include <stdio.h>

void reverse_array(int *ptr, int n) {
    int start =0;
    int end =n-1;
    int temp;
    while (end>start)
    {
        temp= *(ptr+start);
        *(ptr+start)=*(ptr+end);
        *(ptr+end) =temp;
        start++;
        end--;

    }



}

int main() {
    int n;
    scanf("%d", &n);

    int arr[100];
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    reverse_array(arr, n);

    for (int i = 0; i < n; i++) {
        printf("%d", arr[i]);
        if(i < n-1){
            printf(" ");
        }
    }

    return 0;
}

```
