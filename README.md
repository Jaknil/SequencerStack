# What is it
A bare bones digital signal sequencer. Used to make music loops on homemade instruments. One channel per card and a common clock card.

# Motivation

I want it to run my Pipe Organ, I have a [12 valve pneumatic manifold ready to go.](Images/manifold_and_cable.jpg)

- [Pneumatic pipe organ- First test](https://youtube.com/shorts/L7J5WPEUMWw?si=k-WOeQEzKxhjgEyd)

I considered using Siemens logo PLCs but it doesn't seem well suited. ([See Use-A-PLC?](#use-a-plc) or [Use-A-Microcontroller](#use-a-microcontroller)) I want to prioritize working with my hands and avoid sitting infront of a computer for much of the project.

## Inspiration 

Build 12 of these and stackt them:
- [Moriz Kleins Super simple drum sequencer (4 parts)](https://www.youtube.com/shorts/7boGHtppE2U)

Possibly use double length shift registers for 16 bit resolution.

## Electronic strategy

# BOM
- Shift registers
- (555)-Timer
- Potentiometer to control loop lenght
- LEDs to view the queue (optional but fun, makes it a ton of work.)

### Card pins
- Switch signal in
- Note signal out

### Master pins
- Clock speed
- Reset all
- Scan on/off
- VCC
- GND

### Common pins stack
- Clock
- Reset all
- VCC
- GND

### Open questions

- Will it have Clear 1 channel memory feature (uniqe button or combo press?)
- 24V output on card or not, selectanble? Transistor output might be good. Remember freewheel diodes.

Optocoupler option:
- [Solid state relay, optocoupler TOP 5VDC/48VDC 0,5A](https://eshop.weidmueller.com/en/top-5vdc48vdc-05a/p/8950960000)


Thoughts
- Shared input and output pin would be cool but there is a significant risk of self latching. Perhaps if the out is 5V and stepped up later through an input that takes many different voltages like the optocoupler?

## Use a PLC?
I have made a LogoSoft progam with 4 shift registers to test the general idea. Seems to work fine. But the software caps the use of shift registers at 4, which is insulting. I probably need 24. I can make my own shift registers with gates and put them in UserDefinedFunctions but the scan speed of the Logo-programs is potentially silly slow, I read specs of 22-30ms so its not promising. Might do it anyway as an exercise. I HMI would have to be used to display the queues, it does not have enough IOs.  
  - [Jpg of Code](Images/logo_4_standard_shifts.jpg)
  - [LogoSoft code](Shift_register_Organ_4_standard_regs.lsc)

## Use a microcontroller?
I could use an arduino and code the shift registers. But if I wanted the queue visualisation it would require programming graphics on a screen or adding shift registers for up to ~200 leds which sounds like a detour compared to just using them directly.