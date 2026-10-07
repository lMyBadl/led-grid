# Understanding MCUs:
See AN2867 for STM32 crystals
## Crystal Oscillators:
Transconductance (Gm) - how much current an amplifier outputs based on a change in voltage
- Look in the datasheet for these values.
- To find the external oscillator's max Gm, use gmcrit = 4 * ESR * (2 π F)^2 * (C0 + CL)^2
  - ESR is the equivalent series resistance
  - C0 is the crystal shunt capacitance
  - CL is the crystal nominal load capacitance.
  - F is the crystal nominal oscillation frequency
- Importance: Since external oscillators lose energy every cycle, transconductance describes the maximum "energy" that the MCU oscillator pins can output to maintain the oscillator's frequency. External oscillators must be under this value in order for the oscillator to work properly with the MCU (gmcrit < Gm_crit_max)
  - Some datasheets only specify Gm, which means that you need to make sure that 3gmcrit < Gm (for low speed) and 5gmcrit < Gm (for high speed)

External Resistor (Rext) - the external resistor which controls the power delivered to the external oscillator
- Calculated using Rext = 1 / (2 π F CL2)
- Now Gm_crit = 4 * (ESR + Rext) * (2 π F)^2 * (C0 + CL)^2
  - This new value needs to satisfy the ratios above for gmcrit to Gm