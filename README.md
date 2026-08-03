# 🏠 Smart Home Automation System

An IoT-based automated smart home control environment designed and simulated in **Proteus 8 Professional** using **Embedded C/C++** on an ATmega328P (Arduino Uno) micro-controller.

---

## 📌 Project Overview
This system provides real-time environmental monitoring and automated climate/lighting control using active sensor feedback:
* **Temperature & Humidity Control:** Monitors ambient temperature using a **DHT11 sensor**. Automatically activates a 12V DC cooling fan via Relay 2 when room temperature exceeds **30°C**.
* **Automated Ambient Lighting:** Detects ambient light levels using a **Light Dependent Resistor (LDR)**. Automatically triggers 12V illumination lamps via Relay 1 when ambient light falls below a threshold of **500**.
* **Real-time Visual Diagnostic:** Continuously updates system readings (Temperature in °C, Humidity %, and LDR intensity) onto a **16x2 Liquid Crystal Display (LCD)**.

---

## 🛠️ Circuit & Component Breakdown
* **Microcontroller:** Arduino Uno (SIMULINO UNO)
* **Sensors:** 
  * DHT11 Temperature & Humidity Sensor
  * LDR (Light Dependent Resistor) with 10kΩ voltage divider
* **Output Actuators:**
  * 12V DC Cooling Fan (Relay 2 Driven)
  * 12V Illumination Lamp (Relay 1 Driven)
* **Switching & Driver Logic:**
  * BC547 NPN BJT Transistors (Switching drivers for relays)
  * 1N4007 Flyback Diodes (Inductive load/back-EMF protection)
  * 1kΩ Base Resistors
* **Display:** 16x2 Character LCD (HD44780 compliant, operating in 4-bit mode)

---

## ⚡ Control Logic Summary
```cpp
// Ambient Light Logic
if (ldrValue < 500) {
    digitalWrite(RELAY1, HIGH); // Turn ON Lamp
} else {
    digitalWrite(RELAY1, LOW);  // Turn OFF Lamp
}

// Temperature Logic
if (temp > 30) {
    digitalWrite(RELAY2, HIGH); // Turn ON Fan
} else {
    digitalWrite(RELAY2, LOW);  // Turn OFF Fan
}
