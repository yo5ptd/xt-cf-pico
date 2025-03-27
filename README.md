# xt-cf-pico   (needs testing when first boards arrive from jlpcb)
8-bit ISA interface for Compact Flash cards with a single CPLD  

## Introduction

XT-CF-Pico is a remake of Sergey Kiselev  [xt-cf-lite-v4]  efectively reverting glue logic IC back to CPLD but still using through hole components. This card allows connecting a Compact Flash (CF) card to computers with ISA bus and using it as a mass storage device. The card also supports BIOS extension ROM.

* 16 KiB EEPROM (28C128) with either 8 or 16k images, no flash ROM.
* no jumpers, everything you configure in the PLD (GAL20V8, still available on Aliexpress, used in projects like C64 PLA20V8)

This is my first ISA board and first PLD design, it should work only in theory, but not yet tested, so use at your own risk!

## Hardware Documentation
The idea was to use components that were available late '80s, keeping Sergey's idea of having them all through hole (except of course the CF adapter).

### Schematic and PCB Layout

[Schematic](KiCad/XT-CF-Pico-Schematic.pdf)

[PCB Layout](KiCad/XT-CF-Pico-Board.pdf)


### Bill of Materials

Component Type | Reference | Description                             | Quantity | Possible Sources and Notes
-------------- | --------- | --------------------------------------- | -------- | --------------------------
PCB            |           | XT-CF-Pico 	                           | 1        | jlpcb
Capacitor      | C1        | 0.1 uF ceramic, 5.0 mm lead spacing     | 1        | 
Capacitor      | C2 	     | 10 uF electrolytic, 6.3 mm lead spacing | 1        | 
LED            | D1        | 5 m (T-1) LED indicator                 | 1        | You can use 2 pin jumper holder for external led
Connector      | P1        | Compact Flash Card connector            | 1        | 101D-TAAA-R01 from ATTEND  (this was the cheapest now, footprint was updated)
Resistor       | R1        | 470 Ohm, 1/4 W                          | 1        | Mouser 291-470-RC
Resistor       | R3        | 1 kOhm, 1/4 W                           | 1        | Mouser 291-1K-RC
Resistor       | R4        | 5.6 kOhm, 1/4 W                         | 1        | Mouser 291-5.6K-RC
Resistor       | R2        | 10 kOhm, 1/4 W                          | 0        | Note: Do not install, kept for historic reasons only (card present detection?)
IC             | U1        | 27C128 EEPROM                           | 1        | mbm27c128
IC Socket      | U1        | 28 pin 600 mil (wide) DIP socket        | 1        | optional
IC Socket      | U2        | 24 pin 300 mil (narrow) DIP socket      | 1        | optional
