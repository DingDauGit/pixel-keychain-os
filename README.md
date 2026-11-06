[Uploading README_V4_3_2_BLE_REWRITE.txt…]()
PIXEL KEYCHAIN OS V4.3.2 — BLE REWRITE

Package contents:
- index.html: rewritten Web Bluetooth dashboard.
- PixelKeychainOS_V4_3_2_CyberCat_BLERewrite.ino: firmware based on the supplied V4.3.1 source.

Important:
1. The dashboard uses acceptAllDevices with the existing service UUID, so the picker does not depend on the advertised device name filter.
2. The dashboard still checks the exact Pixel OS GATT service and characteristic UUIDs.
3. Firmware retains the supplied display, widgets, pet, games, buttons, clock, LED and idle logic.
4. Firmware BLE command handoff uses a fixed buffer protected by a critical section instead of sharing an Arduino String between the BLE callback and loop.
5. Status notifications are spaced by 25 ms to reduce notification bursts being lost by a phone browser.
6. Existing BLE command protocol is retained:
   G, B:0..3, L:0..4, C:<epoch>:<timezoneOffsetMinutes>, N:<name>, I:0|1, IT:<seconds>.
7. ESP32 Arduino Core 3.2.1 and ESP32C3 Dev Module are intended.

Installation:
A. Save a backup of the currently working firmware and GitHub index.html.
B. Compile the supplied INO in Arduino IDE first. If Verify succeeds, upload it to the ESP32-C3.
C. Replace the repository root index.html with the supplied index.html and commit to main.
D. Wait for GitHub Pages deployment to finish successfully.
E. Open the GitHub Pages URL in Chrome, hard refresh, click Connect Device, select the ESP32 device, then connect.

Debug:
- If the device picker appears but service lookup fails, the ESP32 firmware may not be advertising the expected service UUID.
- If the device does not appear in the picker, verify that the ESP32 is powered and advertising; try scanning with a BLE scanner app.
- Web Bluetooth requires a secure HTTPS origin and a supported browser.
- This source has not been compiled or tested on physical hardware in this session.
