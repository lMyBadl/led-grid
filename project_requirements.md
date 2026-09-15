# Parts:
## Given:
These parts are just ones that I want to work with. They're not based off of any research, just some things that I think would be cool to learn about and could add some interesting features.

- STM32 MCU
- LEDs of some sort (single color)
- Light sensor (I2C)
- 6 axis IMU (SPI)
- Barometer (I2C)
- GPS (UART)
- USB C

## Wants:
These are things that I think would be cool additions to the project. Once again no research behind them, since I'll pick the MCU based off of these wants and given requirements.

- 11x11 grid of LEDs (odd for centerpoint)
- Switches:
  - 11 switches for a single row of LEDs
- Buttons:
  - one reset button
  - one boot button
  - one button to choose between preset images
  - one mode button
  - one speed button
  - one brightness button
  - one save button
  - one clear button
  - one change row button
- programmable from usb c (no debug is fine)
- each type of serial communication in the board (I2C, SPI, UART)
- Real Time Clock


## Requirements:
These are requirements based off of the wants and given lists. 

- 3 PISO (parallel in serial out) shift registers (for input switches and buttons)
  - Register 1:
    - 8 led modification switches
  - Register 2:
    - 3 led mod switch
    - 2 up/down button for preset images
    - 2 up/down speed button (for animated images)
    - 1 mode button (between preset images or manual)
  - Register 3:
    - 2 brightness button
    - Manual Mode:
      - 1 save button
      - 1 clear button
      - 2 switch editing row button
- MCU:
  - Has bootloader function
  - GPIO:
    - 18 for row/col GPIO
    - 3 for shift registers (daisy chained)
    - 4 pins for SPI sensors
    - 2 pins for I2C sensors
    - 4 pins for STLink and debug
    - 2 pins for USB type C bootloading
    - 2 pins for UART
    - Sum: 21 GPIO, 1 sets SPI, 1 sets I2C, 1 set UART, 1 set differential USB, 1 set stlink debug (35) 
  - Protocols:
    - 9 timer pins
    - 1 set of SPI
    - 1 set of I2C
    - 1 set UART
    - 1 set STLink/debug
    - USB 
- MOSFETs:
  - 9 N channel for connecting LEDs to ground 
  - 9 P channel for connecting LEDs to power

- Loop speed: 5.28 MHz

## Parts List:
Based off the requirements, wants, and givens lists, and the calculations, these are the parts that work.

- MCU:
  - STM32F401RET6
    - 84 MHz Clock (15.9 FoS)
    - 512 kB Flash
    - 96 kB SRAM
    - 64 Pins
    - RTC
- IMU:
  - 


## Notes:
These are notes that have to be followed to make sure that the circuitry works and some thoughts about part choices

- MCU:
  - Package: probably LFQP 64, 48 leaves only like 3 usable GPIO for future developing
  - Since storage is cheap, go high as possible to give room for more things
  - 
- MOSFETs: 
  - Loads (LEDs) are always gonnected to drain because MOSFET uses voltage difference between gate and source to determine if it turns on