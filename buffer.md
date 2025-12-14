### Serialized Data Buffer
In firmware, you often need to assemble a communication packet as a byte array before sending it over UART/SPI.

You are given the following fields:

Field	Size	Description
Start	1 byte	Always 0xA5
Command	1 byte	User input
Value	2 byte	16-bit data (uint16_t)
Status	1 byte	Flags (0 or 1)
Checksum	4 byte	32-bit checksum (uint32_t)
End	1 byte	Always 0x5A
Your task is to:

Fill a uint8_t buffer[10] with the data in this order
Use pointer casting or byte manipulation
Print the entire buffer contents as space-separated integers

 ```c
#include <stdio.h>
#include <stdint.h>

void build_packet(uint8_t command, uint16_t value, uint8_t status, uint32_t checksum) {
    uint8_t buffer[10];
      uint8_t *vp;//creating a buffersize pointer
        vp=  (uint8_t*)&value;//typecasting te original data to buffer size pointer
       uint8_t *cs;
       cs =(uint8_t*)&checksum;
 
    // Your logic to fill buffer
    buffer[0]=0xA5;
    buffer[1]=command;
    buffer[2]=*vp;
   buffer[3]=*(vp+1);
 
    buffer[4]=status;
    buffer[5]=*cs;
    buffer[6]=*(cs+1);
    buffer[7]=*(cs+2);
    buffer[8]=*(cs+3);
   

    buffer[9]=0x5A;
    // Then print buffer
    for (int i =0;i<10;i++)
    {
        printf("%d ",buffer[i]);
    }
}

int main() {
    uint8_t cmd, status;
    uint16_t val;
    uint32_t crc;

    scanf("%hhu %hu %hhu %u", &cmd, &val, &status, &crc);
    build_packet(cmd, val, status, crc);
    return 0;
}
```
