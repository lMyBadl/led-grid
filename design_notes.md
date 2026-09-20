# Notes:
These are notes that have to be followed to make sure that the circuitry works and some thoughts about part choices

## MCU
- PI filter to separate analog and digital power
- SPDT switch with a pull up/down resistor for BOOT0
- See AN2867 STM32 for Crystals (16MHz)
- See AN4879 for USB guidelines
- see ESD protections for STM32
- Filter USB power

## MOSFETS
- Loads (LEDs) are always gonnected to drain because MOSFET uses voltage difference between gate and source to determine if it turns on
