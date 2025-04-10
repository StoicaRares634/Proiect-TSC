# Proiect-TSC
Proiect-TSC Stoica Rares-Nicolae 333CA


| Device                                                                       | CHECK_PRICES                                                                                                                                                     |
|------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ESP32_WROVER_EAGLE-LTSPICE_CC0402                                            |                                                                                                                                                                  |
| RCL_CPOL-EUCT3528                                                            | https://a360.co/4iZy6AA                                                                                                                                           |
| CPH3225A                                                                     | https://www.snapeda.com/parts/CPH3225A/Seiko+Instruments/view-part/?ref=eda                                                                                       |
| BUTTON_CUSYOMV1                                                              | https://industry.panasonic.com/global/en/products/control/switch/light-touch/number/evqpuj02k                                                                     |
| ADAFRUIT_LEDCHIP-LED0603                                                     | https://www.snapeda.com/parts/KP-1608SURCK/Kingbright/view-part/?ref=search                                                                                       |
| USBLC6-2SC6Y                                                                 | https://www.snapeda.com/parts/USBLC6-2SC6Y/STMicroelectronics/view-part/?ref=eda                                                                                  |
| ESP32_WROVER_AVX---SD0805S020S1R0                                            | https://eu.mouser.com/ProductDetail/KYOCERA-AVX/SD0805S020S1R0?qs=jCA%252BPfw4LHbpkAoSnwrdjw%3D%3D                                                                |
| MBR0530                                                                      | https://www.snapeda.com/parts/MBR0530/Onsemi/view-part/?ref=eda                                                                                                   |
| PGB1010603MR                                                                 | https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda                                                                                          |
| BD5229G-TR                                                                   | https://componentsearchengine.com/part-view/BD5229G-TR/ROHM%20Semiconductor                                                                                       |
| XC6220A331MR-G                                                               | https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex                                                                                                  |
| FH34SRJ-24S-0.5SH_99_                                                        | https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex                                                                                                  |
| SAMACSYS_PARTS_USB4110-GF-A                                                  | https://componentsearchengine.com/part-view/USB4110-GF-A/GCT%20(GLOBAL%20CONNECTOR%20TECHNOLOGY)                                                                  |
| 112A-TAAR-R03_ATTEND                                                         | https://store.comet.srl.ro/Catalogue/Product/43497/                                                                                                               |
| 744043680IND_4828-WE-TPC_WRE                                                 | https://eu.mouser.com/ProductDetail/Wurth-Elektronik/744043680?qs=PGXP4M47uW6VkZq%252BkzjrHA%3D%3D                                                                |
| ESP32C6_VARISTORCN1812                                                       | https://www.mouser.co.uk/ProductDetail/EPCOS-TDK/B72520T0350K062?qs=dEfas%2FXlABIszF52uu7vrg%3D%3D                                                                |
| ESP32_WROVER_SPARKFUN-DISCRETESEMI_MOSFET_PCH-DMG2305UX-7                    | https://componentsearchengine.com/part-view/DMG2305UX-7/Diodes%20Incorporated                                                                                     |
| D8                                                                           | https://componentsearchengine.com/part-view/SI1308EDL-T1-GE3/Vishay                                                                                               |
| ESP32_WROVER_EAGLE-LTSPICE_RR0402                                            | https://componentsearchengine.com/part-view/R0402%201%25%20100%20K%20(RC0402FR-07100KL)/YAGEO                                                                     |
| BME680                                                                       | https://www.snapeda.com/parts/BME680/Bosch/view-part/?welcome=home                                                                                                |
| SJ                                                                           | https://grabcad.com/library/solder-jumpers-1                                                                                                                     |
| W25Q512JVEIQ                                                                 | https://www.snapeda.com/parts/W25Q512JVEIQ/Winbond+Electronics/view-part/?ref=eda                                                                                 |
| ESP32-C6-WROOM-1-N8                                                          | https://www.snapeda.com/parts/ESP32-C6-WROOM-1-N8/Espressif+Systems/view-part/?ref=eda                                                                            |
| DS3231SN#                                                                    | https://www.snapeda.com/parts/DS3231SN%23/Analog+Devices/view-part/?ref=eda                                                                                       |
| MAX17048G+T10                                                                | https://www.snapeda.com/parts/MAX17048G+T10/Analog+Devices/view-part/?ref=eda                                                                                     |


![diagrama](TSC.drawio.png)



## Descriere detaliata a functionalitatii hardware

Proiectul utilizeaza microcontroller-ul ESP32-C6 WROOM. Acesta gestioneaza comunicatia cu diverse module prin interfete SPI, I2C si GPIO, avand capacitate extinsa pentru conectivitate wireless si control de periferice.

### Structura de alimentare

- Conector USB-C: asigura alimentarea externa si transferul de date.
- Controler incarcare baterie Li-Po (MCP73831): integreaza functii de incarcare sigura si controlata a bateriei.
- Baterie Li-Po: sursa de energie mobila, folosita pentru autonomie.
- LDO Regulator (XC6206): reduce tensiunea de la baterie la 3.3V stabili, necesari ESP32 si altor componente.

### Module conectate la ESP32-C6 si interfetele lor

#### 1. Senzor ambiental BME688
- Interfata: I2C
- Functii: detecteaza temperatura, presiune, umiditate si compusi volatili (calitate aer).
- Pini ESP32-C6:
  - GPIO4 → SDA
  - GPIO5 → SCL
GPIO4 si GPIO5 sunt GPIO standard cu suport I2C hardware.

#### 2. Modul RTC – DS3231SN
- Interfata: I2C
- Functii: mentine timpul real precis, inclusiv in standby.
- Pini ESP32-C6:
  - Impartiti cu BME688: GPIO4 (SDA) si GPIO5 (SCL)

#### 3. Memorie externa NOR Flash – W25Q512JVEIQ
- Interfata: SPI
- Functii: stocare extensiva de date nevolatile (64MB).
- Pini ESP32-C6:
  - GPIO6 → CLK
  - GPIO7 → MISO
  - GPIO8 → MOSI
  - GPIO9 → CS (Flash)
Aceasta configuratie este conforma cu pinii dedicati SPI al ESP32-C6 pentru performanta maxima.

#### 4. Modul SD Card
- Interfata: SPI (partajata cu NOR Flash)
- Pini ESP32-C6:
  - GPIO10 → CS (SD Card)
Se foloseste acelasi bus SPI ca Flash-ul, dar cu CS separat pentru selectare.

#### 5. E-Paper Display
- Subcomponente:
  - Circuit de tip e-paper + selector de tip ecran
  - Header pentru display
- Interfata: SPI
- Pini ESP32-C6:
  - GPIO11 → CS (E-Paper)
  - GPIO12 → RES (Reset)
  - GPIO13 → BUSY (Stare de incarcare)
GPIO11–13 sunt configurabili si sunt utilizati pentru semnale de control specifice E-Paper.

#### 6. Butoane de control (BOOT, RESET, CHANGE)
- Interfata: GPIO
- Pini ESP32-C6:
  - GPIO0 → BOOT
  - GPIO1 → RESET
  - GPIO2 → CHANGE
- Utilitate: ofera control manual pentru operatii precum boot, test sau configurare.
