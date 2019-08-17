works on Raspberry Pi with Openauto Pro
# TSL2561 Smart brightness sensor script

This python script is designed control automatically the original raspberry pi screen brightness and Android Auto with Openauto PRO day/night mode while driving.


# Note: 
The default i2c bus is 3, you should change this value(...)

GPIO 40(Rpi pin 21) needs to be free/NOT connected.
Select in OAPro day/night settings "GPIO Pin": 21

The sensor should be positioned in the left side of Raspberry Pi cover,near usb ports. 
Of course,it's recommended to adjust the lux level values and day/night threshold...


info: VGPLabs@gmail.com
