# xt-cf-pico   (work in progrss)
8-bit ISA interface for Compact Flash cards with a single CPLD  (TODO: PLD and JED files need writing)

## Introduction

XT-CF-Pico is a remake of Sergey Kiselev  [xt-cf-lite-v4]  efectively reverting glue logic IC back to CPLD but still using through hole components. This card allows connecting a Compact Flash (CF) card to computers with ISA bus and using it as a mass storage device. The card also supports BIOS extension ROM.

* 16 KiB EEPROM (28C128) with either 8 or 16k images, no flash ROM.
* no jumpers, everything you configure in the CPLD (GAL20V8, still available on Aliexpress, used in projects like C64 PLA20V8)

## Hardware Documentation
The idea was to use components that were available late '80s

### Schematic and PCB Layout

[Schematic](KiCad/XT-CF-Pico-Schematic.pdf)

[PCB Layout](KiCad/XT-CF-Pico-Board.pdf)


### Bill of Materials

Component Type | Reference | Description                             | Quantity | Possible Sources and Notes
-------------- | --------- | --------------------------------------- | -------- | --------------------------
PCB            |           | XT-CF-Pico 	                     | 1        | jlpcb
Capacitor      | C1        | 0.1 uF ceramic, 5.08 mm lead spacing    | 1        | 
Capacitor      | C2 	   | 10 uF ceramic, 5.08 mm lead spacing     | 1        | 
LED            | D1        | 5 m (T-1) LED indicator                 | 1        | 
Connector      | P1        | Compact Flash Card connector            | 1        | 101D-TAAA-R01 from ATTEND 
Resistor       | R1        | 330 Ohm, 1/4 W                          | 1        | Mouser 291-330-RC
Resistor       | R2        | 470 Ohm, 1/4 W                          | 1        | Mouser 291-470-RC
Resistor       | R3        | 1 kOhm, 1/4 W                           | 1        | Mouser 291-1K-RC
Resistor       | R4        | 5.6 kOhm, 1/4 W                         | 1        | Mouser 291-5.6K-RC
Resistor       | R5        | 10 kOhm, 1/4 W                          | 0        | Note: Do not install
Resistor Array | RR1       | 10 kOhm, 6 pin, bussed resistor array   | 1        | Mouser 264-10K-RC
Resistor Array | RR2       | 10 kOhm, 10 pin, bussed resistor array  | 1        | Mouser 266-10K-RC
IC             | U1        | 27C128 EEPROM                           | 1        | mbm27c128
IC             | U2, U3    | 74LS688 magnitude comparator            | 2        | Mouser 595-CD74HCT688E, 771-74HCT688N, 595-SN74LS688N, 595-SN74LS688NE4
IC             | U4        | 74LS32 quad 2-input OR gate             | 1        | Mouser 595-SN74ALS32N, 512-DM74ALS32N, 595-SN74AHCT32N
IC             | U5        | 74LS04 hex inverters                    | 1        | Mouser 595-SN74ALS04BNE4, 595-SN74ALS04BN, 595-SN74AHCT04NE4
IC Socket      | U1        | 28 pin 600 mil (wide) DIP socket        | 1        | Mouser 517-4828-6000-CP. Note: U4 socket is only required for BIOS extension ROM function
IC Socket      | U2, U3    | 20 pin 300 mil (narrow) DIP socket      | 2        | 
IC Socket      | U4, U5    | 14 pin 300 mil DIP socket               | 2        | Mouser 517-4814-3000-CP
