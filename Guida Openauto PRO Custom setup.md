# myOAPro Toyota Aygo project

I’ve installed and customized my OpenAuto PRO head unit in a 2017 Toyota Aygo (2014 base model).
I’ve been using OpenAuto PRO since 2018!



## Wiring
The head unit is fully removable and upgradable.

The phone can be attached with a magnet in two positions: near the main infotainment display or near the cup holder.
The microphone cable easily passes behind the frame of the main infotainment system.
The back cover includes a covered brightness sensor.
[More PICS in HD here!!!](https://ibb.co/album/XSFRnJ)

## Custom added features
:
- [Automatic DAY/NIGHT script based on the sensor TSL2561](https://github.com/Grawa/brisensor/blob/master/BriSensor.py)
- [Custom Google assistant trigger button](https://github.com/Grawa/OAPro_assistant_button_script)
- [A script that resets the clock at every boot](https://github.com/Grawa/SetRaspyClock0000)(I don't want to use RTC)
- Removed Under-voltage warning (described below with avoid_warnings=2)
## Components
:
- [TECKNET Usb audio adapter UA110](http://www.tecknet.co.uk/ua110.html)
- [TSL2561 Brightness sensor](https://www.amazon.it/caolator-gy-2561-TSL2561-modulo-intensit%C3%A0-luminosa-luminoso/dp/B06Y65FL6H/ref=sr_1_5?__mk_it_IT=%C3%85M%C3%85%C5%BD%C3%95%C3%91&dchild=1&keywords=tsl2561&qid=1612624044&sr=8-5), (I've used a thin, transparent black or blue plastic to cover it. You’ll also need hot glue or similar adhesive to secure it in place.
- Raspberry Pi4
- [Raspberry Pi Official display 7"](https://www.raspberrypi.org/products/raspberry-pi-touch-display/)
- [Case for Raspberry Pi 4 and Official 7" Touchscreen ONENINEDESIGN](https://thepihut.com/products/raspberry-pi-official-7-touchscreen-case)
- [RAVPower charger RP-VC003](https://www.amazon.it/RAVPower-Charge-3-0-54-caricabatteria-Galaxy/dp/B01LCFEQM4/ref=sr_1_1?__mk_it_IT=%C3%85M%C3%85%C5%BD%C3%95%C3%91&dchild=1&keywords=rpvc003&qid=1612618533&sr=8-1)
- [Beikell 1mt Usb-c cable (B078NNH2TJ)](https://www.amazon.it/Cavo-Type-4-Pack-Ricarica-rapido/dp/B07JDP2MNB)
- [Generic External microphone](https://www.chinavasion.com/china/wholesale/electronics/home-audio-video/microphones/usb-microphone-pc-computer-microphone-m-pel-01tg858b)
- Generic 1mt microUSB cable for raspberry pi power
- [Generic clips to anchor cables](https://www.amazon.it/gp/product/B06XWVV83M/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1)
- Generic button (self-made in this setup)
- [Generic Jumper wires](https://www.amazon.it/AZDelivery-Cavetti-Maschio-Femmina-Raspberry/dp/B074P726ZR/ref=sr_1_1_sspa?__mk_it_IT=%C3%85M%C3%85%C5%BD%C3%95%C3%91&dchild=1&keywords=raspberry+pi+cavo&qid=1612619172&sr=8-1-spons&psc=1&smid=A1X7QLRQH87QA3&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUEzMU1WNlpKSEQ4Rzg0JmVuY3J5cHRlZElkPUEwOTU5NTkyMUFENFRMMFM1UDZBSCZlbmNyeXB0ZWRBZElkPUEwNTc5MDU1NzFMTTZUNlJSR0FCJndpZGdldE5hbWU9c3BfYXRmJmFjdGlvbj1jbGlja1JlZGlyZWN0JmRvTm90TG9nQ2xpY2s9dHJ1ZQ==)
- [3M hook loop fastener SJ352Bbk](https://www.amazon.it/gp/product/B07799KYY1/ref=ppx_yo_dt_b_search_asin_image?ie=UTF8&psc=1)
- [Magnet phone holder](https://www.ingrossocinese.com/2021/01/linq-hd-069-supporto-per-smartphone.html)(linq hd069 and maxexcell)
## Guide

1
Connect the TSL2561 brightness sensor to I2C Bus 1:

SDA → GPIO2 (Pin 3)
SCL → GPIO3 (Pin 5)
Connect power (+/-).

In OAPro day/night settings:
Select “Manual” mode.

Set GPIO Pin to 21 (ensure the selected pin is free and not connected to anything else).

Create a physical button (AssistantButton) and connect it between Pin 37 and Pin 39. (optional for AssistantButton)

2
Enable "I2C" from preferences > raspberry pi configuration > interfaces

3
Add this strings to BOOT:/CONFIG.TXT:
```bash
dtoverlay=i2c-gpio
avoid_warnings=2
```

4
Move the required files to the SD card in /home/pi:
- BriSensor.py
- assistant_button.py
- setclock0000.py


5
To enable Autostart add this strings to /etc/xdg/lxsession/LXDE-pi/autostart:
```bash
sudo python3 /home/pi/BriSensor.py
sudo python3 /home/pi/assistant_button.py
sudo python3 /home/pi/setclock0000.py
```


6
Open terminal and execute this command: (optional for AssistantButton)
```bash
sudo pip3 install keyboard
```


## Note
To easily modify files, you should use Nano editor. Use the following command in the terminal. For example: "sudo nano /etc/xdg/lxsession/LXDE-pi/autostart" Then save your changes using Ctrl + X, S, and Enter.

Bluetooth audio: In order to work properly you should disable multimedia and voice audio channel in Settings>Android auto>Audio

