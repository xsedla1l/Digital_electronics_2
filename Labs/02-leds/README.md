# Lab 2: Marek Sedlacek (221068)

Link to GitHub repository:

   [https://github.com/xsedla1l/Digital_electronics_2](https://github.com/xsedla1l/Digital_electronics_2)


## 1 Active-low and active-high LEDs

| **DDRB** | **Description** |
| :-: | :-- |
| 0 | Input pin |
| 1 | Output pin |

| **PORTB** | **Description** |
| :-: | :-- |
| 0 | Output low value |
| 1 | Output high value |

| **DDRB** | **PORTB** | **Direction** | **Internal pull-up resistor** | **Description** |
| :-: | :-: | :-: | :-: | :-- |
| 0 | 0 | input | no | Tri-state, high-impedance |
| 0 | 1 | input | yes/no | Pxn will source current if ext. pulled low/Tri-state (Hi-Z) | 
| 1 | 0 | output | no | Output Low (Sink) |
| 1 | 1 | output | no | Output High (Source) |

### PINOUT ARDUINO UNO 

| **Port** | **Pin** | **Input/output usage?** |
| :-: | :-: | :-- |
| A | x | Microcontroller ATmega328P does not contain port A |
| B | 0 | Yes (Arduino pin 8) |
|   | 1 | Yes (Arduino pin ~9) |
|   | 2 | Yes (Arduino pin ~10) |
|   | 3 | Yes (Arduino pin ~11) |
|   | 4 | Yes (Arduino pin 12) |
|   | 5 | Yes (Arduino pin 13) |
|   | 6 | NO |
|   | 7 | NO |
| C | 0 | Yes (Arduino pin A0) |
|   | 1 | Yes (Arduino pin A1) |
|   | 2 | Yes (Arduino pin A2) |
|   | 3 | Yes (Arduino pin A3) |
|   | 4 | Yes (Arduino pin A4/SDA) |
|   | 5 | Yes (Arduino pin A5/SSL) |
|   | 6 | Yes - RESET pin |
|   | 7 | NO |
| D | 0 | Yes (Arduino pin RX<-0) |
|   | 1 | Yes (Arduino pin TX->1) |
|   | 2 | Yes (Arduino pin D2) |
|   | 3 | Yes (Arduino pin ~D3) |
|   | 4 | Yes (Arduino pin D4) |
|   | 5 | Yes (Arduino pin ~D5) |
|   | 6 | Yes (Arduino pin ~D6) |
|   | 7 | Yes (Arduino pin D7) |


## 2 Part of the C code:
 
```c

#define LED_GREEN   PB5     // AVR pin where green LED is connected
#define LED_RED     PC0     // AVR pin where red LED is connected
#define BLINK_DELAY 200
#ifndef F_CPU
# define F_CPU 16000000     // CPU frequency in Hz required for delay
#endif

/* Includes ----------------------------------------------------------*/
#include <util/delay.h>     // Functions for busy-wait delay loops
#include <avr/io.h>         // AVR device-specific IO definitions

int main(void)
{
    // Green LED at port B
    // Set pin as output in Data Direction Register...
    DDRB = DDRB | (1<<LED_GREEN);
    // ...and turn LED off in Data Register
    PORTB = PORTB & ~(1<<LED_GREEN);

    // Configure the second LED at port C
    DDRC = DDRC | (1<<LED_RED); // posun jednotku o 5 - ostatne sa nemenia!
    PORTC = PORTC & ~(1<<LED_RED); // andujem 1 a na mojej poyicie je 0 - ostatne sa nemenia! 

    
    // Infinite loop
    while (1)
    {
        // Pause several milliseconds
        _delay_ms(BLINK_DELAY);
        PORTB = PORTB ^ (1<<LED_GREEN);	 
        PORTC = PORTC ^ (1<<LED_RED);
        _delay_ms(BLINK_DELAY);                  
           
    }

    // Will never reach this
    return 0;
}

```


```c

#define LED_GREEN   PB5     // AVR pin where green LED is connected
#define LED_RED     PC0     // AVR pin where red LED is connected
#define PUSH_BTN     PD4     // AVR pin where push button
#define BLINK_DELAY 200
#ifndef F_CPU
# define F_CPU 16000000     // CPU frequency in Hz required for delay
#endif

#include <util/delay.h>     // Functions for busy-wait delay loops
#include <avr/io.h>         // AVR device-specific IO definitions
#include <avr/sfr_defs.h>

int main(void)
{
    // Green LED at port B
    // Set pin as output in Data Direction Register...
    DDRB = DDRB | (1<<LED_GREEN);// ...and turn LED off in Data Register
    PORTB = PORTB | (1<<LED_GREEN);

    // Configure the second LED at port C
    DDRC = DDRC | (1<<LED_RED); // posun jednotku o 5 - ostatne sa nemenia!
    PORTC = PORTC & ~(1<<LED_RED); // andujem 1 a na mojej poyicie je 0 - ostatne sa nemenia! 

    // Configure Push button at port D and enable internal pull-up resistor
     DDRD = DDRD & ~ (1<<PUSH_BTN);     
     PORTD = PORTD | (1<<PUSH_BTN);

    // Infinite loop
    while (1)
    {
            if(bit_is_clear(PIND, PUSH_BTN))
            {
                PORTC = PORTC ^ (1<<LED_RED); 
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(BLINK_DELAY);
            }      
           
    }

    // Will never reach this
    return 0;
}

```


## 3 Knight Rider
![alt text](https://github.com/xsedla1l/Digital_electronics_2/blob/main/Labs/02-leds/Images/Knight%20Rider.png)
