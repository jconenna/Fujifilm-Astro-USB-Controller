# Fujifilm-Astro-USB-Controller

USB Serial shutter release device for Fujifilm cameras, geared towards **Astrophotography** use.

![Assembled PCB with 3d Printed Case](https://github.com/jconenna/Fujifilm-Astro-USB-Controller/blob/main/images/Image_1.jpg?raw=true)


## Description
This device was made in response to a lack of tethering options for Fujifilm cameras for **Astrophotography control**, though it can be used for general shutter release needs with manual lenses or lenses with autofocus disabled.</br>

This device allows a compatible Fujifilm camera to be controlled by [digiCamControl](http://digicamcontrol.com/) software (free, MS Windows) with its "Astro" intervalometer mode, which interoperates with [PHD2](https://openphdguiding.org/) software, allowing for autoguiding a mount between frames.</br>

The device was made using common, inexpensive, and easy to assemble parts that can be sourced from places like Amazon, Ebay, Sparkfun, and other retailers.</br>

An optoisolator isolates the 5V Computer side circuit from the shutter release camera side of the circuit, providing some added safety.</br>

This has been tested working with an X-T100 and X-S10, and should work with other similarly controlled Fujifilm cameras (e.g. X-T#, X-T##, X-E#,X-T###, X###C, etc.) If you try this and it works for your camera let me know so I can build a compatability list.</br>

This device has been tested working with some Canon cameras that use the 3 pin shutter release, though I am marketing this for Fujifilm folks since there is no BackyardFuji or other tethering option for most cameras.</br>

For astrophotography use with digiCamControl software, it has been tested working with an X-T100, camera lens, and Star Adventurer mount guided with PHD2 using an ASI120MM-Mini guide cam and 30mm guide scope.</br>

You **may** be able to use this device with other camera control software that has a "Serial Shutter Release" option that uses the RTS signal to trigger a camera. </br>

## Theory of Operation
This device works by using software on a computer to control the RTS signal of an RS-232 connection (USB to Serial Converter in this case). The RTS signal from the Converter used here is inverted using a transistor since it comes from the FTDI chip inverted (cannot change EEPORM setting of **this** converter). When the signal reaching the optoisolatr is asserted it turns on the internal IR LED whose photons turn on the internal IR Photodiode, thereby connecting the Shutter/Focus pins to the Ground pin of the shutter release cable, closing the camera shutter.</br>
From inspection of commercial shutter release products for Fujifilm cameras, it was found that a successful shutter release depends on activating the focus pin before the shutter pin. For astrophotography a telescope or manually focused lens is used, so simultaneously activiating the focus and shutter pins successfully closes the shutter on the camera.</br> 






## What's Included
Included are the Eagle PCB files for ordering a board. Boards can be [purchased from OSH Park](https://oshpark.com/shared_projects/9drAsv7N) for around $11 for 3 boards. If you choose to order elsewhere, the 3D files are designed for a PCB thickness of 1.5-1.6mm.

Included are two stl files for 3D printing a case. This contains a top and bottom piece that snap together and can be easily printed without supports by a wide variety of printers. I used PLA with default printed settings on an Ender 3 Pro printer. 

![Device Inside 3D Printed Case](https://github.com/jconenna/Fujifilm-Astro-USB-Controller/blob/main/images/Image_2.jpg?raw=true)

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

#### Assembly

[Here is a video showing from start to finish how I solder the components to the board.](https://youtu.be/rFp3plmKMuA)

#### Use with digiCamControl

1. [Download FTDI drivers here](https://cdn.sparkfun.com/assets/learn_tutorials/7/4/CDM21228_Setup.exe), or visit [FTDI's VCP Drivers page](https://ftdichip.com/drivers/) for the latest download of the Windows FTDI Driver executable.
2. Install the drivers using the executable file.
3. Open Windows Device Manager (Win-R, devmgmt.msc, OK).
4. Plug in the Fujifilm-Astro-USB-Controller device using the USB Mini cable.
5. Click the drop-down arrow for **Ports** and note "USB Serial Port" device. Right-click, properties, and note Manufacturer: FTDI. 
6. Note the COM number assigned to the device, in this case COM7.</br>
![COM Port](https://github.com/jconenna/Fujifilm-Astro-USB-Controller/blob/main/images/capture_1.JPG?raw=true)
7. Download the latest stable version of [digiCamControl](http://digicamcontrol.com/download) and install.
8. Open digiCamControl.
9. Go to File > Settings.
10. In the popup window click on Devices, under available devices click Add.
11. Name the device under Configuration, set the driver as **Serial Port Shutter Release**, and Com Port to the COM port of the device.</br>
![Device Setup](https://github.com/jconenna/Fujifilm-Astro-USB-Controller/blob/main/images/capture_2.JPG?raw=true)
12. Click Ok in the bottom left of the Settings window to exit.
13. On the top toolbar click on the Astronomy button.</br>
![Astronomy Button](https://github.com/jconenna/Fujifilm-Astro-USB-Controller/blob/main/images/capture_3.JPG?raw=true)
14. In the popup BULB window, under the **External shutter release** menu, select enable and chose the device you just set up.</br>
![Chose device](https://github.com/jconenna/Fujifilm-Astro-USB-Controller/blob/main/images/capture_4.JPG?raw=true)
15. Set the imaging session parameters:</br>
![Bulb settings](https://github.com/jconenna/Fujifilm-Astro-USB-Controller/blob/main/images/capture_5.JPG?raw=true)
16. Set **Capture time** value in seconds.
17. Set **Number of photos** to set how many frames to capture before stopping.
18. Set **Time between shots** value in seconds. For non guided imaging I usually set this to 5.
19. If guiding with PHD2, open, setup, and begin guiding with PHD2. **If not guiding skip to Step 21.**
- Set **PHD Guiding** from (None) to Move1 - Move5 (Dither a random amount, up to +/- [0.5, 1.0, 2.0, 3.0, 5.0] x dither scale)
20. Set **Wait for PHD** to 20 seconds. This value will depend on how long it takes starting from when the shutter closes, ending after a dither in PHD2 and the guiding is stabalized. For me 20 seconds was sufficient, but you may test to get a feel for this value. You could also set this value to 0 and set **Time between shots** to the necessary amount of time.</br>
21. Connect the shutter release cable from the Camera to the Fujifilm-Astro-USB-Controller device.
22. Turn on your device, set ISO, and put it in BULB mode. If camera is asleep, wake up with half shutter press.
23. To begin imaging click Start Capture.
24. If nothing happens and the BULB window shows "Error Shutter Access to the port is denied", turn off the camera, unplug and replug the Fujifilm-Astro-USB-Controller device, turn on the camera, press Start Capture again and it should work.

Some notes:</br>
If the camera falls asleep before you start imaging you will have to wake it up with a button press before you begin.

