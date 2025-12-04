# multiplexI2C
4-position screw connectors on multiplexed on I2C with PCA9548A. 
This allows connecting I2C sensors such as AHT10 (on module boards) using 
low voltage 4-wire cable.

##  Status: Prototype.

## Summary

Kicad project WIP.

PCB design to connect multiple (up to 8) I2C sensors (eg. AHT20) to a I2C multiplexer
connecting to an MCU. Sensor connectors are  4-pin KF128-2.54-4P generic screw terminals.
Many types of I2C sensors are inexpensive and easily available on module boards, 
but 4-wire cable will typically need to be attached. 

The pcb board has a LoRa radio on a SPI bus which transmits measurement results.
There is also a I2C header for an optional OLED display, intended mainly for debugging.

Related software is in repository https://github.com/pdgilbert/SensorProject_th8.

As of December 2025, this repository has three important branches. (Branch `main` is not 
an important branch but rather a somewhat stable version of the most active
development, which is on the `dev` branch. Both may be removed or reorganized 
in the future.)
 
Branch `blackpill-socket` has two 20-pin sockets arranged for a commonly available 
blackpill module. It has an RFM95 LoRa radio on spi, an I2C pinsocket arrange to plug in 
an SSD module for display, and 8 4-pin terminals multiplexed to connect I2C devices.
The pinsocket arrangement can also be used for jumper-wiring MCUs on other development
boards. Further work on this branch will be limited.
 
Branch `f411-RFM95W-module` has a footprint for a module with an MCU and LoRa radio.
(See repository MCU-LoRa for module details.)
It has a socket for I2C arranged to plug in an SSD module for display, 
and 8 4-pin terminals multiplexed to connect I2C devices. 
As of November 2025 this branch is almost ready to manufacture a prototype.
 
Branch `f411-RFM95W` has an STM32F411 MCU and RFM95W LoRa radio on the board (no module).
It has a socket for I2C arrange to plug in an SSD module for display, 
and 8 4-pin terminals multiplexed to connect I2C devices. 
As of December 2025 this branch is almost ready to manufacture a prototype.

See history further below for regarding status and testing of each branch.

Graphics below will be different on different branches, reflecting the differences above.
The `.png` files below are produced from kicad  in the `3D Viewer`  
with `File > Export Current View as PNG`.
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
The file is best produced by exporting a `.wrl` or `.step` file from kicad and
importing that to Meshlab or Freecad, and then exporting an `.stl` file.
The file can also be produced from kicad  with `File > Export ... >  STEP.../STEP...` but
the result has bad artifacts. The .wrl version is much better than the .stl version.
![.stl file](Graphics/multiplexI2C.stl)

3D  `.ast` file (ASCII stl) is rendered by Github, according to above link, but files  
larger than 10 MB are too big for GitHub to display. 
The `multiplexI2C.ast` is almost 20MB so this format cannot be used by Github.
It is not rendered by Meshlab.
![.ast file](Graphics/multiplexI2C.ast)

## History
 
 - `th8-F411 version 0.3.1 2025-12 (`f411-RFM95W`) has not yet been manufactured/tested.
 - `th8-F411 version 0.3.2 2025-12 (`f411-RFM95W-module`) has not yet been manufactured/tested.

 - `Version 0.1.1 2025-01 (`blackpill-socket`) has pull up resistor added but 
   has not been manufactured/tested.

 - Version 0.1.0 2024-09 (`blackpill-socket`) needs manual addition of a pull up 
   resistor on nss line to the radio chip, MCU pin A4. 
   With this modification it works with `blackpill` `stm32f401` or `stm32f411` inserted,
   using AHT20 sensors. With jumper wiring it has also been used to test a WeAct 
   Studio STM32474G474 board. See notes re testing in the software repository.
