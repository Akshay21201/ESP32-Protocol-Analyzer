# ESP32 Multi-Protocol Analyzer & Fault Simulator

![ESP32](https://img.shields.io/badge/ESP32-WROOM-E7352C?logo=espressif)
![Language](https://img.shields.io/badge/Language-C++-00599C?logo=cplusplus)
![IDE](https://img.shields.io/badge/IDE-Arduino_IDE-00979D?logo=arduino)
![Protocols](https://img.shields.io/badge/Protocols-UART%20%7C%20SPI%20%7C%20I²C-blue)
![Communication](https://img.shields.io/badge/MQTT-WebSockets-success)
![PCB](https://img.shields.io/badge/PCB-Custom-green)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

# Working Prototype

<p align="center">
<img src="images/working-model/user-interface/user-interface.jpeg" width="50%">
</p>

---

## Table of Contents

- [Overview](#overview)
- [Motivation](#motivation)
- [Key Features](#key-features)
- [Technology Stack](#technology-stack)
- [Hardware Components](#hardware-components)
- [System Architecture](#system-architecture)
- [Project Gallery](#project-gallery)
- [Protocol Implementations](#protocol-implementations)
- [MQTT Integration](#mqtt-integration)
- [Communication Fault Simulation](#communication-fault-simulation)
- [Educational Dashboard](#educational-dashboard)
- [PCB Design](#pcb-design)
- [Circuit Design](#circuit-design)
- [Project Documentation](#project-documentation)
- [Future Improvements](#future-improvements)
- [Learning Outcomes](#learning-outcomes)

---

# Overview

The **ESP32 Multi-Protocol Analyzer & Fault Simulator** is an embedded systems project designed to demonstrate and visualize three widely used communication protocols:

- UART
- SPI
- I²C

Unlike conventional protocol analyzers that simply monitor communication, this system **generates communication frames using software-driven (bit-banged) protocol implementation**, validates peripheral responses, visualizes communication on a TFT LCD, and publishes protocol data over Wi-Fi using MQTT for remote monitoring through a web dashboard.

The project also simulates communication faults such as **noise, broken frames, and incorrect frames**, allowing users to understand protocol behavior under various operating conditions.

---

# Motivation

Debugging embedded communication protocols often requires expensive logic analyzers or oscilloscopes. This project was developed as a compact educational platform capable of:

- Demonstrating protocol communication visually
- Comparing transmitted and received frames
- Simulating communication errors
- Understanding ACK/NACK responses
- Monitoring protocols remotely over Wi-Fi

The system serves as both a learning platform and a protocol debugging tool.

---

# Key Features

- Software-driven UART implementation
- Software-driven SPI implementation
- Software-driven I²C implementation
- Real-time TFT LCD waveform visualization
- MQTT communication over Wi-Fi
- Browser-based monitoring dashboard
- Communication fault simulation
- ACK/NACK verification
- Custom PCB design
- Breadboard prototype development
- Wokwi simulation
- Historical frame visualization
- Interactive protocol information pages

---

# Technology Stack

| Category | Technologies |
|----------|--------------|
| Microcontroller | ESP32-WROOM |
| Programming Language | C++ |
| Development Environment | Arduino IDE |
| Communication Protocols | UART, SPI, I²C, MQTT |
| Communication Method | Wi-Fi |
| Display | ILI9341 TFT LCD |
| EEPROM | 24LC256-I/P |
| SPI Flash Memory | W25X10CLSNIG |
| UART Interface | MAX485EPA RS485 Transceiver |
| PCB Design | KiCad |
| Web Technologies | HTML, CSS, JavaScript |
| Simulation | Wokwi |

---

# Hardware Components

| Component | Purpose |
|-----------|---------|
| ESP32-WROOM | Main controller responsible for protocol generation, communication, and visualization |
| ILI9341 TFT LCD | Displays protocol waveforms and user interface |
| MAX485EPA | UART communication using RS485 |
| 24LC256-I/P EEPROM | I²C peripheral for protocol testing |
| W25X10CLSNIG Flash Memory | SPI peripheral for protocol testing |
| Push Buttons (3) | Select UART, SPI, or I²C mode |
| LEDs (2) | MQTT connection status and protocol activity indication |
| Custom PCB | Integrated hardware implementation |

---

# System Architecture

<p align="center">
  <img src="circuit/diagrams/system-architecture.jpeg" width="80%">
</p>

---

# Communication Workflow

<p align="center">
  <img src="circuit/diagrams/communication-workflow.jpeg" width="50%">
</p>

---

# Project Development Workflow

<p align="center">
  <img src="circuit/diagrams/development-workflow.jpeg" width="50%">
</p>

---

# Project Gallery

## Simulation

| UART | SPI | I²C |
|------|-----|------|
| ![](images/simulation/uart-simulation.jpeg) | ![](images/simulation/spi-simulation.png) | ![](images/simulation/i2c-simulation.jpeg) |

---

## Breadboard Prototype

| Control Circuit | Protocol Testing |
|-----------------|------------------|
| ![](images/breadboard-testing/control-circuit.jpeg) | ![](images/breadboard-testing/protocol-testing.jpeg) |

---

# Protocol Implementations

The ESP32 implements all three communication protocols using **software-driven (bit-banged) communication**, providing complete control over frame generation, timing, and fault injection.

---

## UART Communication

The ESP32 communicates with a **MAX485EPA RS485 transceiver** by transmitting predefined UART frames. The received response is validated through ACK/NACK detection and simultaneously visualized on the TFT LCD and web dashboard.

### UART Simulation

<p align="center">
  <img src="images/serial-monitor/uart-simulation.jpeg" width="70%">
</p>

### UART Serial Monitor

![](images/serial-monitor/uart-output.png)

---

## SPI Communication

SPI communication is demonstrated using the **W25X10CLSNIG SPI Flash Memory**. The ESP32 generates SPI frames, receives peripheral responses, and visualizes communication in real time.

### SPI Simulation

<p align="center">
  <img src="images/serial-monitor/spi-simulation.jpeg" width="100%">
</p>

### SPI Serial Monitor

![](images/serial-monitor/spi-output.png)

---

## I²C Communication

I²C communication is implemented using the **24LC256-I/P EEPROM**. Frame generation, acknowledgement detection, and visualization are handled entirely by the ESP32 firmware.

### I²C Simulation

<p align="center">
  <img src="images/serial-monitor/i2c-simulation.jpeg" width="100%">
</p>

### I²C Serial Monitor

![](images/serial-monitor/i2c-output.png)

---

# MQTT Integration

Protocol data is transmitted wirelessly using MQTT over Wi-Fi, enabling real-time visualization on a browser-based dashboard.

The ESP32 publishes protocol frames and protocol status over MQTT, allowing the browser dashboard to visualize communication in real time.

### MQTT Connection

<p align="center">
  <img src="images/serial-monitor/mqtt-connected.png" width="100%">
</p>

---

# Device User Interface

| Home Screen | Protocol Selection |
|-------------|--------------------|
| ![](images/working-model/user-interface/user-interface.jpeg) | ![](images/working-model/user-interface/user-menu.jpeg) |

---

# Communication Fault Simulation

To demonstrate protocol reliability and error handling, four communication scenarios were implemented. The TFT LCD displays the transmitted waveform, while the browser dashboard visualizes the processed communication after applying the selected fault condition.

- Correct Frame
- Wrong Frame
- Broken Frame
- Noise Injection

---

## Correct Frame

| Protocol | Hardware (TFT LCD) | Web Dashboard |
|----------|---------------------|---------------|
| UART | ![](images/working-model/correct/uart-correct.jpeg) | ![](images/software/correct/uart-correct.png) |
| SPI | ![](images/working-model/correct/spi-correct.jpeg) | ![](images/software/correct/spi-correct.png) |
| I²C | ![](images/working-model/correct/i2c-correct.jpeg) | ![](images/software/correct/i2c-correct.png) |

---

## Wrong Frame

| Protocol | Hardware (TFT LCD) | Web Dashboard |
|----------|---------------------|---------------|
| UART | ![](images/working-model/wrong/uart-wrong.jpeg) | ![](images/software/wrong/uart-wrong.png) |
| SPI | ![](images/working-model/wrong/spi-wrong.jpeg) | ![](images/software/wrong/spi-wrong.png) |
| I²C | ![](images/working-model/wrong/i2c-wrong.jpeg) | ![](images/software/wrong/i2c-wrong.png) |

---

## Broken Frame

| Protocol | Hardware (TFT LCD) | Web Dashboard |
|----------|---------------------|---------------|
| UART | ![](images/working-model/broken/uart-broken.jpeg) | ![](images/software/broken/uart-broken.png) |
| SPI | ![](images/working-model/broken/spi-broken.jpeg) | ![](images/software/broken/spi-broken.png) |
| I²C | ![](images/working-model/broken/i2c-broken.jpeg) | ![](images/software/broken/i2c-broken.png) |

---

## Noise Injection

| Protocol | Hardware (TFT LCD) | Web Dashboard |
|----------|---------------------|---------------|
| UART | ![](images/working-model/noise/uart-noise.jpeg) | ![](images/software/noise/uart-noise.png) |
| SPI | ![](images/working-model/noise/spi-noise.jpeg) | ![](images/software/noise/spi-noise.png) |
| I²C | ![](images/working-model/noise/i2c-noise.jpeg) | ![](images/software/noise/i2c-noise.png) |

---

# Educational Dashboard

The web dashboard was designed not only for monitoring protocol communication but also as an educational interface for understanding serial communication protocols.

## Protocol Theory

The dashboard provides concise information about the supported communication protocols.

| UART | SPI | I²C |
|------|-----|------|
| ![](images/software/theory/uart-theory.jpeg) | ![](images/software/theory/spi-theory.jpeg) | ![](images/software/theory/i2c-theory.jpeg) |

---

## Past Frame History

Previously transmitted communication frames are stored and displayed on the dashboard, allowing users to review earlier protocol transactions.

| UART | SPI | I²C |
|------|-----|------|
| ![](images/software/past-frames/uart-past-frames.jpeg) | ![](images/software/past-frames/spi-past-frames.jpeg) | ![](images/software/past-frames/i2c-past-frames.jpeg) |

---

# PCB Design

A custom PCB was designed to integrate the ESP32, communication peripherals, TFT LCD interface, status LEDs, and user controls into a compact embedded platform.

| PCB Layout | 3D View |
|-----------|----------|
| ![](circuit/pcb/pcb-layout.png) | ![](circuit/pcb/pcb-3d.png) |

---

## Communication Routing

| UART | SPI | I²C |
|------|-----|------|
| ![](circuit/pcb/uart-routing.png) | ![](circuit/pcb/spi-routing.png) | ![](circuit/pcb/i2c-routing.png) |

---

# Circuit Design

## Block Diagram

<p align="center">
  <img src="circuit/diagrams/block-diagram.png" width="90%">
</p>

---

## Circuit Schematic

<p align="center">
  <img src="circuit/schematic/schematic.png" width="80%">
</p>

---

# Project Documentation

A detailed project report containing the system architecture, hardware design, firmware implementation, PCB design, testing methodology, and project outcomes is available below.

📄 **Project Report**

- [Protocol Analyzer Report](docs/protocol-analyzer-report.pdf)

---

# Source Code

The firmware source code has intentionally not been included in this public repository.

This repository is intended to showcase the project's:

- Hardware Design
- PCB Design
- System Architecture
- Communication Protocols
- MQTT Integration
- Testing Methodology
- Project Documentation
- Final Results

while keeping the implementation private.

---

# Future Improvements

Some potential enhancements for future versions include:

- CAN Bus communication support
- USB communication analysis
- Ethernet-based protocol monitoring
- SD Card logging
- OTA firmware updates
- BLE-based monitoring
- Real-time waveform plotting
- Additional communication protocols
- Higher-speed protocol support
- Improved graphical dashboard

---

# Learning Outcomes

Through this project, I gained practical experience in:

- Embedded Systems Design
- ESP32 Development
- Software-driven UART, SPI, and I²C Communication
- MQTT Communication
- Wi-Fi Networking
- PCB Design using KiCad
- Embedded Graphics using TFT LCD
- Communication Protocol Analysis
- Fault Injection and Testing
- Hardware Debugging
- Embedded Web Interfaces
- System Integration

---

# Repository Structure

```text
ESP32-Multi-Protocol-Analyzer/
│
├── circuit/
│   ├── diagrams/
│   ├── pcb/
│   └── schematic/
│
├── code/
│
├── docs/
│
└── images/
    ├── simulation/
    ├── breadboard-testing/
    ├── serial-monitor/
    ├── software/
    └── working-model/
```

---

# Author

**Akshay Patankar**

Bachelor of Engineering (Electronics & Telecommunication)

Honours in Artificial Intelligence & Machine Learning

Pune Institute of Computer Technology (PICT)

---

# License

This project is licensed under the **MIT License**.

See the [LICENSE](LICENSE) file for more information.

---
