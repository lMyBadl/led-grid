# Parts:
## Given:
These parts are just ones that I want to work with. They're not based off of any research, just some things that I think would be cool to learn about and could add some interesting features.

- STM32 MCU
- LEDs of some sort (single color)
- 7-segment displays
- 2 ICs that use I2C
- 2 ICs that use SPI
- 1 IC with UART
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
- 3 SIPO shift registers (for seven segment displays)
  - one per each
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

- MCU: STM32F411VET6
  - 100 MHz Clock (18.94 FoS)
  - 512 kB Flash
  - 128 kB SRAM
  - 81 I/O Pins
  - RTC
  - Watchdog 
  - FPU for potential calculations
  - GPIO Voltage: 3.3V
- IMU: BMI323
  - 6 DoF IMU
  - 3 axis accelerometer (16 bit): 2, 4, 8, 16 g 
  - 3 axis gyroscope (16 bit): 125, 250, 500, 1000, 2000 deg/s
  - temperature sensor (16 bit): -40 - 80 degC
  - SPI communication
- Light Sensor: VEML3235
  - Operating voltage: 2.6 - 3.3V
  - I2C communication
    - I2C voltage: 1.7 - 3.6V
  - Sensitivity from 0.0021 - 17867 lux
  - White channel (16 bit):
    - Raw light sensor
  - Ambient light sensor channel (16 bit):
    - Adjusted for human vision
- Barometer: BMP581
  - Operating voltage: 1.7 - 3.6V
  - SPI and I2C
  - Pressure (24 bit): 30 - 125 kPa
  - Temperature (24 bit): -40 - 80 degC
  - On chip temperature compensation
- GNSS: MAX-M10M-20B
  - Operating voltage: 1.76 - 5.5V
  - I2C and UART
  - Velocity accuracy: 0.05 m/s
  - Heading accuracy: 0.3 deg
  - Position accuracy: 1.5 m
- Antenna: W2332
  - Return loss mins at ~1575 MHz and ~1605 MHz (GNSS bands for the world)


