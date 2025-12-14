### Checksum Validation
You are given a block of memory (array of n bytes) which includes n-1 data bytes and the last byte as checksum.

Your task is to verify whether the last byte equals the XOR of all previous bytes (excluding itself).

Return:

1 if the checksum is valid
0 if the checksum is incorrect
Checksum: It’s a simple error-detection method that ensures data hasn’t been corrupted during storage or transmission.

The sender calculates based on specific algorithm and sends it with the data; the receiver recalculates it similarly from the received data—if both match, the data is intact, otherwise it’s likely corrupted.
```c
#include <stdio.h>

int validate_checksum(int *mem, int n) {
    // Write your XOR scan logic here
int cs=0;
int l = n-1;
    for(int i=0;i<n-1;i++)
    {
cs ^=*(mem+i);


    }
    if(cs==*(mem+l))
    return 1;
    else 
    return 0;
}

int main() {
    int n, arr[100];
    scanf("%d", &n);
    
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    int result = validate_checksum(arr, n);
    printf("%d", result);

    return 0;
}
```

### Reverse an Array In-Place
You are given an array of integers and its length. Write a function to reverse the array in-place, without using another array.
```c
#include <stdio.h>

void reverse_array(int arr[], int n) {
    
int start =0;
int end = n-1;
    int temp=0;

    while(end>start)
    {
        temp =arr[start];
        arr[start]=arr[end];
        arr[end]=temp;
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

###  Left Rotate Array by K Positions
You are given an array of size n and an integer k. Rotate the array left by k positions, in-place (without using any extra array).

This means the elements that go beyond the first k positions should wrap around to the end.

```c
#include <stdio.h>

void rotate_array(int arr[],int n)
{
    int start =0;
    int end =n-1;
    int temp=0;
    while(end>start)
    {   temp=arr[start];
        arr[start]=arr[end];
        arr[end]=temp;
        start++;
        end--;
    }
}
void rotate_left(int arr[], int n, int k) {
    // Your logic here
int k1=k%n;// for wrap around condt
rotate_array(arr,k1);//rotate upto k
rotate_array(arr,n);//rotate the whole 
rotate_array(arr,n-k1);

}

int main() {
    int n, k;
    scanf("%d %d", &n, &k);

    int arr[100];

    // Read array elements
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    // Rotate the array
    rotate_left(arr, n, k);

    // Print the rotated array
    for (int i = 0; i < n; i++) {
        printf("%d", arr[i]);
        if(i < n-1){
        	printf(" ");
        }
    }

    return 0;
}
```

### Find Duplicate in Range 0 and n-1
You are given an array of n integers. Each number is guaranteed to be in the range [0, n-1], and exactly one number is repeated once. Write a program to find and print the repeated number.

You cannot modify the array and cannot use extra memory (O(1) space).
```c
#include <stdio.h>

int find_duplicate(int arr[], int n) {
    // Your logic here
    for(int i =0;i<n;i++)
    {
        for (int j = i+1;j<n;j++)
        {
           if(arr[i]==arr[j]) 
           return arr[i];
        }
    }
    
}

int main() {
    int n;
    scanf("%d", &n);

    int arr[100];
    for (int i = 0; i < n; i++) scanf("%d", &arr[i]);

    int result = find_duplicate(arr, n);
    printf("%d", result);
    return 0;
}
```
###  Sliding Window Sum
You are given an array of integers and a window size k. Your task is to calculate the sum of each window of size k as it slides across the array from left to right.

Return all window sums in a single line, separated by space.

```c
#include <stdio.h>

void sliding_window_sum(int arr[], int n, int k) {
    // Your logic here
   
    for (int i =0;i<n-k+1;i++)
    {    int sum=0;
        for (int j =i;j<i+k;j++)
        {sum += arr[j];}
     printf("%d ",sum);
     
    }
}

int main() {
    int n, k, arr[100];
    scanf("%d %d", &n, &k);
    for (int i = 0; i < n; i++) scanf("%d", &arr[i]);

    sliding_window_sum(arr, n, k);
    return 0;
}
```
