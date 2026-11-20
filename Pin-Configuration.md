# IoT Based Laptop Live Tracking & Anti-Theft System – Pin Configuration

## ESP32 + NEO-6M GPS Pin Mapping

> **Note:** The project report specifies UART communication between ESP32 and NEO-6M GPS, but it does not give exact GPIO numbers. The GPIOs below are an example recommended mapping; confirm with the actual ESP32 board and wiring before connecting.

| Component | Signal | ESP32 Pin (suggested) | Purpose |
|---|---|---|
| NEO-6M GPS | TX | GPIO 16 (RX2) | GPS sends serial data to ESP32 |
| NEO-6M GPS | RX | GPIO 17 (TX2) | ESP32 sends serial commands to GPS (if needed) |

## Power Connections (as described in the project report)

| Component | Connection | Purpose |
|---|---|---|
| 3.7V LiPo Battery | TP4056 battery terminals (B+ / B−) | Rechargeable backup battery |
| TP4056 Charging Module | Battery charging/protection module | Charges the LiPo battery via USB input |
| Boost Converter | Boost converter input from battery/charging output as supported by module wiring | Raises battery voltage to 5V |
| Boost Converter | 5V output → ESP32 5V/VIN input (board-dependent) | Provides 5V supply to ESP32 |
| Common Ground | Battery/boost/ESP32 grounds connected together as appropriate | Shared electrical reference |

## Power Flow

**3.7V LiPo Battery → TP4056 Charging Module → 5V Boost Converter → ESP32**

The report describes a LiPo battery, TP4056 charging module, and boost converter that increases 3.7V to 5V to power the ESP32. Follow the labels and wiring diagram for the specific charging/boost modules; this table is not a substitute for checking module terminals.

## GPS Communication

- GPS module communicates with ESP32 over UART (serial).
- GPS TX connects to ESP32 RX.
- GPS RX connects to ESP32 TX (optional if the setup only reads GPS data).
- Ensure signal voltage compatibility and confirm the GPS module's supply requirements from its datasheet.

## Report-Confirmed Components

- ESP32 microcontroller
- NEO-6M GPS module
- 3.7V Lithium Polymer battery
- TP4056 battery charging module
- Voltage boost converter (3.7V to 5V)

**Pin numbers are not specified in the uploaded project report.** The GPIO16/GPIO17 UART mapping above is only a suggested example, not a confirmed project wiring detail.
