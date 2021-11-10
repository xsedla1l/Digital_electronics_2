# Lab 8: Marek Sedlacek (221068)

Link to GitHub repository:

   [https://github.com/xsedla1l/Digital_electronics_2](https://github.com/xsedla1l/Digital_electronics_2)


### Analog-to-Digital Conversion

1. Complete table with voltage divider, calculated, and measured ADC values for all five push buttons.

   | **Push button** | **PINS** | 
   | :-: | :-: |
   | PWM generators from Timer0, Timer1, Timer2 | 3, 5, 6, 9, 10, 11 		| 
   |analog channels for ADC | PC0, PC1, PC2, PC3, PC4, PC5| 
   |UART pins   | PD1, PD0  	|   
   | I2C pins  | PC4, PC5    	|  
   | SPI pins | PB2, PB3, PB4, PB6  |  
   | external interrupt pins INT0, INT1  | INT0 - PD2, INT1 - PD3   	|  

2. Code listing of ACD interrupt service routine for sending data to the LCD/UART and identification of the pressed button. Always use syntax highlighting and meaningful comments:

```c
/**********************************************************************
 * Marek Sedlacek
 * Function: ADC complete interrupt
 * Purpose:  Display value on LCD and send it to UART.
 **********************************************************************/
ISR(ADC_vect)
{
    uint16_t value = 0;
    char lcd_string[4] = "0000";
    value = ADC;  
    
    //Clear previous value
    lcd_gotoxy(8,0);
    lcd_puts("    ");
    
    //Put new value to LCD display
    itoa(value, lcd_string, 10);  // Convert dec to string
    lcd_gotoxy(8,0);
    lcd_puts(lcd_string);
    
    // send the same value to UART
    uart_puts(lcd_string);
    uart_puts(" ");        
        
    //Clear previous value
    lcd_gotoxy(13,0);
    lcd_puts("    ");
    //Put new value to LCD
        
    //display value in hex
    itoa(value, lcd_string, 16);    // Convert dec to string
    lcd_gotoxy(13,0);
    lcd_puts(lcd_string);
        
    //display what button was pressed
    lcd_gotoxy(8,1);
    lcd_puts("    ");
    lcd_gotoxy(12,1);
    lcd_puts("    ");
        
        
    lcd_gotoxy(8, 1);                // Copy ADC result to 16-bit variable
    itoa(value, lcd_string, 10);     // Convert dec value to string

    if (value>1000) { lcd_puts("NONE");}
        if ((value>600)&&(value<1000)) { lcd_puts("SELECT");}
            if ((value>350)&&(value<450)) { lcd_puts("LEFT");}
                if ((value>200)&&(value<270)) { lcd_puts("DOWN");}
                    if ((value>5)&&(value<120)) { lcd_puts("UP");}
                        if (value==0) { lcd_puts("RIGHT");}
     ;
}

```


### UART communication

1. (Hand-drawn) picture of UART signal when transmitting three character data `De2` in 4800 7O2 mode (7 data bits, odd parity, 2 stop bits, 4800&nbsp;Bd).

 ![alt text](https://github.com/xsedla1l/Digital_electronics_2/blob/main/Labs/07-uart/Images/De2.png) 



2. Flowchart figure for function `uint8_t get_parity(uint8_t data, uint8_t type)` which calculates a parity bit of input 8-bit `data` according to parameter `type`. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.

![alt text](https://github.com/xsedla1l/Digital_electronics_2/blob/main/Labs/07-uart/Images/flowchart.png)


### Temperature meter

Consider an application for temperature measurement and display. Use temperature sensor [TC1046](http://ww1.microchip.com/downloads/en/DeviceDoc/21496C.pdf), LCD, one LED and a push button. After pressing the button, the temperature is measured, its value is displayed on the LCD and data is sent to the UART. When the temperature is too high, the LED will start blinking.

1. Scheme of temperature meter. The image can be drawn on a computer or by hand. Always name all components and their values.

![alt text](https://github.com/xsedla1l/Digital_electronics_2/blob/main/Labs/07-uart/Images/schema.png)



