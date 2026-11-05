[README.md](https://github.com/user-attachments/files/34432540/README.md)
# Pixel Keychain OS V3.0 — BLE Edition

## Hardware
- ESP32-C3 SuperMini
- OLED SSD1306 I2C 128x64: VDD->3V3, GND->GND, SCK/SCL->GPIO9, SDA->GPIO8
- Button A: GPIO4 to GND
- Button B: GPIO5 to GND
- White LED: GPIO6 -> 330 ohm resistor -> LED anode; LED cathode -> GND

## Arduino IDE
- Board: ESP32C3 Dev Module
- ESP32 Arduino Core: 3.2.1
- USB CDC On Boot: Enabled
- Install Adafruit GFX Library and Adafruit SSD1306.
- BLE uses the ESP32 Arduino core's built-in BLE library. No separate BLE library is required.

## Upload firmware
Open PixelKeychainOS_V3.ino, select the correct port, and upload.
Open Serial Monitor at 115200 baud. Look for:
[BLE] Advertising: PIXEL-OS-BLE
[OS] Ready

## Publish dashboard with GitHub Pages
1. Create a GitHub repository, e.g. pixel-keychain-dashboard.
2. Upload index.html to the repository root.
3. Open Settings -> Pages.
4. Choose Deploy from a branch, branch main, folder /(root), then Save.
5. Wait for the HTTPS Pages URL.
6. Open it in Chrome on Android (TECNO POVA 5), enable Bluetooth, and tap CONNECT DEVICE.
7. Select PIXEL-OS-BLE.

Web Bluetooth requires a supported browser and a secure context (HTTPS). GitHub Pages provides HTTPS. Chrome may ask for Bluetooth / nearby devices permission.

## BLE protocol
Service: 12345678-1234-1234-1234-123456789000
Command characteristic (Write): 12345678-1234-1234-1234-123456789001
Status characteristic (Read + Notify): 12345678-1234-1234-1234-123456789002

Commands:
- G = request status
- B:0..3 = OLED brightness (100%, 70%, 40%, 15%)
- L:0..4 = LED mode (OFF, BREATHING, STATUS, NOTIFICATION, FLASHLIGHT)
- C:<epoch>:<timezoneOffsetMinutes> = set clock from phone

Status notifications are short packets:
- B:<brightnessIndex>,L:<ledModeIndex>
- U:<uptimeSeconds>
- T:<HH:MM>
- D:<YYYY-MM-DD>

## Notes
- BLE is the only radio transport used by this firmware; Wi-Fi AP code is removed.
- GitHub Pages only hosts the dashboard. Commands travel directly from the phone to ESP32 over BLE.
- Clock runs while powered. Without an RTC, the device cannot account for time while fully powered off; sync again from the phone after reboot.
- Music, Tools, and Games remain placeholders in this release.
