works on Raspberry Pi with Openauto Pro
# TSL2561 Smart brightness sensor script

This python script is designed to automatically control the original raspberry pi screen brightness and trigger Android Auto day/night mode in Openauto PRO.


# Note: 
The default i2c bus is 1, you can change this value according to your rpi configuration 

GPIO 40(Rpi pin 21) needs to be free/not connected.
IMPORTANT: Select in OAPro day/night settings "GPIO Pin": 21

The sensor should be positioned in the left side of Raspberry Pi cover,near usb ports. 
Of course,it's recommended to adjust the target screen brightness values and day/night threshold...


info: VGPLabs@gmail.com

ref. Full Guide OAPro https://bluewavestudio.io/community/showthread.php?tid=2398
