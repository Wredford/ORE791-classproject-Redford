#ORE 791: Low-Cost Benchtop pH Meter Project Log (Fall 2026)

## Week 1: GitHub + KiCad version

### Date
-8/24 to 8/27

### KiCad 10.05

### GitHub Repo
- ORE791-classproject-Redford

### Tutorials Completed
- Digikey playlist

### What I set up
- Got KiCad Running
- Got Github working w/ Desktop

### Problems Encountered
-None

## Questions for class
1. None

## Week 2: Buffer7 Resistors + BOM Start

### Date
-9/4

### Files created or Updated
- /kidcad/low_cost_benchtop_ph_meter/ #Featherwing project page containing schematic, pcb, etc
- /kicad/low_cost_benchtop_ph_meter/128LM/ #From Digikey's archive
- /bom/buffer7_bom_v0.csv
- /docs/week2_buffer7_annotations.png
- /Screenshots/Week2

### Components Identified
- Listed in BOM

## Gain-setting table interpretation
1. Gain = R3/R4. Gain of 1 indicates no need for either R3 or R4, just a "0 ohm" resistor to drive current.
2. Gain of 10 is 9.1k / 1.01k. 
3. Gain of 20 is 9.5k / 500. 
4. ZERO means a 0 ohm resistor
5. OMIT means no need for any component there other than wire/trace.
6. Multiple gains is good for testing/troubleshooting, and also multiple applications
7. unity gain is good for testing/troubleshooting before attempting to get accurate gains. Also to evaluate the rest of the system's noise level before amplifying.

# Understanding
- I now understand the base of our circuit

# Questions for class
- Will we be able to revise all components (including the resistors we just put in our BOM) later?
- What was the output/test header (part 5 of worksheet) for?

## Week 3: GitHub + KiCad version

### Date
-9/11

# Capacitor Components identified on schematic annotations (screenshots folder)

### RC Filter vs power rail decoupling (packet has detailed answers)
- The schematic does not showa clear signal path RC filter
- Power rail decoupling is needed to stabilize the Vin values for the OPAMP (and there is no clear resistor)
- Capacitance in line with the ph probe would create a competing signal, which is completely unecessary

### Decoupling interpretation
- Power rail capacitors are C1 and C2. They stabilize the voltage that goes to the op amp by removing spikes
- supply might spike when it gets turned on or if connections arent great or if the battery is in harsh condition
- Settling the voltage makes it safer to put into the opamp
- We dont want leakage current anywhere near the raw signal because it is such a low magnitude. And possibly also nowhere near the output signal cause its only getting amplified by 20x maximum.
- we want to avoid creating unwanted stray capacitance between other components of the circuit, meaning we should isolate the main signal line as much as possible. 
- We dont want capacitors in line with anything they dont need to be so that we dont accidentally induce Voltages where we dont want them. 

# 5
a) A signal path RC filter filters noise out of a signal that we want to read afterwards. The power rail decoupling is to filter noise out of the power rail BEFORE it goes into a sensitive component, such as an OPAMP.
b) in packet
c) 1/2piRC
d-j) in packet

### BOM updates
- Capacitors

## I now understand unwanted Capacitor effects, and inductor common uses (back emf purposes)

## I am still unsure about the Op-Amp configuration

# Questions for class
- Why are we guarding just the initial Op Amp input line and not also lines 2/6?
- what is the relationship between lines 2 and 6 and how do they create the amplification?

## Week 4: buffer7 connector and bom v2

### Date
-9/18

# Capacitor Components identified on schematic annotations, buffer7 notations shown in screenshot (images folder)

### Component Questions
-J1, a and b, BNC connection/connector can shield the signal from the ph probe
-J2, c and d, BNC out is for routing the signal to an oscilliscope. Now it is a pinout instead because it will go to a microcontroller
-J3, e and f, connects battery power and the rest of the circuit. the +-9V seems to come from the battery, which connects to J3
-S1, g, controls the battery usage either to be on, off, or testing to see if the battery has over 11V of voltage difference. 
-BAT TEST nodes, h, BAT TEST 1 and 2 are the nodes that the switch goes to when it wants to see if battery charge is more or less than 11V
-Battery holder, Enclosure, Standoffs,lightpipe , i, they may or may not still be the same as before, depending on the design of the new pcb. it may need a smaller enclosure, not need a lightpipe, and need different standoffs.
-microcontroller, j, a lot of the decisions still need to be made. such as how to handle output signal and battery test.

### Component Necessary
-J1, keep
-J2, change
-J3, keep?
-S1, keep?
-Battery holder, keep
-BAT TEST nodes, keep
-Enclosure, keep?
-Standoffs, keep?
-lightpipe, likely dont need anymore

## Questions for class
- Is it okay to decide to remove the lightpipe now? Or should I put it in the BOM and decide later? Does it matter as long as I know it is an option?
- Arent we making a hat for the featherwing ("feather")? Wont that require a weird pinout/BNC structure that requires us to change out almost all these BNC/holder/standoff components?