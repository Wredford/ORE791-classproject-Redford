## Week 8: Power  arch 

## Selected power arch
- Separate analog supply: two 9V batteries in series for ±9V.
- The Feather runs on its own USB or LiPo power.
- Grounds are tied together so the ADC can measure the amplifier output.

## Voltage rails in the design
- +9V, GND, and -9V from the battery stack (the junction between the batteries is GND).
- +2.5V and -2.5V from LDOs, for the ADC's AVDD and AVSS.
- 3.3V from the Feather, for the ADC's DVDD and the SPI logic.

## Amp power
- The OPA128LM runs directly from ±9V, inside its ±5V to ±18V range.
- Estimated draw is about 1 to 2 mA, including the gain network.
- Decoupling capacitors sit at its supply pins.

## Feather power
- USB or LiPo, independent of the analog batteries.
- It supplies the 3.3V logic and the ADC's digital supply.
- Prefer LiPo for measurements to avoid USB ground-loop hum.

## ADC power
- ADS1220 analog supply of +2.5V and -2.5V (5V total, under its 5.5V limit).
- Digital supply of 3.3V from the Feather.
- Draws roughly 0.3 to 0.5 mA.

## GND reference plan
- All grounds form one net, tied together at the battery junction only.
- The probe's reference electrode and BNC shield go to GND.
- Keep the Feather's return currents off the analog ground path.

## Regulator plan
- Linear regulators (LDOs), one positive and one negative, fed from ±9V.
- Choose LDOs rated for more than a fresh battery's ~9.5V input, with low noise.
- No switching converters on the analog rails. The LM2596 was rejected for its ~5 mA quiescent current and 150 kHz switching noise.

## How to handle negative V
- The ADC's bipolar supply lets its inputs go below ground.
- A scaling and clamp stage keeps the amplifier's swing inside the ADC's range.
- Reduce the amplifier gain if possible, and add a series resistor at the ADC inputs.

## Why this approach
- Quietest supply for a high-impedance pH front end, with no switching noise.
- No negative converter or charge pump needed.
- The op-amp tolerates battery sag, and the ADC gets a regulated supply.
- The pH signal is bipolar around 0V, so no bias network is required.

## Main risks
- USB ground loops causing 50/60 Hz hum.
- ADC input overvoltage from amplifier output swing or power sequencing.
- Feather return currents coupling into the analog ground.
- Two batteries to manage, and the BAT TEST branch needs the right voltage across it.

## Main uncertainties/questions for class
- ADS1220 bipolar-supply details.
- A suitable low-noise negative LDO part.
- Final amplifier gain and scaling ratio.
- Whether the 11V Zener BAT TEST is across the full 18V.