# ⚙️ Embedded X-Ray Control Panel – ESP32-S2 Based Firmware

**Author:** Vedant Mishra  
**Organization:** Lenek Technology Pvt. Ltd.  
**Internship Role:** Embedded Systems Intern  
**Version:** v0.4.6  
**Duration:** May 2025 – July 2025  

---

## 📘 Overview
An embedded firmware designed for an **X-Ray Control Panel** using the **ESP32-S2** microcontroller.  
The system integrates dual DAC control, real-time battery monitoring, and safe shutdown logic, ensuring reliable and accurate analog output management for medical equipment control.

---

## 🔩 Key Features
- Dual **MCP4725 DAC** control via independent I²C buses.  
- **Battery voltage monitoring** and percentage mapping (13V → 0%, 16.8V → 100%).  
- **Low battery protection** with “Low Battery – Shutting Down” alert before system freeze.  
- **Independent voltage control** for two DAC channels using RobTillaart/MCP4725 library.  
- **Real-time system feedback** and sensor data integration.  
- **Safety logic** for controlled startup and shutdown sequence.

---

## 🧠 Technical Implementation
- Two I²C instances for independent DAC communication:  
  ```cpp
  TwoWire I2C1 = TwoWire(0);
  TwoWire I2C2 = TwoWire(1);
  MCP4725 MCP1(0x60, &I2C1);
  MCP4725 MCP2(0x61, &I2C2);
  I2C1.begin(20, 19);
  I2C2.begin(2, 18);
  MCP1.begin();
  MCP2.begin();

  ## 🔹 Libraries Used

| Library | Version | Purpose |
|----------|----------|----------|
| **RobTillaart/MCP4725** | 0.4.0 | Dual DAC analog output |
| **lvgl/lvgl** | 8.3.6 | GUI management (minimal visual logic) |
| **ezButton** | 1.0.4 | Button debouncing and event handling |
| **GFX Library for Arduino** | 1.4.2 | Display driver interface |
| **Adafruit Unified Sensor** | 1.1.14 | Sensor data handling framework |

## 🧩 Hardware Integration

| Component | Interface | Function |
|------------|------------|-----------|
| **ESP32-S2 Saola v1.2** | — | Main microcontroller |
| **MCP4725 (x2)** | I²C | Dual DAC voltage control |
| **Battery Input (13–16.8V)** | ADC | Voltage monitoring |
| **Push Buttons** | GPIO | Input & control events |
| **TFT Display** | SPI | Visual output & status display |

## 🧩 System Logic Flow

### 🔹 System Boot
- Initializes **LVGL** and all **hardware peripherals** (DACs, sensors, buttons).

### 🔹 Normal Operation
- Displays **battery status** on the TFT screen.  
- Dynamically controls **output voltages** using dual DACs.

### 🔹 Low Battery Condition
- If **battery < 13V** → display message:  
  `"Low Battery – Shutting Down"`  
- Freezes display output and triggers **shutdown sequence**.

### 🔹 Safety Handling
- Prevents **DAC voltage overshoot**.  
- Enforces **safe operational limits** for hardware protection.

---

## 📊 Testing & Validation

| Test Case | Method | Observation |
|------------|---------|-------------|
| **Dual DAC Output Verification** | Oscilloscope | Linear and stable voltage response confirmed |
| **I²C Communication** | Logic Analyzer | Independent dual-bus operation validated |
| **Battery Mapping Accuracy** | Bench Power Supply | Accurate percentage conversion (13V–16.8V range) |
| **Full System Test** | ESP32-S2 Saola Board | Reliable performance under real hardware environment |

## 🧰 Tools & Environment

| Tool | Purpose |
|------|----------|
| **PlatformIO (VS Code)** | Development & Build System |
| **Proteus** | Simulation (early logic testing) |
| **ST-LINK / Serial Monitor** | Debugging |
| **GitHub** | Version Control |
| **LVGL + Arduino GFX** | Display Rendering Framework |

## 🧰 Tools & Libraries

| Tool / Library | Version | Purpose |
|----------------|----------|----------|
| **PlatformIO (VS Code)** | — | Development & Build |
| **RobTillaart/MCP4725** | 0.4.0 | DAC control |
| **lvgl/lvgl** | 8.3.6 | UI logic |
| **ezButton** | 1.0.4 | Button handling |
| **GFX Library for Arduino** | 1.4.2 | Display interface |
| **Adafruit Unified Sensor** | 1.1.14 | Sensor framework |

---

## 🧪 Testing & Results

| Test Case | Method | Observation |
|------------|---------|-------------|
| **DAC Output Verification** | Oscilloscope | Verified for accuracy and fast response |
| **Battery Voltage Mapping** | Variable Bench Power Supply | Correct mapping across 13V–16.8V range |
| **Dual I²C Operation** | Logic Analyzer | Independent I²C operation confirmed |
| **System Shutdown Test** | Controlled Low-Voltage Input | System performs safe shutdown below 13V |

---

## 🧾 Outcomes

- ⚙️ Stable **dual-channel analog output** control using ESP32-S2  
- 🔋 Integrated **battery protection** and **voltage mapping logic**  
- 🧠 Enhanced **system safety** via event-driven firmware design  
- 🏭 Reliable **embedded firmware** ready for industrial and medical systems  

---

## 🔗 References

| Resource | Description |
|-----------|-------------|
| [RobTillaart MCP4725 Library](https://github.com/RobTillaart/MCP4725) | DAC control library |
| [ESP32-S2 Saola Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-s2_datasheet_en.pdf) | Hardware reference |
| [PlatformIO Documentation](https://docs.platformio.org/) | Build and configuration guide |
| [Lenek Technology Pvt. Ltd.](https://lenektech.com) | Organization website |

---

## 🧑‍💻 Author

| Name | Education | Role | Contact |
|------|------------|------|----------|
| **Vedant Mishra** | B.Tech in Electronics and Communication Engineering (ECE) | Embedded Systems Intern @ Lenek Technology Pvt. Ltd. | 📧 **vedantmishra.dev@gmail.com** |
| 🌐 **GitHub:** [VedantMishra-dev](https://github.com/VedantMishra-dev) |

---

⭐ *If you like this project, don’t forget to star the repository!* ⭐

