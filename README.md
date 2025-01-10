# Marlin Firmware for Anet A8 3D printer with BIGTREETECH SKR V1.3

This repository contains the Marlin firmware for an Anet A8 with a BTT SKR V1.3 motherboard.

  - `Marlin version`: 2.1.2.5
  - `Stepper motor drivers`: TMC2130 (SPI mode)
  - `Screen`: Original LCD screen with working keypad :warning: requires an hardware modification to not damage the motherboard (see below) :warning:
  - `Micro SD card`: allows updating the firmware and to print from SD card
  - `Language`: compiled files for English and French, for other languages you will need to compile the firmware
  
## Motherboard

Follow the BIGTREETECH SKR V1.3 documentation to set the jumpers on the motherboard accordingly.

The stepper motor drivers must be configured to work in SPI mode (may require soldering if not pre-configured correctly).

Wiring connectors needs to be adjusted for the motherboard.

## LCD screen

As the analogue pin of the LPC1768 are not 5V tolerant, you need to modify the screen to not damage the motherboard. I cut the 5V trace going to the keypad and soldered a 3.3V regulator (AZ1117CH-3.3TRG1) with its required capacitors (22uF) (see picture below). With this modification, the voltage for the keypad is 3.3V while the LCD screen is still powered with 5V.

PICTURE

You will also need to modify the wiring of the ribbon cable. For that, I added dupont wires on one side to keep the original ribbon cable.

PICTURE

Before connecting the screen to the motherboard, check the wiring and voltage of the keypad with a multimeter. Ideally, test the screen with a lab power supply to do your measurements.

## Upload the firmware

Copy the file (`` or ``) and put it on a micro SD card. Insert the micro SD while the 3D printer is powered off and the firmware will be updated at the next startup.

## Compile the firmware

Download Marlin 2.1.2.5 (or newer non-major release), and replace the configuration files by the ones of this repository.
Install platformio, compile, and copy the file `.pio/build/LPC1768/firmware.bin` to the micro SD card.


Romain THOMAS 2025
