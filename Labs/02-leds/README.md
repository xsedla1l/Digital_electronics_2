# Lab 2: Marek Sedlacek (221068)

Link to GitHub repository:

   [https://github.com/xsedla1l/Digital_electronics_2](https://github.com/xsedla1l/Digital_electronics_2)


### Blink example
 
   1. Draw two basic ways to connect a LED to the output pin of the microcontroller: LED active-low, LED active-high.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

2. [Calculate LED resistor value](https://electronicsclub.info/leds.htm) for typical red and blue LEDs.

&nbsp;
![ohms law](Images/ohms_law.png)
&nbsp;

| **LED color** | **Supply voltage** | **LED current** | **LED voltage** | **Resistor value** |
| :-: | :-: | :-: | :-: | :-: |
| red | 5&nbsp;V | 20&nbsp;mA | | |
| blue | 5&nbsp;V | 20&nbsp;mA | | |


3. Draw the basic ways to connect a push button to the microcontroller input pin: button active-low, button active-high.



| **DDRB** | **Description** |
| :-: | :-- |
| 0 | Input pin |
| 1 | |

| **PORTB** | **Description** |
| :-: | :-- |
| 0 | Output low value |
| 1 | |

| **DDRB** | **PORTB** | **Direction** | **Internal pull-up resistor** | **Description** |
| :-: | :-: | :-: | :-: | :-- |
| 0 | 0 | input | no | Tri-state, high-impedance |
| 0 | 1 | | | |
| 1 | 0 | | | |
| 1 | 1 | | | |

See [schematic of Arduino Uno board](../../Docs/arduino_shield.pdf) in docs folder of Digital-electronics-2 repository and find out which pins of ATmega328P can be used as input/output pins. To which pin is the LED L connected? Is it connected as active-low or active-high? Note that labels on Arduino `~3`, `~5`, etc. do not mean that the signals are inverted; the `~` symbol indicates that a PWM (Pulse-width modulation) signal can be generated on these pins.

| **Port** | **Pin** | **Input/output usage?** |
| :-: | :-: | :-- |
| A | x | Microcontroller ATmega328P does not contain port A |
| B | 0 | Yes (Arduino pin 8) |
|   | 1 | Yes (Arduino pin 9) |
|   | 2 | Yes (Arduino pin 10) |
|   | 3 | Yes (Arduino pin 11) |
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
|   | 1 |  |
|   | 2 |  |
|   | 3 |  |
|   | 4 |  |
|   | 5 |  |
|   | 6 |  |
|   | 7 |  |


### 

 
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
