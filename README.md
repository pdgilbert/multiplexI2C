# multiplexI2C
Multiplexed 4-wire screw down connectors on I2C with PCA9548A. This allows connecting 
I2C sensors such as AHT10 (on module boards) using low voltage 4-wire cable.

##  Status: Prototype.

## Summary

Kicad project WIP.

PCB design to connect multiple (up to 8) I2C sensors (eg. AHT20) to a I2C multiplexer
connecting to an MCU. Connectors are  4-pin KF128-2.54-4P generic screw terminals.
Many types of I2C sensors are inexpensive and easily available, 
but 4-wire cable will typically need to be attached. 
The MCU socket is arranged for a blackpill module.

The module has a LoRa radio on a SPI bus which transmits measurement results.
There is also a I2C header for an optional OLED display, intended mainly for debugging.

Related software is in repository https://github.com/pdgilbert/SensorProject_th8.

The `.png` files are produced from kicad  in the `3D Viewer`  with `File > Export Current View as PNG`.
![alt text](Graphics/multiplexI2C_top1.png)

![alt text](Graphics/multiplexI2C_top2.png)

![alt text](Graphics/multiplexI2C_bottom1.png)

( hints from https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#3d-file-viewer )

3D  `.wrl` file opens with Meshlab. Good, full colour. The file needs to be download and then viewed. 
To download go to the file in the Graphics/ directory and click on the file.
Github will try to render this, but fails because it is too large.
Then click on the download raw file icon at the top right. 
The file is produced from kicad  with `File > Export ... >  VRML...`
![.wrl file](Graphics/multiplexI2C.wrl)

3D  `.step` file can be loaded by Freecad. It can be downloaded as above for `.wrl`.
The file is produced from kicad  with `File > Export ... >  STEP...`
![.step file](Graphics/multiplexI2C.step)

3D  `.stl` file can be  rendered by Github, Meshlab and Freecad. So far only mono-colour is working. 
To render by Meshlab or Freecad requires downloading as above for `.wrl`.
The file can be produced from kicad by exporting a `.wrl` or `.step` file, 
importing that to Meshlab or Freecad, and then exporting to `.stl`
![.stl file](Graphics/multiplexI2C.stl)

3D  `.ast` file (ASCII stl) is rendered by Github, according to above link, but files  
larger than 10 MB are too big for GitHub to display. 
The `multiplexI2C.ast` is almost 20MB so this format cannot be used by Github.
It is not rendered by Meshlab.
![.ast file](Graphics/multiplexI2C.ast)

## History

 - Version 0.1.1 2025-01 has pull up resistor added but has not been manufactured/tested.

 - Version 0.1.0 2024-09 needs manual addition of pull up resistors on nss line to radio chip. 
   With this modification it works with `blackpill` `stm32f401` or `stm32f411` inserted,
   using AHT20 sensors. See notes re testing in the software repository.
