# Sainsmart Coreception 300 (With Bl touch)

## Supported Platforms
This is designed for a Stock 2019-2020 Coreception 300 with the MKS Robin nano V1.2. But this is almost completly stock marlin at its core and is compatible with any board marlin is. so if you change your coreception motherboard just change your compile environment and go. 

## Features
All core features of the Coreception are present and working except the GUI is currently the default text based marlin.

BL Touch is not configured as an endstop it is mainly used for bed mesh creation, this is due to Coreception having 2 seperate Z-Axis leadscrews that are both low pitch and that require seperate leveling (removing prints its normal to unlevel the Zscrews). 

## Configuring BL Touch
To configure your BL Touch will not replace any axis endstops, it will replace the secondary filament runout detection pin,  No endswitch is perfectly accurate which makes BL Touch the perfect addon aswell.

![alt text](https://github.com/jgarder/Marlin-Coreception-300/blob/2.0.x/MKS_Robin_Nano-BLTouch.png?raw=true)

## Disabling BL Touch
if you want an up to date firmware but dont have bl touch, then Comment Line 902 of Configuration.h "#define BLTOUCH" by making it -> "//#define BLTOUCH".  
Then compile and upload to your board. there will be compile errors saying "this option is not available without a bed probe". Ctl-F find in the configuration and configurationadv files the features and disable them. then compile and go. (note: your second filament pin will be avaialble for use again)

## Loose Idea to compile : 
1. download VScode
2. Download the platformIO extension from the extensions tab in vscode
3. download this git (or clone any marlin) and place it on your drive somewhere. 
4. open the folder in vs code  (use "open folder")
5. setup the platformio.ini to have a default environment matching your CPU and its pinouts on your board. wait for intellisense building to finish. for the coreception we use "default_envs = mks_robin_nano35"
6. Hit platformIO:Build in the bottom status bar, or goto platoform io quick access and hit build. (you will need internet to auto download libraries)
7. goto the folder you placed on your drive and goto .pio->build->mks_robin_nano35 where you will see you ROBIN NANO BIN file.
8. take this Binfile and place it on any microsd card... and..... follow the proceeding instructions. 


## QuickStart guide for New Firmware with Coreception (or any marlin printer)
1. Place binfile into SD card
2. Turn off machine Put in SD card, turn on machine
3. If you it ask about Eeprom,  Intialize.
4. If it says "top left" Touch top left, bottom left, top right ,bottom right to calibrate screen, it should then say "calibration complete" and freeze for 10 seconds. 
5. CALIBRATION NEEDED - NEW FIRMWARE
6. GO TO  Main-> configuration->Advanced settings-> tempurature - >
7. PID autotune E1 a(at print temp most often used)+ PIN autotune Bed (at temp most often used) - Run both commands 
8. A  GO TO Main-> configuration->Advanced settings->probe offset->Z Probe Wizard - Run that
8. B Lower Z by 1 mm until  Nozzle to bed is close... 
8. C lower z by .025 or smaller while sliding a piece of paper under a clean nozzle UNTIL slight friction can be felt.
9.  Go TO main->configuration -> Store settings
10. Start a print test calibration cube.
11. Watch while print starts if first layer isn't perfect, click the XYZ position bar (on Color Touchscreens) to enter babystepping mode which will change your initial Probe Z offset (takes 10 presses to change .01 to .02), proceed to Change Z height to fit your material.(If you do change the settings, repeat step 9)



<----------------NORMAL MARLIN BELOW------------------------------------------->

# Marlin 3D Printer Firmware
Additional documentation can be found at the ![GitHub](https://github.com/MarlinFirmware/Marlin).

Additional documentation can be found at the [Marlin Home Page](https://marlinfw.org/).


## License

Marlin is published under the [GPL license](/LICENSE) because we believe in open development. The GPL comes with both rights and obligations. Whether you use Marlin firmware as the driver for your open or closed-source product, you must keep Marlin open, and you must provide your compatible Marlin source code to end users upon request. The most straightforward way to comply with the Marlin license is to make a fork of Marlin on Github, perform your modifications, and direct users to your modified fork.

While we can't prevent the use of this code in products (3D printers, CNC, etc.) that are closed source or crippled by a patent, we would prefer that you choose another firmware or, better yet, make your own.
