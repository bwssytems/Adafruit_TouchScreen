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
```
int XP=12,XM=15,YP=33,YM=13;
```
Also, you must restore the analog and digital pins used to read touch to be able to continue writing:
```
  TSPoint tp = <TouchScreen>.getPoint();
  pinMode( YP, OUTPUT); //restore shared pins
  pinMode( XM, OUTPUT);
  digitalWrite( YP, HIGH); //because TFT control pins
  digitalWrite( XM, HIGH);
```
Then the point must be mapped based on the calibration parameters recevied. An example here is of a 240x320 display.
```
// PORTRAIT  CALIBRATION     240 x 320
int TS_LEFT=516,TS_RT=3677,TS_TOP=3691,TS_BOT=56; //PORTRAIT Example
x = map(p.x, TS_LEFT=516, TS_RT=3677, 0, 240)
y = map(p.y, TS_TOP=3691, TS_BOT=56, 0, 320)

// LANDSCAPE CALIBRATION     320 x 240
int TS_LEFT=3691,TS_RT=56,TS_TOP=3677,TS_BOT=516; //LANDSCAPE Example
x = map(p.y, TS_LEFT=3691, TS_RT=56, 0, 320)
y = map(p.x, TS_TOP=3677, TS_BOT=516, 0, 240)
```

## Installing

Download and install the library using your IDE, eg Arduino. 

## Using

No changes are required to existing sketches, just recompilation.

Compatible with both [TFT_eSPI](https://github.com/Bodmer/TFT_eSPI) library.

Touchscreen needs to be calibrated before use, either manually using included [ESP32testTouch](examples/ESP32testTouch) or eg  [TouchScreen_Calibr_native](https://github.com/prenticedavid/MCUFRIEND_kbv/tree/master/examples/TouchScreen_Calibr_native)
