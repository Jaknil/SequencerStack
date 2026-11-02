# What is it
A bare bones digital signal sequencer. Used to make music loops on homemade instruments. One channel per card and a common clock card.

# Use case

I want it to run my Pipe Organ, I have a 12 valve manifold ready to go. It takes 24VDC. I can probably use optocouplers to level shift up to 24V, but I Need to check the current draw.

- [Pneumatic pipe organ- First test](https://youtube.com/shorts/L7J5WPEUMWw?si=k-WOeQEzKxhjgEyd)


## Inspiration 

Build 12 of these and stackt them:
- [Moriz Kleins Super simple drum sequencer (4 parts)](https://www.youtube.com/shorts/7boGHtppE2U)


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
