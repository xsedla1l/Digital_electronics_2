# Lab 3: YOUR_FIRSTNAME FAMILYNAME

Link to your `Digital-electronics-2` GitHub repository:

   [https://github.com/...](https://github.com/...)


### Data types in C


| **Data type** | **Number of bits** | **Range** | **Description** |
| :-: | :-: | :-: | :-- | 
| `uint8_t`  | 8 | 0, 1, ..., 255 | Unsigned 8-bit integer |
| `int8_t`   | 8 | -128 to 127 | Signed 8-bit integer |
| `uint16_t` | 16 | 0 to 65,535 | Unsigned 16-bit integer |
| `int16_t`  | 16 | -32,768 to 32,767 | Signed 16-bit integer |
| `float`    | 32 | -3.4e+38, ..., 3.4e+38 | Single-precision floating-point |
| `void`     | - |  |  |


### GPIO library

1. In your words, describe the difference between the declaration and the definition of the function in C.
   * Function declaration
   * Function definition

2. Part of the C code listing with syntax highlighting, which toggles LEDs only if push button is pressed. Otherwise, the value of the LEDs does not change. Use function from your GPIO library. Let the push button is connected to port D:

```c
    // Configure Push button at port D and enable internal pull-up resistor
    // WRITE YOUR CODE HERE

    // Infinite loop
    while (1)
    {
        // Pause several milliseconds
        _delay_ms(BLINK_DELAY);

        // WRITE YOUR CODE HERE
    }
```


### Traffic light



   ![your figure]()