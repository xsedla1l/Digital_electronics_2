# Lab 2: Marek Sedlacek (221068)

Link to GitHub repository:

   [https://github.com/xsedla1l/Digital_electronics_2](https://github.com/xsedla1l/Digital_electronics_2)


## 1



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
| 0 | 1 | input | yes/no | Pxn will source current if ext. pulled low/Tri-state (Hi-Z) | - ak je ten bit nastaveny do nuly, tak su vypnute vsetky pud rezistory
| 1 | 0 | output | no | Output Low (Sink) |
| 1 | 1 | output | no | Output High (Source) |



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
|   | 7 |  |
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
int main(void)
{
    // Set pin as output in Data Direction Register
    // DDRB = DDRB or 0010 0000
    DDRB = DDRB | (1<<LED_GREEN);

    // Set pin LOW in Data Register (LED off)
    // PORTB = PORTB and 1101 1111
    PORTB = PORTB & ~(1<<LED_GREEN);

    // Infinite loop
    while (1)
    {
        // Pause several milliseconds
        _delay_ms(LONG_DELAY);
		
        PORTB = PORTB ^ (1<<LED_GREEN);	 // H	
		_delay_ms(SHORT_DELAY);		
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		
		_delay_ms(LONG_DELAY);
		
		PORTB = PORTB ^ (1<<LED_GREEN);	 // i
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		
		_delay_ms(LONG_DELAY);
		
		PORTB = PORTB ^ (1<<LED_GREEN);	 // ;
		_delay_ms(LONG_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(LONG_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);	 
		_delay_ms(LONG_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		
		_delay_ms(LONG_DELAY);
		
		PORTB = PORTB ^ (1<<LED_GREEN);	 // )
		_delay_ms(LONG_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(LONG_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);	 
		_delay_ms(LONG_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(LONG_DELAY);
		PORTB = PORTB ^ (1<<LED_GREEN);
		_delay_ms(SHORT_DELAY);		
		
    }

    // Will never reach this
    return 0;
}

```


2. Scheme of Morse code application
![alt text](https://github.com/xsedla1l/Digital_electronics_2/blob/main/Labs/01-tools/Images/Image1.png)
