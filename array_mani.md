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
