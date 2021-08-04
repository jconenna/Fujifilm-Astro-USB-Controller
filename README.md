# Fujifilm-USB-Shutter-Release

![Assembled PCB with 3d Printed Case](https://github.com/jconenna/Fujifilm-USB-Shutter-Release/blob/main/Image_1.jpg?raw=true)

USB Serial shutter release device for Fujifilm cameras. 

## Description
This device was made in response to a lack of tethering options for Fujifilm cameras for Astrophotography control, though it can be used for general shutter release needs.
This device allows a compatible Fujifilm camera to be controlled by [digiCamControl](http://digicamcontrol.com/) software (free, MS Windows) with its "Astro" intervalometer mode, which allows for autoguiding a mount between frames using [PHD2](https://openphdguiding.org/) software which interoperates with digiCamControl.

This has been tested working with an X-T100 and X-S10, and may work with other similarly controlled Fujifilm cameras (e.g. X-T#, X-T##, X-E#,X-T###, X###C, etc.) If you try this and it works for your camera let me know so I can build a compatability list.

For astrophotography it has been tested working with an X-T100, camera lens, and Star Adventurer guided with a small guide camera and guide scope.

## What's Included
Included are the Eagle PCB files for ordering a board. Boards can be [purchased from OSH Park](https://oshpark.com/shared_projects/9drAsv7N) for around $11 for 3 boards. If you choose to order elsewhere, the 3D files are designed for a PCB thickness of 63mil (1.6mm).

Included are two stl files for 3D printing a case. This contains a top and bottom piece that snap together and can be easily printed without supports by a wide variety of printers. I used PLA with default printed settings. 

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
