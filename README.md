# Adafruit TouchScreen with mod for ESP32 UNO

This is the 4-wire resistive touch screen firmware for ESP32 only.

## Reason for Modification

ESP32 has different ADC read values than Arduino.

## Prerequisites

After the PARALLEL wiring is determined with TFT_eSPI.

Determining Wiring for YP, YM, XP and XM:

Touch Defines | Display |
--------------|---------|
YP |   CS |
XM |   RS |
YM |    D1 |
XP |    D0 |

## Installing

Download and install the library using your IDE, eg Arduino. 

## Using

No changes are required to existing sketches, just recompilation.

Compatible with both [TFT_eSPI](https://github.com/Bodmer/TFT_eSPI) library.

Touchscreen needs to be calibrated before use, either manually using included [ESP32testTouch](examples/ESP32testTouch) or eg  [TouchScreen_Calibr_native](https://github.com/prenticedavid/MCUFRIEND_kbv/tree/master/examples/TouchScreen_Calibr_native)
