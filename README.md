Total-Control-app-to-HA

"uncloud" Extraflame NAVEL 2.0 Wifi Modul to Home Assistant.

What has happened so far.

I can still record when something is sent to the public.
It's just that my programming knowledge is outdated (rusty).
Well, here's what I've found out so far.

I opened the wifi adapter (white label).
And found 3 pins on the ESP32.

![ESP32_Pins](https://github.com/jeng37/Total-Control-app-to-HA/assets/12857791/8f61cc9c-6878-4c8d-9441-ce4cbc64a04e)

GND is drawn, just need to find rx and tx.
So in my case now (Blue = GND, Orange = RX, Yellow = TX)
You need a 3.3v usb2uart.
Note (green is not connected)

![ESP32_Usb2UART](https://github.com/jeng37/Total-Control-app-to-HA/assets/12857791/95634655-ef08-4f44-b724-3371b0c79307)

![usb2uart_Pin_Def](https://github.com/jeng37/Total-Control-app-to-HA/assets/12857791/fa2f1ced-ec19-4db5-8c58-adb0dc21e0f7)

Then connect with putty, serial port of usb2uart, baud rate 115200.

I was very surprised that it is an esp32 wroom and there is a partition with spiffs.

[extraflame.txt](https://github.com/user-attachments/files/16098214/extraflame.txt)


That's the status so far.
I would be happy about help.
