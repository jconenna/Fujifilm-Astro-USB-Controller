# Fujifilm-Astro-USB-Controller

USB Serial shutter release device for Fujifilm cameras, geared towards **Astrophotography** use.

![Assembled PCB with 3d Printed Case](https://github.com/jconenna/Fujifilm-USB-Shutter-Release/blob/main/Image_1.jpg?raw=true)


## Description
This device was made in response to a lack of tethering options for Fujifilm cameras for **Astrophotography control**, though it can be used for general shutter release needs with manual lenses or lense with autofocus disabled.
This device allows a compatible Fujifilm camera to be controlled by [digiCamControl](http://digicamcontrol.com/) software (free, MS Windows) with its "Astro" intervalometer mode, which allows for autoguiding a mount between frames using [PHD2](https://openphdguiding.org/) software which interoperates with digiCamControl.</br>

The device was made using common, inexpensive, and easy to assemble parts that can be sourced from places like Amazon, Ebay, Sparkfun, and others.</br>

An optoisolator isolates the 5V Computer side circuit from the shutter release camera side of the circuit, providing added safety. 

## Theory of Operation
This device works by using software on a computer to control the RTS signal of an RS-232 connection (USB to Serial Converter in this case). The RTS signal from the Converter used here is inverted using a transistor since it comes from the FTDI chip inverted (cannot change EEPORM setting of **this** converter). When the signal reaching the optoisolatr is asserted it turns on the internal IR LED whose photons turn on the internal IR Photodiode, thereby connecting the Shutter/Focus pins to the Ground pin of the shutter release cable. For Fujifilm cameras I was targeting it was noted from inspection of commercial shutter release products that a successful shutter release depends on activating the focus pin before the shutter pin.

You **may** be able to use this device with other camera control software that has a "Serial Shutter Release" option that uses the RTS signal to trigger a camera. 

This has been tested working with an X-T100 and X-S10, and may work with other similarly controlled Fujifilm cameras (e.g. X-T#, X-T##, X-E#,X-T###, X###C, etc.) If you try this and it works for your camera let me know so I can build a compatability list.

For astrophotography it has been tested working with an X-T100, camera lens, and Star Adventurer guided with a small guide camera and guide scope.

## What's Included
Included are the Eagle PCB files for ordering a board. Boards can be [purchased from OSH Park](https://oshpark.com/shared_projects/9drAsv7N) for around $11 for 3 boards. If you choose to order elsewhere, the 3D files are designed for a PCB thickness of 63mil (1.6mm).

Included are two stl files for 3D printing a case. This contains a top and bottom piece that snap together and can be easily printed without supports by a wide variety of printers. I used PLA with default printed settings. 

![Device Inside 3D Printed Case](https://github.com/jconenna/Fujifilm-USB-Shutter-Release/blob/main/Image_2.jpg?raw=true)

## Bill of Materials:
1 - FT232RL USB to TTL Serial Converter module (red PCB with Mini USB female connector)<br/>
1 - PJ-307 3.5 mm Audio Jack Connector PCB Mount Female Socket 5 Pin<br/>
1 - 4N25 Optoisolator (6 pin DIP, white)<br/>
1 - 2N2222 NPN Transistor (TO-92 package)<br/>
2 - 1 kOhm Axial Resistor (common through hole resistor)<br/>
1 - 50 Ohm Axial Resistor (common through hole resistor)<br/>

## In addition you will need:
1 - A-Male to Mini-B USB, length of your choice<br/>
1 - 3.5mm Audio Cable, length of your choice<br/>
1 - 3.5mm Female to 2.5mm Male adapter, preference to short cable type with right angle 2.5mm connector<br/>
OR 1 - 3.5mm male to 2.5mm male Audio cable<br/>

## Tutorial
*Soon to come is a tutorial for assembly, and use with digiCamControl.
