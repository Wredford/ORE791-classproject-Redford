###Approach
- Assumed 2x Duracell 9V alkaline-Manganese Dioxide batteriesn(500-600 mAh is likely)
- OPA128LM datasheet from Uchicago: 1.5mA maximum supply current, .9mA typical.
- LED current calculated to be .9 mA max.
- R1 calculated to be under .2mA
- R2+R3 calculated to be under .1mA max.
- Current cant run through both the LED (~1mA) and the main circuit (1.8mA) at once. 1.8 > 1, so that is the assumed.
- For 550mAh, and a ~2mA draw (factor of safety from 1.8), it will likely get 275 hours (assuming the V doesnt sag too low to function) 

###Power Creation
-9V is the positive end of one battery
--9V is the neg end of another battery
-0V is where the two batteries meet.

###split rails
-because the op amp needs both a positive and negative source to create outputs with flipping signs.

###SuppyV and outputV
-outputV is at most 20x the inputV. SupplyV is what is needed to work the opamp

###Current estimates
-max 1.8 mA at once
-runtime of ~275 hrs
-uncertanties are mainly voltage sag from the batteries, realistic current draw, and wire length related losses

###Questions for class
-What op amp are we actually using
-Where do the ADC and featherboard pins come in