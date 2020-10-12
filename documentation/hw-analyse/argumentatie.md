# Argumentatie Tabel

| **Blok**                                    | **Argumentatie**                                             | **Alternatieven**                            |
| ------------------------------------------- | ------------------------------------------------------------ | -------------------------------------------- |
| Micro Controller ESP32-Cam (van Ai Thinker) | De MCu is verantwoordelijk voor de aansturing van de steppenmotoren zodat de camera de gewenste positie bereikt en vervolgens zal er een foto getrokken worden via de cameramodule en stuurt deze via WiFi naar de backend server API, deze MCu is gebaseerd op ESP32-S Module heeft een 32bit resolutie, TF Card slot, WiFi Module, en de mogelijkheid een Camera aan te sluiten via een FPC-connector | RaspberryPi – andere ESP32 /Arduino variatie |
| OV2640 Camera Module                        | De camera module zal een foto trekken wanner ze een bepaalde positie bereikt, het kan ook een Stream data voorzien aan de microcontroller tot 30fps (SVGA) dus zou een QR-code detectie mogelijk zijn om de gewenste positie te kunnen identificeren. | OV7670 - ArduCam/Pixy2                       |
| DRV8825 step stick                          | Een breakout board voor de DRV8825 stappenmotorcontroller, het heeft een resolutie van 1/32 en beschikt over beschermende functies voor kortsluiting overheating en te veel aan stroom | A4988                                        |
| Power Supply HF100W-SF-12                   | Voor een stabiel functionaliteit het is aangeraden om een constant DC-bron te gebruiken voor de ESP32-Cam hoewel het laagstroomverbruik in standby-stand, het zou een hoge stroompiek beoordelen wanneer het zijn radio/Wifi/Camera gebruikt. Het is ook nodig voor de voeding van de steppenmotoren. | RS-100-12                                    |
| LM7805                        | Het is van belang de 12V Spanning te converteren naar de werkspanning van de MCu | LM317 met extra componenten                  |

# Waarom ESP-Cam?

| Cam - Mcu Alternatieven | ESP-CAM       | Raspberry Pi v2+ Model B+ | Pixy2 + Pi B+    | ESP-EYE       |
| ----------------------- | ------------- | ------------------------- | ---------------- | ------------- |
| Camera sensor           | OV2640        | Sony IMX219               | Aptina MT9M114   | OV2640        |
| Resolutie               | 1632x1220 2Mp | 3280 × 2464  8Mp          | 1296×976  1.26MP | 1632x1220 2Mp |
| MicroSD card            | Ja            | Ja                        | Neen             | Neen          |
| GPIOs                   | 10            | 26                        | 26               | Neen          |
| USB                     | Neen          | Ja                        | Ja               | Ja          |
| Camera prijs            | -             | 28.95                     | 64.99            | -             |
| Mcu prijs               | -             | 29.95                     | 29.95            | -             |
| FTDI Programmer         | Nodig         | -                         | -                | -             |
| Totaal Prijs            | 16.99 €       | 58.9 €                    | 94.94 €          | 29.95 €       |