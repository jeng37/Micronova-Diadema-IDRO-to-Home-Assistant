Diadem IDRO / Total Control app / uncloud to Home Assistant

"uncloud" La Nordica Extraflame Dadema IDRO / NAVEL 2.0 Wifi Modul to Home Assistant.

What has happened so far.

I can still record when something is sent to the stove.
It's just that my programming knowledge is outdated (rusty).
Well, here's what I've found out so far.


Total Control
https://totalcontrol.extraflame.it
or the new one i found in this log,
http://wifi.extraflame.it

I opened the wifi adapter (white label).
And found 3 pins on the ESP32.

<img src="ESP32_Pins.jpg" data-canonical-src="https://github.com/jeng37/Total-Control-app-to-HA/blob/main/ESP32_Pins.jpg"  width="800" height="800" />

GND is drawn, just need to find rx and tx.
So in my case now (Blue = GND, Orange = RX, Yellow = TX)
You need a 3.3v usb2uart.
Note (green is not connected)

<img src="ESP32_Usb2UART.jpg" data-canonical-src="https://github.com/jeng37/Total-Control-app-to-HA/blob/main/ESP32_Usb2UART.jpg" width="800" height="800" />

<img src="ESP32_Pin_Def.jpg" data-canonical-src="https://github.com/jeng37/Total-Control-app-to-HA/blob/main/ESP32_Pin_Def.jpg" width="800" height="800" />

Then connect with putty, serial port of usb2uart, baud rate 115200.

I was very surprised that it is an esp32 wroom and there is a partition with spiffs.

[extraflame.txt](https://github.com/jeng37/Total-Control-app-to-HA/blob/main/extraflame.txt)


Unfortunately I can't make a backup of the esp. I always get the error message
A fatal error occurred: Failed to connect to ESP32: No serial data received.

esptool -p COM7 -b 115200 read_flash 0 0x400000 flash.bin

Instructions [here](https://jmswrnr.com/blog/hacking-a-smart-home-device#dumping-flash)

 
Then based on[
philibertc
Philibert Cheminot ](https://github.com/philibertc/micronova_controller)
i created the controller.
https://github.com/philibertc/micronova_controller/wiki/How-to-build-it

after that,
i got the software from [
Jorre05
Joris S ](https://github.com/Jorre05/micronova)
and installed it on a Wemos d1 mini.
changed some variables and it´s running.

[Diadema_IDRO](https://github.com/jeng37/Total-Control-app-to-HA/blob/main/Diadema_IDRO.txt) read write locations.
   
   
My Stove model is "Extraflame Diadema IDRO"

<img src="Diadema_IDRO.jpg"  Home Assistant data-canonical-src="https://github.com/jeng37/Total-Control-app-to-HA/blob/main/Diadema_IDRO.jpg" width="800" height="800" />

