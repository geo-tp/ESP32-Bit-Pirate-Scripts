# ESP32 Bit Pirate Scripts

![Bit Pirate Scripts](https://github.com/geo-tp/ESP32-Bit-Pirate/raw/pioarduino/images/bus_pirate_scripts.png)

A collection of **easy-to-use** Python scripts to control the [**ESP32 Bit Pirate**](https://github.com/geo-tp/ESP32-Bit-Pirate) via USB serial interface, WiFi or BPIO adapter.

The `bit-pirate` package repo is available here: [Bit-Pirate-Python](https://github.com/geo-tp/Bit-Pirate-Python)

## Install

Install from the repository:

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

Or install the Bit Pirate package directly from PyPI:

```bash
python -m pip install bit-pirate
```

## Usage

Run scripts:

```bash
python wifi_networks_log.py
```


## Scripts

| Script | Description |
|--------|-------------|
| `wifi_scan_log.py` | Periodically scan networks and logs them timestamped to a file |
| `wifi_sniff_log.py` | Periodically sniff WiFi and logs timestamped raw packets to a file |
| `wifi_deauth_all.py` | Sends deauth frames to all discovered SSIDs |
| `bluetooth_sniff_log.py` | Periodically sniff packets and logs them timestamped to a file |
| `uart_read_log.py` | Logs all UART data receiveid into a file |
| `i2c_dump_eeprom_hex.py` | Dump the content of an I2C EEPROM in hex format to a file |
| `i2c_dump_eeprom_bin.py` | Dump the content of an I2C EEPROM in raw bin format to a file |
| `i2c_identify_all.py` | Detects all I2C devices and attempts to identify them |
| `i2c_glitch_all.py` | Detects all I2C devices and attempts to glitch them |
| `spi_dump_flash_hex.py` | Dump the content of an SPI Flash in hex format to a file |
| `spi_dump_flash_bin.py` | Dump the content of an SPI Flash in raw bin format to a file |
| `spi_dump_eeprom_hex.py` | Dump the content of an SPI EEPROM in hex format to a file |
| `spi_dump_eeprom_bin.py` | Dump the content of an SPI EEPROM in raw bin format to a file |
| `led_custom_animation.py` | Custom LED animation using led commands |
| `infrared_devicebgone_loop.py` | Sends 'Device-B-Gone' IR commands in loop |
| `dio_wait_and_pulse.py`  | Wait for a defined pin to go LOW to send a pulse |
| `gps_util.py` | Parse NMEA packets from a UBlox M10 GPS module hooked up to a Bus Pirate |


## Creating a script

```python
from bitpirate import BitPirate

bp = BitPirate.auto_connect()
bp.start()
bp.change_mode("i2c")
bp.send("scan")
bp.wait()
print(bp.receive())
bp.stop()
```