# Lab 1: Marek Sedlacek (221068)

Link to your `Digital-electronics-2` GitHub repository:

   [https://github.com/...](https://github.com/xsedla1l/Digital_electronics_2)


### Blink example

1. 
   * `|`    - It is OR     (logical sum)
   * `&`    - It is AND    (logical product)
   * `^`    - It is NOT    (logical negation)
   * `~`    - It is XOR
   * `<<`   - It is "bit shift"
   * `>>`   - It is "bit shift"

2. Complete truth table with operators: `|`, `&`, `^`, `~`

| **b** | **a** |**b or a** | **b and a** | **b xor a** | **not b** |
| :-: | :-: | :-: | :-: | :-: | :-: |
| 0 | 0 | **0** | **0** | **0** | **1** |
| 0 | 1 | **1** | **0** | **1** | **1** |
| 1 | 0 | **1** | **0** | **1** | **0** |
| 1 | 1 | **1** | **1** | **0** | **0** |


### Morse code ( Hi ;) )

 
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
![alt text](https://github.com/xsedla1l/Digital-electronics-1/blob/main/Labs/04-adder/Images/image4.png)
