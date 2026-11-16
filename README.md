# ⚡ ESP32 Smart Power Source Switch (Grid ↔ Solar PV)

IoT-enabled switching board that automatically transfers a load between the **utility grid** and a **photovoltaic (solar) system**, depending on source availability and conditions.

![Board photo](docs/board.jpg)

## 🎯 Problem
Power outages and the rising cost of electricity create a need for systems that use solar energy when it is available and fall back to the grid when it is not, without manual intervention and with remote monitoring.

## 💡 Solution
A custom board based on the **ESP32** that:
- Monitors the voltage of both sources (grid and PV) through analog conditioning circuits.
- Decides which source should feed the load and switches it automatically using [relays / contactors / MOSFETs].
- Sends source status and measurements to an IoT platform for remote monitoring [and manual control].

## 🧩 System Architecture
![Block diagram](docs/block-diagram.png)

`Grid / PV source → Voltage sensing & signal conditioning → ESP32 (ADC + control logic) → Switching stage → Load`
`ESP32 → Wi-Fi → [IoT platform: Blynk / ThingSpeak / MQTT / web dashboard]`

## 🔧 Hardware
| Component | Function |
|---|---|
| ESP32 [model] | Control logic, ADC readings, Wi-Fi connectivity |
| Voltage sensing circuit [divider / ZMPT101B / op-amp] | Analog conditioning of source voltages |
| [Relay module / contactor] | Source switching |
| [Power supply / regulator] | Board power |
| [Other components] | ... |

Schematic and PCB files designed in **Proteus** are in [`/hardware`](hardware/).

## 💻 Firmware
- Written in C/C++ with **Arduino IDE** for the ESP32.
- Source code: [`/firmware`](firmware/)

**Switching logic (summary):**
1. Read the voltage of each source through the ADC.
2. If the PV voltage is within range → feed the load from solar.
3. If PV is insufficient → transfer to the grid.
4. Publish the status to the IoT dashboard.

## 📊 Results
- Switching time: [X ms]
- Voltage measurement accuracy: [±X %]
- Tested with a load of [X W]
- [Other measured results]

## 🎥 Demo
[Link to demonstration video]

## 🛠️ Tools
ESP32 · Arduino IDE · Proteus · C/C++ · Analog Electronics · IoT

## 👤 Author
**Juan Diego Medina Arévalo** — Electronic & Telecommunications Engineering, IU CEDOC
[LinkedIn](link-to-your-profile)
