# Kalem-TPS5430-StepDown-Selectable

Adjustable DC-DC step-down (buck) power supply module for converting 12–24 V industrial power rails to regulated low-voltage outputs.

This repository contains hardware design files and documentation for the **Kalem-TPS5430-StepDown-Selectable** board.

---

## 1. Overview

The **Kalem-TPS5430-StepDown-Selectable** is a compact, high-efficiency DC-DC buck converter module based on the **Texas Instruments TPS5430** regulator.

It is designed to step down common industrial supply voltages (12–24 V DC) to lower, regulated output voltages suitable for microcontrollers, sensors and auxiliary electronics.

Key characteristics:

- Wide input voltage range suitable for industrial systems  
- Output voltage selected via a feedback resistor network (jumpers or solder links)  
- ENABLE pin for external on/off control  
- Screw terminal connectors for reliable field wiring  

The module is intended as a robust power front-end for embedded, PLC-adjacent and automation projects.

---

## 2. Main Features

- Based on **TPS5430** DC-DC buck regulator  
- Input voltage range: **7–24 V DC nominal** (device rated up to 36 V)  
- Selectable output voltage via feedback resistor network  
- Up to **3 A output current** (thermal and VIN/VOUT dependent)  
- Fixed **500 kHz switching frequency**  
- High efficiency step-down topology  
- Dedicated **ENABLE** pin for logic control  
- Input power LED indicator  
- Screw terminal connectors for VIN, VOUT and GND  
- Compact PCB optimized for industrial use  

> **Note:** Exact output voltage options and resistor values are listed in the PDF datasheet in the `docs/` folder.

---

## 3. Typical Applications

- 24 V → 5 V / 3.3 V power conversion for MCUs (STM32, ESP32, Arduino)  
- Auxiliary power rails in PLC cabinets  
- Powering sensors, communication modules and I/O boards  
- Industrial control panels and automation projects  
- Embedded and IoT systems using a 24 V backbone  

---

## 4. Hardware Overview

### 4.1 Power input

The module accepts a DC input voltage through a screw terminal.

Typical input connections:

- `VIN` – Input supply voltage (7–24 V DC nominal)  
- `GND` – Common ground  

An onboard LED indicates presence of input power.

---

### 4.2 Power output

The regulated output voltage is available on a dedicated screw terminal.

Typical output connections:

- `VOUT` – Regulated output voltage (as selected by feedback resistors)  
- `GND` – Output ground (common with input ground)  

The output voltage is defined by the feedback network connected to the TPS5430 FB pin.

---

### 4.3 Voltage selection (feedback)

The output voltage is set using a resistor divider referenced to the internal **1.221 V** feedback reference of the TPS5430.

- Multiple resistor values are provided on the board  
- Jumpers or solder bridges select the desired output voltage  
- Only **one feedback option** should be enabled at a time  

This approach allows the same PCB to be used for different output voltages without redesign.

---

### 4.4 Enable control

- `ENABLE` – Logic control input  
  - LOW (< 0.5 V): regulator disabled  
  - Floating or HIGH: regulator enabled  

The ENABLE pin has an internal pull-up, so the module turns on by default if the pin is left unconnected.

---

## 5. Basic Connection Example

1. Connect the 12–24 V DC supply to `VIN` and `GND`.  
2. Select the desired output voltage using the feedback jumpers or solder links.  
3. Connect the load to `VOUT` and `GND`.  
4. (Optional) Drive the `ENABLE` pin from an MCU or control signal for power sequencing.  
5. Verify the output voltage before connecting sensitive electronics.

---

