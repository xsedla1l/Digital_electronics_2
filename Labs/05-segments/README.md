# Lab 5: Marek Sedlacek (221068)

Link to GitHub repository:

   [https://github.com/xsedla1l/Digital_electronics_2](https://github.com/xsedla1l/Digital_electronics_2)


### 7-segment library

1. In your words, describe the difference between Common Cathode and Common Anode 7-segment display.
   * CC SSD - CC je skratka "Common cathode" čo v preklade znamená "spoločná katóda". Takže všetky katódy LED diód v dispaly sú spojené do jednej. Segmenty display riadíme pomocov anód - ACTIVE HIGH.
   * CA SSD - CA je skratka "Common anode" čo v preklade znamená "spoločná anoda". Takže všetky anody LED diód v dispaly sú spojené do jednej. Segmenty display riadíme pomocov katód - ACTIVE LOW.

2. Code listing with syntax highlighting of two interrupt service routines (`TIMER1_OVF_vect`, `TIMER0_OVF_vect`) from counter application with at least two digits, ie. values from 00 to 59:

```c
/**********************************************************************
 * Function: Timer/Counter1 overflow interrupt
 * Purpose:  Increment counter value from 00 to 59.
 **********************************************************************/
uint8_t DIG1 = 0; // showed number on DIG 1
uint8_t DIG2 = 0; // showed number on DIG 2
ISR(TIMER1_OVF_vect){ 
    DIG1++; 
    if (DIG1 == 10){ 
        DIG1 = 0; 
        DIG2++;   
        if (DIG2 == 6) DIG2 = 0; 
    }
}
```

```c
/**********************************************************************
 * Function: Timer/Counter0 overflow interrupt
 * Purpose:  Display tens and units of a counter at SSD.
 **********************************************************************/
ISR(TIMER0_OVF_vect){ 
    static uint8_t position = 0;
    
    if (position == 0){ SEG_update_shift_regs(digit1,0;
    } 
    else{ SEG_update_shift_regs(digit2,1); 
    }

    position++; 
    if (position > 1) position = 0; 
}
```

3. Flowchart figure for function `SEG_clk_2us()` which generates one clock period on `SEG_CLK` pin with a duration of 2&nbsp;us. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.

![alt text](https://github.com/xsedla1l/Digital_electronics_2/blob/main/Labs/05-segments/Images/flowchart.png)


### Kitchen alarm

Consider a kitchen alarm with a 7-segment display, one LED and three push buttons: start, +1 minute, -1 minute. Use the +1/-1 minute buttons to increment/decrement the timer value. After pressing the Start button, the countdown starts. The countdown value is shown on the display in the form of mm.ss (minutes.seconds). At the end of the countdown, the LED will start blinking.

1. Scheme of kitchen alarm; do not forget the supply voltage. The image can be drawn on a computer or by hand. Always name all components and their values.

![alt text](https://github.com/xsedla1l/Digital_electronics_2/blob/main/Labs/05-segments/Images/mega328P.png)
![alt text](https://github.com/xsedla1l/Digital_electronics_2/blob/main/Labs/05-segments/Images/7-seg.png)
![alt text](https://github.com/xsedla1l/Digital_electronics_2/blob/main/Labs/05-segments/Images/BTNS.png)
