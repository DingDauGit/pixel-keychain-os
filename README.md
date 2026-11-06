[README_PixelOS_Dashboard_V2.txt](https://github.com/user-attachments/files/34464270/README_PixelOS_Dashboard_V2.txt)
PIXEL OS DASHBOARD V2 — CYBER CAT

Files:
- PixelOS_Dashboard_V2_CyberCat.html: updated Web Bluetooth dashboard.
- PixelKeychainOS_V4_3_1_CyberCat_DashboardFix.ino: matching firmware source.

Dashboard features:
- Existing BLE connection, clock sync, brightness, and LED controls.
- Rename Cyber Cat (N:<name>).
- Read pet name, mood, sleeping state, and four pet stats.
- Enable/disable OLED idle mode (I:1 / I:0).
- Set inactivity timeout in seconds (IT:<seconds>).

Important firmware correction:
The original firmware tested cmd.startsWith("I:") before testing "IT:".
Because "IT:30" also begins with "I:", the timeout command was consumed by
the enable/disable handler and never reached its own handler. The supplied
firmware fix excludes "IT:" from the "I:" handler.

Compatibility:
- ESP32-C3 SuperMini
- ESP32 Arduino Core 3.2.1
- Existing BLE service/command/status UUIDs are unchanged.
- Open the HTML dashboard in Chrome on Android over HTTPS (for example,
  GitHub Pages). Do not open it as a local file if Web Bluetooth is required.

The source files have not been compiled or hardware-tested in this session.
Upload the matching firmware first, then publish the HTML file to GitHub Pages.
