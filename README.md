<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/7499fc6d-a8ff-4278-95a3-e87a92838bb4" /># H2oTronics
"Arduino Uno R4 project enabling remote control via smartphone. Features Bluetooth/Wi-Fi connectivity, easy setup, and customizable commands for IoT applications, robotics, and smart devices."

Absolutely! I can create a **complete, copy-paste-ready README.md** that starts with **hardware wiring & component connections** and then continues to **hosting steps using GitHub Developer Pack**. Here’s a polished version:

---

# 🚰 Smart Water Pump Automation System

### **Arduino UNO R4 WiFi + MQTT + Node-RED (GitHub Developer Pack Hosted)**

This project is a fully automated **IoT water pump system** using Arduino UNO R4 WiFi, MQTT, and Node-RED, now **hosted online 24/7** using GitHub Student Developer Pack cloud credits.

---

## 🌟 Key Features

* 🌐 **WiFi-enabled Arduino UNO R4**
* 📡 **MQTT Publish/Subscribe** communication
* 💧 **Water level monitoring via ultrasonic sensor**
* 🛑 **Dry-run pump protection**
* 🔌 **Automatic shutdown on WiFi/MQTT disconnect**
* 🖥️ **Node-RED dashboard hosted on cloud VPS**
* 📱 Remote access via web/mobile

---

## 🧩 Hardware Components & Wiring

| Component                  | Arduino Pin / Connection                          | Purpose                   |
| -------------------------- | ------------------------------------------------- | ------------------------- |
| Arduino UNO R4 WiFi        | USB or external power                             | Main controller           |
| HC-SR04 Ultrasonic Sensor  | TRIG → D10, ECHO → D9                             | Measures water level      |
| 1-Channel Relay Module     | IN → D7, VCC → 5V, GND → GND                      | Switches mini pump ON/OFF |
| Mini Water Pump            | Connected via relay COM/NO, powered by 9V battery | Water pumping             |
| 9V Battery                 | Connected to pump only                            | External power source     |
| I2C LCD Display (optional) | SDA → A4, SCL → A5, VCC → 5V, GND → GND           | Local water-level display |
| Breadboard & Jump Wires    | N/A                                               | Circuit assembly          |

**Wiring Notes:**

* Ensure the relay **GND is common** with Arduino GND.
* The **pump is powered separately**; relay acts as a switch.
* LCD display is optional; system works without it.
* Ultrasonic sensor should be **facing the water surface** without obstruction.

---

## 🔧 Software & System Logic

### Arduino UNO R4 Logic

1. Connect to WiFi.
2. Publish water level, pump status, and system status via MQTT.
3. Receive **ON/OFF commands** from Node-RED dashboard.
4. Pump operates **only if sensor confirms safe water level**.
5. Auto-shutdown if WiFi or MQTT disconnects.

### System Bug Fixes Implemented

| Issue                                      | Solution                                                       |
| ------------------------------------------ | -------------------------------------------------------------- |
| Sensor readings jump due to water splashes | Average **5 consecutive readings** before sending updates      |
| Pump may run with empty tank               | Pump **requires safe water level**; app cannot override sensor |
| Pump may continue during network drop      | Automatic **shutdown on WiFi/MQTT disconnect**                 |

---

## 🔧 Node-RED Dashboard (Hosted via VPS)

* Real-time tank level gauge
* Pump ON/OFF button
* Master switch status
* MQTT logs & system health

**Topics:**

```
watersystem/r4/control  → Cloud → Arduino (ON/OFF)
watersystem/r4/level    → Arduino → Cloud (%)
watersystem/r4/pump     → Arduino → Cloud (ON/OFF)
watersystem/r4/master   → Arduino → Cloud (System health)
```

---



## 🌐 Hosting Roadmap Using GitHub Developer Pack

### Step 1: Claim Cloud Credits

1. Navigate to [GitHub Student Developer Pack](https://education.github.com/pack)
2. Select a cloud provider:

   * **DigitalOcean**: $200 credit → VPS/Droplet
   * **Microsoft Azure**: $100 credit → VM hosting
3. Follow instructions to apply credits and create an account.

### Step 2: Set Up VPS (DigitalOcean Example)

1. Log in → **Create Droplet**
2. Choose:

   * OS: Ubuntu LTS 22.04
   * Plan: ≥2GB RAM recommended
   * Auth: SSH Key
3. Name Droplet (e.g., `nodered-iot-host`) → Create

### Step 3: Install Node-RED & Dependencies

```bash
ssh your_user@your_droplet_ip_address
bash <(curl -sL https://raw.githubusercontent.com/node-red/linux-installers/master/deb/update-nodejs-and-nodered)
sudo systemctl enable nodered
sudo systemctl start nodered
```

* Node-RED runs on port **1880**
* Access editor: `http://your_droplet_ip_address:1880`

### Step 4: Configure Node-RED Flow

* Add **MQTT Input Node**
* Configure broker:

  * Host: HiveMQ Cloud (or your own broker)
  * Port: 1883 / 8883
* Set topics to match Arduino publishing topics
* Build flows for **dashboard controls** and **status display**

### Step 5: GitHub Integration

* Enable **Node-RED Projects**
* Connect to **private GitHub repo**
* Commit & push flows for version control

---

## 🔋 Power Setup

* Arduino: USB or 5V adapter
* Pump: 9V battery (via relay)
* Relay **isolates Arduino from high load**

---
---

## 🧪 Testing Checklist

* WiFi connection verified
* MQTT broker connects via HiveMQ Cloud
* Node-RED dashboard loads on VPS
* Pump auto-shutdown works
* Dashboard reflects real-time status

---

## 🚀 Future Improvements

* Push notifications
* Mobile app integration (Blynk / Arduino IoT Cloud)
* Multi-tank support
* Waterproof ultrasonic sensor housing

---

## 📜 License

MIT License

---

👤 Author

ht0Tronics
Smart Water Pump Automation System — **GitHub Hosted**
2025

---

