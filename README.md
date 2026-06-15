# Maincrafts-Task-3
Embedded systems and IoT 
# Smart IoT Automation System (Overview)

## 1. System Pin Architecture
* **Input Transducers:** `tempPin = A0` (Analog Temperature Sensor) [cite: 65, 66]
* **Primary Actuators:** `ledPin = 13` (Active Cooling Fan Indicator) [cite: 65, 66]
* **Secondary Alerts:** `buzzerPin = 12` (Acoustic Fault Alarm) [cite: 65, 66]

---

## 2. Global Configurations
* **Setpoints:** `thresholdTemp = 30.0` (Operational Boundary Limit in °C) [cite: 67]
* **Baud Rate:** `9600` (Hardware UART Serial Link Communication speed) [cite: 71]

---

## 3. Algorithmic Data Pipeline (Loop Execution)
```text
[ Data Input ]  ---> Analog Signal Quantization (Read A0 Channel)
                        │
                        ▼
[ Calibration ] ---> Map Voltage & Linear Scaling to Celsius (°C)
                        │
                        ▼
[ Monitoring ]  ---> Stream Continuous Live Telemetry via UART
                        │
                        ▼
[ Decision ]    ---> Core Conditional Logic Check: Is Temp > 30.0°C?
                        │
                        ├──► (YES) ──► Assert High State on Pins 13 & 12 (Cooling & Alarms ON)
                        │
                        └──► (NO)  ──► Deassert Low State on Pins 13 & 12 (Energy Saving Mode)
                        │
                        ▼
[ Execution ]   ---> Constrain Polling Cycle Interval to 2000 ms Delay
