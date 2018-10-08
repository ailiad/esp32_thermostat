# esp32_thermostat

WiFi thermostat based on ESP32 (Espressif WROOM-32 Developer Kit), using SHT3X(SHT31-D) temperature/humidity sensor and ILI 9341 TFT LCD Touch display. Data are sent to Thingspeak server and Blynk. Thermostat can be controlled by the Blynk application or directly by the touch on the LCD.  Project is free to use, coded in C++, created in Visual Code with [PlatfomIO IDE](http://docs.platformio.org/en/latest/ide/vscode.html). 

**The project is not yet complete and is still being developed!**

> To build a project, you need to download all the necessary libraries and create the *settings.cpp* file in the src folder:
```c++
// Thermostat project settings
struct Settings
{
    const char *ssid = "WIFI ssid";
    const char *password = "WIFI password";
    const char *blynkAuth = "blynkAuth";
    const char *version = "0.1.0";
};
```

### LCD Touch panel library & wiring:
I'm using awasome [TFT_eSPI](https://github.com/Bodmer/TFT_eSPI) library from Bodmer. You must update *User_Setup.h* file to set display type and pins. There is ESP32 section, my setup for this section is following:

```c++
// ###### EDIT THE PIN NUMBERS IN THE LINES FOLLOWING TO SUIT YOUR ESP32 SETUP   ######

// For ESP32 Dev board (only tested with ILI9341 display)
// The hardware SPI can be mapped to any pins
#define TFT_MISO 19
#define TFT_MOSI 23
#define TFT_SCLK 18
#define TFT_CS    15  // Chip select control pin
#define TFT_DC    2  // Data Command control pin
#define TFT_RST  -1  // Set TFT_RST to -1 if display RESET is connected to ESP32 board RST

#define TOUCH_CS 4 // Chip select pin (T_CS) of touch screen
```

For wires connection between the display and the ESP32 look to the schema..

### Currents list:
* [ESP32](https://www.aliexpress.com/item/ESP-32-ESP-32S-Development-Board-WiFi-Bluetooth-Ultra-Low-Power-Consumption-Dual-Cores-ESP32-Board/32796032726.html) Espressif WROOM-32 Developer Kit
* [HLK-PM01](https://www.aliexpress.com/item/Free-Shippingn-HLK-PM01-AC-DC-220V-to-5V-mini-power-supply-module-intelligent-household-switch/32319515750.html) 220v to 5v power supply
* [Relay module shield](https://www.aliexpress.com/item/Free-Shipping-1PCS-5V-low-level-trigger-One-1-Channel-Relay-Module-interface-Board-Shield-For/32519570562.html)
* [2.8" SPI TFT LCD Touch Panel](https://www.aliexpress.com/item/1pcs-J34-F85-240x320-2-8-SPI-TFT-LCD-Touch-Panel-Serial-Port-Module-with-PCB/32795636902.html)
* [SHT3X (SHT-31D)](https://www.aliexpress.com/item/Free-shipping-SHT31-Temperature-SHT31-D-Humidity-Sensor-module-Breakout-Weather-for-Arduino/32706618932.html) temperature and humidity sensor

### Schema:
![Schema](https://github.com/vitzaoral/esp32_thermostat/blob/master/schema/schema.png)