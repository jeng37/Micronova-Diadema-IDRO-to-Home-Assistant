Total-Control-app-to-HA

"uncloud" Extraflame NALEL 2.0 Wifi Modul to Home Assistant.

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

C (220) : ********************** INIT **********************
C (223) : *
C (225) : *                  Board T009_3
C (230) : *                  FW rev. 00.33
C (234) : *         compiled at Jul 18 2019 14:16:16
C (240) : *
C (242) : *    ESP32 chip with 2 CPU cores, WiFi/BT/BLE
C (248) : *               silicon revision 1
C (253) : *               4MB external flash
C (258) : *     idf version : v3.2.2
C (262) : *
I (265) [STORE]: try get par_new_ota dst=1073457852, size=4
I (272) [STORE]: nvs_open err=4353
C (265) : *
C (278) : **************************************************


I (296) [STORE]: try get par_new_ota dst=1073457804, size=4
I (296) [STORE]: get int par_new_ota = 3
I (296) system_api: Base MAC address is not set, read default base MAC address from BLK0 of EFUSE
I (306) [STORE]: try get par_security dst=1073527728, size=32
I (312) [STORE]: try get par_customer dst=1073527760, size=32
I (319) [STORE]: try get par_fact_sign dst=1073466988, size=4
I (325) [STORE]: get int par_fact_sign = 7
C (329) [SYS]: monitor_task create
I (333) FS: Initializing SPIFFS
I (355) FS: Partition size: total: 836081, used: 46435
I (355) FS:

list of path /

I (356) FS: >> config.json .... 6234
I (358) FS: >> config0.json .... 236
I (363) FS: >> www/ind.js .... 1962
I (367) FS: >> www/index.html .... 1251
I (371) FS: >> www/logo1.png .... 3693
I (376) FS: >> www/sta.html .... 2208
I (380) FS: >> www/sta.js .... 5040
I (386) FS: >> www/w3.css .... 23308
I (401) FS:
   43932 bytes in 8 file(s)
   
and here is the complete log.

[extraflame.txt](https://github.com/user-attachments/files/16098214/extraflame.txt)


That's the status so far.
I would be happy about help.
