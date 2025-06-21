

 ESP32 Gas Monitoring System using Python & XAMPP

🔍 Overview

This project implements a real-time **IoT-based Gas Monitoring system** using the **ESP32 microcontroller** and a **soil moisture sensor**. The ESP32 reads analog moisture levels from the sensor and sends the data over Wi-Fi to a **Python script** running on a local server. The script stores this data in a **MySQL database** managed via **XAMPP**.


🛠️ Features

* 📶 Wi-Fi enabled data transmission using ESP32
* 🐍 Python server to receive and log data
* 💾 Data stored in MySQL database via XAMPP
* 📈 Extendable for dashboards, alerts, or IoT platforms



⚙️ Hardware Components

* 🧠 **ESP32 Wi-Fi Module**
*  Gas Sensor **
* 🧪 Jumper wires & Breadboard
* 🔋 USB Cable for ESP32 power


 💻 Software Stack

| Tool        | Purpose                             |
| ----------- | ----------------------------------- |
| Arduino IDE | Programming ESP32                   |
| Python 3.x  | Local server for data receiving     |
| XAMPP       | MySQL & Apache for local backend    |
| HeidiSQL    | GUI to view and manage MySQL tables |



 🔧 How It Works

1. **ESP32 + Gas Sensor:**

   * ESP32 reads analog voltage from the soil sensor.
   * Moisture data is sent via HTTP POST to a Python Flask server.

2. **Python Server:**

   * A lightweight Python server listens for incoming POST requests.
   * Moisture values are inserted into the MySQL database.

3. **Data Storage:**

   * MySQL is hosted via XAMPP.
   * HeidiSQL/phpMyAdmin is used to monitor or export moisture logs.



🚀 Getting Started

 1. 🛠 Hardware Setup

```
Gas Moisture Sensor Pin  -> ESP32 Pin
-------------------------    ----------
VCC                        -> 3.3V
GND                        -> GND
Analog Output (A0)         -> GPIO 34 (or any ADC pin)
```

> 💡 Use an analog sensor that outputs varying voltage based on moisture content.



 2. 💡 Arduino IDE Setup

* Install **ESP32 Board Manager**
* Set Wi-Fi SSID and password inside the sketch
* Code will read moisture level (0–4095) and send via HTTP POST



3. 🐍 Python Server Setup

 Install required libraries:


pip install flask mysql-connector-python


* Run `server.py` from `/Server_Code/`:

```bash
python server.py
```

* Flask will listen for incoming moisture data from ESP32.


 4. 🗃️ MySQL Database Setup (via XAMPP)

* Start Apache and MySQL services in XAMPP Control Panel
* Open phpMyAdmin or HeidiSQL
* Create database `gas_monitoring`
* Create table `soil_data`:

```sql
CREATE TABLE soil_data (
    id INT AUTO_INCREMENT PRIMARY KEY,
    moisture INT NOT NULL,
    timestamp DATETIME DEFAULT CURRENT_TIMESTAMP
);
```

---

## 📊 Sample Output

| ID | Moisture | Timestamp           |
| -- | -------- | ------------------- |
| 1  | 1800     | 2025-06-20 10:01:45 |
| 2  | 2200     | 2025-06-20 10:05:31 |
| 3  | 2400     | 2025-06-20 10:10:22 |








