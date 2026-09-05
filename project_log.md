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