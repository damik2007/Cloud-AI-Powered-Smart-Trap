# Project 2: ESP32-CAM Cloud AI Smart Trap with Notifications

## Goal
To overcome the limitations of on-device processing by creating an IoT smart trap system that uses cloud-based Artificial Intelligence for accurate pest detection and sends real-time alerts to the user.

## How it Works
1.  An ESP32-CAM, connected via Wi-Fi, automatically captures an image of a yellow sticky trap every 30 seconds.
2.  The image is Base64 encoded and sent securely (HTTPS) to the Google Gemini Vision API.
3.  A carefully engineered prompt instructs the powerful cloud AI to analyze the image, specifically looking for real insects or clear drawings while ignoring noise like shadows or smudges.
4.  The AI responds with a simple "PEST" or "NO PEST" classification.
5.  The ESP32-CAM displays the current status ("Capturing", "Analyzing", "PEST DETECTED!", "Status: Clear") on an OLED screen.
6.  If a pest is detected, the device sends a push notification with a custom alert message to the user's phone via the ntfy.sh service.

## Technologies Used
* **Hardware:** ESP32-CAM, FTDI Programmer, OLED Display (SSD1306), Jumper Wires
* **Software:** Arduino IDE (C++), Google Gemini API (Cloud Vision AI), ntfy.sh (Push Notifications)
* **Libraries:** `HTTPClient`, `ArduinoJson`, `base64`, `Adafruit_GFX`, `Adafruit_SSD1306`

## Development Process & Challenges Solved
This project involved significant troubleshooting and iterative development:
* **API Integration:** Successfully integrated with the Google Gemini API, resolving initial `404 Not Found` errors by identifying and using the correct API endpoint version (`v1` vs `v1beta`) and model name (`gemini-pro-vision`).
* **Memory Management:** Overcame `HTTP Error: -?` crashes caused by insufficient RAM during HTTPS requests by optimizing the camera image size to `FRAMESIZE_CIF` and efficiently handling JSON payloads using `ArduinoJson`.
* **Connectivity:** Debugged and resolved Wi-Fi connection failures with mobile hotspots by identifying the root cause (WPA3 incompatibility) and configuring the hotspot to use `WPA2-Personal` security. Optimized `setup()` sequence to connect WiFi before initializing peripherals.
* **AI Accuracy:** Refined the prompt sent to the Gemini API multiple times to improve accuracy, specifically instructing it to handle drawings and ignore visual noise, achieving reliable detection in test scenarios.
* **Hardware Debugging:** Diagnosed and resolved power delivery issues during the initial hardware prototyping phase (soldering).

## Outcome
A fully functional, reliable, and portable prototype of an AI-powered smart trap. The system successfully leverages cloud AI to overcome local hardware limitations, providing accurate pest detection and instant notifications. The integration of an OLED display provides clear status updates. This demonstrates a practical application of IoT and Cloud AI for agricultural monitoring.

*
Adding the link to the video here:
https://github.com/user-attachments/assets/aaf4e0af-b0eb-4b7c-90e8-bbf6d13ad637
https://github.com/user-attachments/assets/672b527e-9bae-4bd2-8117-6e30b46fe4d3


Add the screenshot of your ntfy notifications here:
![PHOTO-2025-10-17-11-53-56](https://github.com/user-attachments/assets/3b57449a-8d3a-492d-acc3-270c4f176469)

