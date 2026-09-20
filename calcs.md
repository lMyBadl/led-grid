# Power:
Part    | Max Current
--------|-------------
BMI323  | 790 uA

# Control Loop Speed:
Number  |   Reasoning
--------|------------------
120 Hz  | Camera photos indoors take around 8 ms to take
*4      | Have 4 different settings (1/4, 1/2, 3/4, 1) duty cycle of the row on time for brightness
*11     | Each row (11 total) have to has to display for it to show up on the photo
*10     | To ensure that the camera captures the entire picture with brightness
*100    | To account for the clock cycles that GPIO pin toggling uses 

Total: 5.28 MHz