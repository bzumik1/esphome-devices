---
title: KinCony KC868-A6
date-published: 2023-04-20
type: relay
standard: global
board: esp32
---

![Product](KC868-A6.jpg "Product Image")

## GPIO Pinout

| Pin    | Function            |
| ------ | ------------------- |
| GPIO36 | ANALOG_A1           |
| GPIO39 | ANALOG_A2           |
| GPIO34 | ANALOG_A3           |
| GPIO35 | ANALOG_A4           |
| GPIO4  | IIC_SDA             |
| GPIO15 | IIC_SCL             |
| GPIO32 | 1-Wire GPIO         |
| GPIO33 | 1-Wire GPIO         |
| GPIO26 | analog  output1     |
| GPIO25 | analog  output2     |
| GPIO14 | RS485_RXD           |
| GPIO27 | RS485_TXD           |
| GPIO17 | RS232_RXD           |
| GPIO16 | RS232_TXD           |
| GPIO5  | CS   (SPI_Bus)      |
| GPIO23 | MOSI (SPI_Bus)      |
| GPIO19 | MISO (SPI_Bus)      |
| GPIO18 | CSK  (SPI_Bus)      |

[Additional pinout/design details](https://www.kincony.com/esp32-6-channel-relay-module-kc868-a6.html)

## Basic Configuration

```yaml
# Basic Config
esphome:
  name: kc868-a4
  platform: ESP32
  board: esp32dev

# Enable logging
logger:

# Enable Home Assistant API
api:

ota:
  password: "4d5a388de4f759bf88e71cde7a31af6f"

wifi:
  ssid: "KinCony"
  password: "a12345678"

  # Enable fallback hotspot (captive portal) in case wifi connection fails
  ap:
    ssid: "Kc868-A4 Fallback Hotspot"
    password: "QOU4hbAjJ5Wb"

captive_portal:

# Relays are connected trough I2C
i2c:
  sda: 4
  scl: 15
  scan: True

pcf8574:
  - id: 'pcf8574_hub'
    address: 0x24
    pcf8575: False

switch:
  - platform: gpio
    name: "Relay 1"
    pin:
      pcf8574: pcf8574_hub
      number: 0
      mode:
        output: true
      inverted: false

  - platform: gpio
    name: "Relay 2"
    pin:
      pcf8574: pcf8574_hub
      number: 1
      mode:
        output: true
      inverted: false

  - platform: gpio
    name: "Relay 3"
    pin:
      pcf8574: pcf8574_hub
      number: 2
      mode:
        output: true
      inverted: false

  - platform: gpio
    name: "Relay 4"
    pin:
      pcf8574: pcf8574_hub
      number: 3
      mode:
        output: true
      inverted: false

  - platform: gpio
    name: "Relay 5"
    pin:
      pcf8574: pcf8574_hub
      number: 4
      mode:
        output: true
      inverted: false

  - platform: gpio
    name: "Relay 6"
    pin:
      pcf8574: pcf8574_hub
      number: 5
      mode:
        output: true
      inverted: false

binary_sensor:
  - platform: gpio
    name: "input1"
    pin:
      number: 36
      inverted: true

  - platform: gpio
    name: "input2"
    pin:
      number: 39
      inverted: true

  - platform: gpio
    name: "input3"
    pin:
      number: 27
      inverted: true

  - platform: gpio
    name: "input4"
    pin:
      number: 14
      inverted: true
```
