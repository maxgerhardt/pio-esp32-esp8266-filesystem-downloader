# ESP32 & ESP8266 Filesystem Downloader Plugin

# Description

This script provides functions to download the filesystem (SPIFFS or LittleFS) from a running ESP32 / ESP8266  over the serial bootloader using esptool.py, and mklittlefs / mkspiffs for extracting.

# Limitations

* only works with ESP8266 and ESP32 chips. 
* only works over the serial bootloader too, downloading the flash content via a JTAG adapter and OpenOCD is not implemented.
* for the ESP32, only SPIFFS is supported. LittleFS support is not merged in mainline Arduino-ESP32 yet as a built-in library

# Usage

The extractor can be run by either using the VSCode task "Custom" -> "Download Filesystem".

![project task](project_task.png)

Alternatively one can execute

```
pio run -t downloadfs
```
(with optional `-e <environment>`) from the commandline. 

# Configuration
The output will be saved, by default, in the "unpacked_fs" of the project.
This folder can be changed by writing `custom_unpack_dir = some_other_dir` in the corresponding platformio.ini environment. 

# Using in a different project

To add this extractor task functionality to your project, simply copy the `download_fs.py` of this repository to your project and add 

```ini
extra_scripts = download_fs.py
```
to the `platformio.ini`. After a VSCode restart, the new task should appear.

# This Test Firmware

This repository contains a test firwmare for both

# Example execution