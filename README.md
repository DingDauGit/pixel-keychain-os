[README_V4_3_3_Brightness10.txt](https://github.com/user-attachments/files/34466898/README_V4_3_3_Brightness10.txt)
PIXEL KEYCHAIN OS V4.3.3 — 10% BRIGHTNESS CONTROL

Files:
- index_brightness10.html: updated Web Bluetooth dashboard.
- PixelKeychainOS_V4_3_3_Brightness10.ino: matching ESP32-C3 firmware.

Brightness:
- Dashboard slider ranges from 10% to 100%, in 10% increments.
- New BLE command: V:<percent>, e.g. V:70.
- Firmware maps 10..100% to SSD1306 contrast 26..255.
- Status notification remains B:<percent>,L:<ledMode>.
- Existing saved legacy brightness presets are migrated if no new percentage is stored.

Other BLE commands and UUIDs remain unchanged.
Use ESP32 Arduino Core 3.2.1 and ESP32C3 Dev Module.
Compile/Verify before uploading. This source has not been hardware-tested here.
