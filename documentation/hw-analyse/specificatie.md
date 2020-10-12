# Specificatie Tabel
| **Blok**                   | **Specificatie**     | **Min.**                                            | **Nominaal**             | **Max.**   |
| -------------------------- | -------------------- | --------------------------------------------------- | ------------------------ | ---------- |
| ESP32-CAM MCu              | Werkspanning         |                                                     | 3.3V                     | 5V         |
|                            | Stroom               | 6mA@5V (deep sleep)                                 |                          | 310ma @ 5V |
|                            | Freq. Cpu            |                                                     | 160MHz                   |            |
|                            | Flash                | 32Mbit                                              |                          |            |
|                            | RAM                  | 520KB SRAM + 4M PSRAM                               |                          |            |
|                            | Protocol             | WiFi 802.11b/g/n, BLE, SPI, I2C,  PWM, UART, TFCard |                          |            |
|                            | Image output format  | JPEG, BMP, Grayscale                                |                          |            |
| OV2640 2.0MP               | Output Format        | 10bit Raw RGB, 8bit compressed  data                |                          |            |
|                            | Max. image transfer  | UXGA/SXGA 15fps                                     | SVGA 30fps               | CIF 60fps  |
|                            | vermogen             | Standby 600uA                                       | Active 140mW UXGA @15fps |            |
| DRV8825 Stepstick          | Werkspanning (vmout) | 12V                                                 |                          | 24V        |
|                            | Werkspanning(logic)  | 3V                                                  | 5V                       | 5.25V      |
|                            | Stroom (Aout)        |                                                     |                          | 2.5A @ 24V |
|                            | Stroom(operating)    |                                                     | 5mA                      | 8mA        |
| Nema17motor (42BYGHM809)   | Hoek                 | 0.9°/step                                           |                          |            |
|                            | Stroom               |                                                     | 1.68A                    |            |
|                            | Werkspanning         |                                                     | 2.77V                    |            |
| Power Supply  HF100W-SF-12 | AC Input Spanning    | 170V                                                | 230V                     | 264V       |
|                            | AC input stroom      |                                                     |                          | 1.5A       |
|                            | Strom                |                                                     |                          | 8.5A@12V   |
| DC-DC Buck converter       | Werkspanning         | 3.2V                                                |                          | 40V        |
|                            | Stroom               |                                                     |                          | 2A @ 35V   |