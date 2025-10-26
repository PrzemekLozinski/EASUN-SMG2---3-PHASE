# 🌞 Easun SMG2 - 3 Phase Integration for Home Assistant

**Author:** Przemek Lozinski  
**Platform:** ESPHome + Home Assistant  
**Hardware:** 3x Easun SMG2 6.2kW inverters in 3-phase mode (L1, L2, L3)  
**Communication:** RS485 → ESP32 (WiFi Modbus Bridge)

---

## 🔧 Project Overview

This project integrates three Easun SMG2 inverters using RS485 communication with an ESP32,  
acting as a WiFi → Modbus bridge for Home Assistant.

Each inverter operates on a separate Modbus address (1, 2, 3)  
and uses its own RS485 converter connected to a dedicated UART interface on the ESP32.

---

## ⚙️ ESP32 Pin Configuration

| Inverter | TX Pin | RX Pin | DE/RE Pin | Modbus ID |
|-----------|--------|--------|------------|------------|
| P1 (South) | GPIO17 | GPIO16 | GPIO21 | modbus1 |
| P2 (East)  | GPIO4  | GPIO5  | GPIO22 | modbus2 |
| P3 (West)  | GPIO25 | GPIO26 | GPIO23 | modbus3 |

> All grounds (GND) must be common between ESP32 and all RS485 modules.

---

## 🧠 Home Assistant Dashboard

The included `dashboard.yaml` provides a full Lovelace layout with:
- 3 inverters (P1 / P2 / P3)
- Battery, Load, and PV gauges
- Mode and priority selectors
- Total PV & Load indicators

---

## ⚡ Template Sensors

Defined in `home_assistant/sensors_template.yaml`:
- `sensor.total_load_power` → total load from all inverters  
- `sensor.total_pv_power` → total PV power (voltage × current)

---

## 🚀 How to Use

1. Copy `esphome/easun-smg2.yaml` to your ESPHome folder  
2. Flash it to an ESP32 board  
3. Copy the `home_assistant/` folder into your HA `/config` directory  
4. Restart Home Assistant  
5. Import `dashboard.yaml` into Lovelace  

---

**License:** MIT  
**Version:** 1.0  
*Project by Przemek Lozinski & ChatGPT, 2025*
