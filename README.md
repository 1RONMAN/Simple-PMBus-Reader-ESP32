# Simple PMBus Power Supply Monitor & Controller

**v1** is based on the [sxjack/dps750tb_psu_i2c](https://github.com) project.  
**v2** is based on the `CSPS_TO_USB_AND_WIFI` project.

This is a lightweight PMBus utility designed for ESP32 to monitor server Power Supply Units (PSUs) via the I2C interface. It reads real-time telemetry data (voltage, current, power, temperature, and fan speed) and outputs it via the serial console. It also supports remote power control via the PSON pin and custom fan speed duty cycle adjustments (v2).

---

## Features
- **Real-Time Telemetry:** Continuous monitoring of input/output voltage (V), current (A), and power (W).
- **Environmental Monitoring:** Real-time readings from internal temperature sensors and fan speeds (RPM).
- **Diagnostic Logging:** Direct fetching of the PMBus standard status word (`STATUS_WORD`) for error tracking.
- **Serial Interface:** Operates at a baud rate of `115200` for seamless debugging, logging, or integration with a GUI/host application.
- **PSU & Fan Control:** Full power cycle management via the `PSON#` pin and dynamic fan speed adjustment (v2).

---

## Hardware Compatibility / Tested Hardware
This firmware has been actively verified and tested on the following server PSU models:

- ✅ **LITEON PS-2461-7H**
- ✅ *[Add your Great Wall / other model here if tested]*

---

## Wiring & Pinout
Default pin configuration (can be redefined in the source code):

| ESP32 Pin | Function | Connects to |
| :--- | :--- | :--- |
| **GPIO 18** | I2C SDA | PSU SDA |
| **GPIO 8**  | I2C SCL | PSU SCL |
| **GPIO X**  | Control | PSU PSON# |

> ⚠️ **Important I2C Note:** While most server PSUs feature internal pull-up resistors on the I2C lines, they can often be too weak for stable high-speed communication. If you experience bus timeouts or communication drops, it is highly recommended to add hardware **2kΩ to 10kΩ pull-up resistors** between the SDA/SCL lines and the `3.3V` rail.

---

## Getting Started
1. Clone this repository and open the project using **PlatformIO** (VS Code).
2. Connect your ESP32 to the server PSU according to the wiring guide above.
3. Flash the firmware to your microcontroller.
4. Open your favorite Serial Monitor tool, set the baud rate to **115200**, and watch the telemetry stream.

---

## Credits & Acknowledgments
This project has been remixed and enhanced based on the following awesome open-source repositories:
- [sxjack/dps750tb_psu_i2c](https://github.com) — PMBus PSU I2C readout implementation used in the **v1** branch.
- `CSPS_TO_USB_AND_WIFI` — PMBus PSU I2C readout & telemetry framework used in the **v2** branch.

---

## License
This project is licensed under the [MIT License](LICENSE).
