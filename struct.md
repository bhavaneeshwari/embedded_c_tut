### Pointer to Struct with Bitfields
You are given a pointer to a UART_ControlRegister struct representing a 32-bit hardware register.
The struct has the following bitfields:

struct UART_ControlRegister {
    unsigned int baudrate : 4;   // Bits 0-3
    unsigned int tx_enable : 1;  // Bit 4
    unsigned int rx_enable : 1;  // Bit 5
    unsigned int tx_irq_en : 1;  // Bit 6
    unsigned int rx_irq_en : 1;  // Bit 7
    unsigned int parity_en : 1;  // Bit 8
    unsigned int stop_bits : 1;  // Bit 9
    unsigned int reserved : 22;  // Bits 10-31
};Copy
Your task:
Write a function that receives a pointer to this struct.
Set the UART configuration:
Baud rate = 9
TX & RX enable = 1
TX IRQ = 1, RX IRQ = 0
Parity = 1
Stop bit = 0
Print each field’s value after configuration.

 ```c
#include <stdio.h>

struct UART_ControlRegister {
    unsigned int baudrate : 4;
    unsigned int tx_enable : 1;
    unsigned int rx_enable : 1;
    unsigned int tx_irq_en : 1;
    unsigned int rx_irq_en : 1;
    unsigned int parity_en : 1;
    unsigned int stop_bits : 1;
    unsigned int reserved : 22;
};

void configure_uart(struct UART_ControlRegister *reg) {
   
   reg->baudrate = 9;
   reg->tx_enable =1;
   reg->rx_enable=1;
   reg->tx_irq_en =1;
   reg-> rx_irq_en =0;
   reg-> parity_en=1;
   reg->stop_bits=0;
   
}
int main() {
    struct UART_ControlRegister reg = {0};

    configure_uart(&reg);

    printf("baudrate = %u\n", reg.baudrate);
    printf("tx_enable = %u\n", reg.tx_enable);
    printf("rx_enable = %u\n", reg.rx_enable);
    printf("tx_irq_en = %u\n", reg.tx_irq_en);
    printf("rx_irq_en = %u\n", reg.rx_irq_en);
    printf("parity_en = %u\n", reg.parity_en);
    printf("stop_bits = %u", reg.stop_bits);

    return 0;
}
```

### Construct UART Data Frame with Parity Bit
You are implementing UART data transmission logic. A control register configures parity settings for data framing. The control register is defined as an 8-bit register:
 

typedef struct {
    uint8_t parity_enable : 1;   // 0 = Disabled, 1 = Enabled
    uint8_t parity_type   : 1;   // 0 = Even parity, 1 = Odd parity
    uint8_t reserved      : 6;   // Reserved bits
} UART_Control;Copy
 

You’re given a 7-bit data (0–127). Your task is to create an 8-bit UART frame using the control register:

If parity is disabled, the MSB (bit 7) is 0, and the remaining 7 bits are data.
If parity is enabled:
Count the number of 1s in the 7-bit data.
Add a parity bit at the MSB (bit 7):
Even parity ➝ parity bit = 0 if 1s are even, 1 if odd.
Odd parity  ➝ parity bit = 1 if 1s are even, 0 if odd.
 

Parity in Simple Terms

Parity is an error-detection bit added to the data:

Even parity → total number of 1s (including parity) must be even
(e.g., data = 1011 → has 3 ones → parity = 1 → 10001011)
 
Odd parity  → total number of 1s (including parity) must be odd
(e.g., data = 1010 → has 2 ones → parity = 1 → 10001010)


```c
#include <stdio.h>
#include <stdint.h>

typedef struct {
    uint8_t parity_enable : 1;
    uint8_t parity_type   : 1;
    uint8_t reserved      : 6;
} UART_Control;

uint8_t create_uart_frame(uint8_t data, UART_Control *ctrl) {
    // Your logic here
    
     int count =0;
    if (ctrl-> parity_enable)
    {
        for(int i =0;i<7;i++)
        {
            if((data>>i)&1)
            
               count ++;
            
        }
    
        if( ctrl->parity_type)
        {
            if(count%2==0){data|=(1<<7);}//set msb one
            else {data&=~(1<<7);}
        }
        else 
        {
            if(count%2==0){data&=~(1<<7);}
            else {data|=(1<<7);}
        }
    }
    else 
    {
       data&=~(1<<7);
    }
    
    return data;
}

int main() {
    uint8_t data;
    scanf("%hhu", &data);  // 7-bit input

    uint8_t parity_enable, parity_type;
    scanf("%hhu %hhu", &parity_enable, &parity_type);

    UART_Control ctrl;
    ctrl.parity_enable = parity_enable;
    ctrl.parity_type = parity_type;

    uint8_t frame = create_uart_frame(data, &ctrl);
    printf("frame = 0x%02X", frame);

    return 0;
}
```
