# About this Fork
This fork is a Marlin version, based on the original branch of MKS (board manufacturer), and was created to bring Marlin 2.0 with the easy configurability of Marlin implementation from l3tspeak to TwoTrees printers like the Sapphire Plus an Pro. This brings back the original GUI that originally came with your printer but with full configurability.

## Preconfigured printers:
- Sapphire Pro
- Sapphire Plus (Dual-Z and belt-synced versions)
- Bluer
- Sapphire Pro/Plus with E3D Hemera

As I own a Sapphire Plus with a Hemera, this will be the only tested version by myself. So be carefull with those other versions at the until you trust them. At least the software Z-Endstop of the Pro has to be adjusted. Please feel free to bring in your own modifications and do a pull-request or verify modifications I'm not able to verify.

![](https://github.com/makerbase-mks/Mks-Robin-Nano-Marlin2.0-Firmware/blob/master/Images/MKS_Robin_Nano_printing.png)

## Some hint before the installation
I am not responsible for bricked devices, dead SD cards, thermonuclear war, or having some unsupervised 3D-Printer (which probably does not match your countries electrical safety standarts anyway) burning down your house. I would recommend you to have at least your configured factory firmware ready, in case the firmware is maybe not working, as intended. 

YOU are choosing to make these modifications, and if you point the finger at me for messing up your device, I will laugh at you.

Do everything at your own risk! But it's probably worth it anyway huh?

## Installation on your Printer
If you do not have a clou, what VS-Code or PlatformIO is: This is the way for you!

You are going to find some precompiled firmware binaries under the section ["releases"](
https://github.com/RolfZuckowskiUltras/TwoTrees-Sapphire-Pro-Plus-Marlin2.0-with-GUI/releases) on this page. You will find a file named "Robin_nano35.bin" in the .zip, that is according to your machine. Just put that one onto a SD-Card. Put the card into your (switched off) machine and switch it on after that. Your machine will update itself (progress-bar is shown) and start the firmware after that. The Screen has to be calibrated at the first startup.

## About the mounting of the Hemera

The preconfigurations for the E3D Hemera [are optimized for this mount (Seems to work best)](https://www.thingiverse.com/thing:4435761). I remixed the mount for the useage of an EBM Pabst RLF35, beacause we can [(See Thingiverse)](https://www.thingiverse.com/thing:4578322). You have to also do some spacers between the platform and Z-endstops (See Photos of the RLF35 Mount). The cables of the Hemera are not long enougth. Just take the factory ones for that last part. Nobody wants to go back from a hemera anyway, right?

## Compile your own firmware
You can't find your particular firmware, just want to do some modifications or have I been to lazy to rebuilt the binaries (again)? Then go for it.
It's Marlin. You probably know how to work with it. To make life easier, the Firmware includes some precompiler definitions, inspired by user l3tspeaks ["TwoTrees Marlin 2.0 Firmware"](https://github.com/le3tspeak/Marlin-2.0.X-MKS-Robin-Nano).

There are some defintions in the Marlin `Configuration.h` and one further defintion in `Configuration_adv.h`. Definitions are
- `//#define SAPPHIRE_PRO`
- `//#define SAPPHIRE_PLUS`
- `//#define SAPPHIRE_PLUS_DUAL_Z `
- `//#define E3D_HEMERA`
- `//#define BL_TOUCH` 

Uncomment your personal machine and options, if needed. Only the function of the Sapphire Plus Dual Z with E3D Hemera is verified yet. The factory will probably work fine. The Hemera will work probably fine with the Sapphire Plus models. At that point you are going to find other features, like the neo-pixel implementation anyway...

As now (January 2021) All TwoTrees Printers seem to be delivered with the Robin Nano V1. It might be, that they switch to V2 or V3 in the meantime. Just a hint for troubleshooting...

Please also keep the direct information of the MKS repository in mind.

## You prefer the Stock Marlin over the lvgl GUI?
No Problem. [Take a look at this Repository](https://github.com/RolfZuckowskiUltras/Marlin-2.0.X-MKS-Robin-Nano). Same stuff, but with the stock Marlin UI. It's proven to be stable.

-------------------


# Mks-Robin-Nano-Marlin2.0-Firmware (Description of upstream repository...)
## Features
The firmware of MKS Robin Nano, based on [Marlin2.0.x](https://github.com/MarlinFirmware/Marlin), added the [LittlevGL](https://github.com/littlevgl/lvgl), supporting colourful GUI and touch screen. It is developed on PlatformIO, we hope more and more developers will participate the development of this repository.

![](https://github.com/makerbase-mks/Mks-Robin-Nano-Marlin2.0-Firmware/blob/master/Images/MKS_Robin_Nano_printing.png)

## Build
As the firmware is based on Marlin2.0.x which is built on the core of PlatformIO, the buid compiling steps are the same as Marlin2.0.x. You can directly using [PlatformIO Shell Commands](https://docs.platformio.org/en/latest/core/installation.html#piocore-install-shell-commands), or using IDEs contain built-in PlatformIO Core(CLI), for example, [VSCode](https://docs.platformio.org/en/latest/integration/ide/vscode.html#ide-vscode) and [Atom](https://docs.platformio.org/en/latest/integration/ide/atom.html). VSCode is recommended.

## About the gcode file preview
The images should be added to gcode file when slicing, and MKS has developed the [plugin for Cura](https://github.com/makerbase-mks/mks-wifi-plugin) to make it.

## About the image conversion
- Open [LVGL online image converter tool](https://lvgl.io/tools/imageconverter).
- Open bmp images.
- Enter the saved file name.
- Choose color format:True color.
- Choose file output format:Binary RGB565.
- Start convertion.
- Save bin file.
- Copy the converted bin file to the assets folder.
- Copy the assets folder to the SD card.
- SD card is connected to the motherboard, and you can see the update interface after powering on.

## Firmware Can be run on Robin Nano V1.x / V2.x boards and V3.x boards
## MKS Robin Nano V1.x build and update firmware

1. Build config:

- platformio.ini:

     default_envs = mks_robin_nano35    
- Configuation.h:  
     #define SERIAL_PORT 3  
     #define MKS_ROBIN_TFT35  
     #define MOTHERBOARD BOARD_MKS_ROBIN_NANO  
     #define TFT_LVGL_UI  
     #define TOUCH_SCREEN  

2. Update firmware:

- Enter the `.pio\build\mks_robin_nano35` directory, copy the `assets` folder and `Robin_nano35.bin` to the sd card
- Insert SD card to the motherboard, and you can see the update interface after power on.   

## MKS Robin Nano V2.x build and update firmware

1. Build config:

- platformio.ini:

     default_envs = mks_robin_nano35    
- Configuation.h:   
     #define SERIAL_PORT 3  
     #define MKS_TS35_V2_0  
     #define MOTHERBOARD BOARD_MKS_ROBIN_NANO_V2     
     #define TFT_LVGL_UI  
     #define TOUCH_SCREEN  

2. Update firmware:
   
- Enter the `.pio\build\mks_robin_nano35` directory, copy the `assets` folder and `Robin_nano35.bin` to the sd card
- Insert SD card is to the motherboard, and you can see the update interface after power on.   

## MKS Robin Nano V3.x build and update firmware

1. Build config:
     
- platformio.ini: 
     
     default_envs = mks_robin_nano_v3_usb_flash_drive_msc
- Configuation.h:   
     #define SERIAL_PORT -1  
     #define MKS_TS35_V2_0  
     #define MOTHERBOARD BOARD_MKS_ROBIN_NANO_V3     
     #define TFT_LVGL_UI  
     #define TOUCH_SCREEN

- Configuation_adv.h:    
     Now you can either use the TF card or USB disk, use TF card:   
    // #define USB_FLASH_DRIVE_SUPPORT  
    Use USB disk:  
     #define USB_FLASH_DRIVE_SUPPORT  

2. Update firmware:
   
- Enter the `.pio\build\mks_robin_nano35` directory, copy the `assets` folder and `Robin_nano_v3.bin` to the sd card or usb disk
- Insert sdcard or usb disk to the motherboard, and you can see the update interface after power on.  

3. Example build config:

- [Open the example configuration file](https://github.com/makerbase-mks/Mks-Robin-Nano-Marlin2.0-Firmware/tree/master/config/MKS%20Robin%20nano%20v3.0).
- Modify the parameters, replace configuration.h and configuration_adv.h in the Marlin path of the source code.
- Compile the firmware.

4. Prebuilt *.bin firmware for update

- We have prebuilt the robin nano v3 [firmware](https://github.com/makerbase-mks/MKS-Robin-Nano-V3.X/tree/main/firmware/Marlin-bugfix2.0.x-MKS-2.1.2) for some type of printers and some extended usage. 


## For more function configuration, please refer to Robin nano series Wiki
- [MKS Robin Nano V1.x Wiki](https://github.com/makerbase-mks/MKS-Robin-Nano-V1.X/wiki). 
- [MKS Robin Nano V2.x Wiki](https://github.com/makerbase-mks/MKS-Robin-Nano-V2.X/wiki). 
- [MKS Robin Nano V3.x Wiki](https://github.com/makerbase-mks/MKS-Robin-Nano-V3.X/wiki).

## More information about the Robin Nano V1.X
Please refer to [MKS Robin Nano github](https://github.com/makerbase-mks/MKS-Robin-Nano-V1.X).

##  More information about the Robin Nano V2.X
Please refer to [MKS Robin Nano V2 github](https://github.com/makerbase-mks/MKS-Robin-Nano-V2).

##  More information about the Robin Nano V3.X
Please refer to [MKS Robin Nano V3 github](https://github.com/makerbase-mks/MKS-Robin-Nano-V3.X).

