# Notes:
These are notes that have to be followed to make sure that the circuitry works and some thoughts about part choices

## MCU
- PI filter to separate analog and digital power
- SPDT switch with a pull up/down resistor for BOOT0
- See AN2867 STM32 for Crystals 
  - C = 2(CL - Cs)
    - CL is load capacitance (from datasheet)
    - Cs is stray capacitance 
    - C are the two capacitors that you put on the PCB
  - (for oscillator) gmcrit = 4 * ESR * (2 pi F)^2 * (C0 + CL)^2
    - ESR is the equivalent series resistance
    - C0 is the crystal shunt capacitance
    - CL is the crystal nominal load capacitance.
    - F is the crystal nominal oscillation frequency
    - make sure it is less than gmcrit on datasheet
      - Ex: for STM32F411CE, HSE gm_crit_max = 1 mA/V and LSE gm_crit_max = 1.5 uA/V
      - Ex: for 
- See AN4879 for USB guidelines
- see ESD protections for STM32
- Filter USB power

## MOSFETS
- Loads (LEDs) are always gonnected to drain because MOSFET uses voltage difference between gate and source to determine if it turns on
- Unless for reverse polarity protection, then opposite
