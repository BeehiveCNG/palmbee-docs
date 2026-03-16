# Hardware

This section lists the main hardware components used in the PalmBee drone system.

The hardware setup is designed to support autonomous pollination using PX4 flight control, ROS2 processing, and vision-based navigation.

For wiring and connection details, see the **Wiring Diagram** page.

---

# System Hardware Overview

The PalmBee platform consists of the following core components:

- Flight Controller
- Companion Computer
- Vision Sensor
- Telemetry System
- Optical Flow Sensor
- Radio Receiver
- ESC and Motors
- Power System

---

# Flight Controller

**Pixhawk 6C**

The Pixhawk 6C is the main flight controller responsible for stabilization, motor control, and flight state estimation.

**Key Features**

- PX4 firmware compatible
- Multiple UART telemetry ports
- Dedicated PWM outputs for ESC control
- Supports MAVLink communication with companion computers

**Role in System**

- Flight stabilization
- Motor control
- Sensor integration
- MAVLink communication with Jetson companion computer

---

# Companion Computer

**NVIDIA Jetson Orin Nano**

The Jetson Orin Nano acts as the companion computer responsible for high-level processing tasks such as computer vision and autonomous navigation.

**Key Features**

- GPU acceleration for AI workloads
- Runs Ubuntu + ROS2 Humble
- High-speed USB interfaces
- Supports camera and sensor processing

**Role in System**

- Vision processing
- High-level navigation
- AI-based decision making
- MAVLink communication with PX4

---

# Vision Sensor

**ZED2i Stereo Camera**

The ZED2i camera provides stereo vision capabilities for depth perception and environmental awareness.

**Key Features**

- Stereo depth sensing
- High-resolution RGB imaging
- GPU accelerated processing via SDK
- ROS2 integration support

**Role in System**

- Depth estimation
- Obstacle detection
- Environmental perception
- Visual navigation support

---

# Telemetry System

**CUAV PW-Link**

The telemetry module provides long-range communication between the drone and the ground control station.

**Key Features**

- Long range telemetry link
- MAVLink compatible
- Reliable communication channel

**Role in System**

- Ground station communication
- Telemetry data transmission
- Remote monitoring

---

# Optical Flow Sensor

**MTF-01P Optical Flow**

The optical flow sensor helps estimate ground-relative movement of the drone.

**Key Features**

- Motion estimation
- Altitude and velocity support
- PX4 compatible

**Role in System**

- Position estimation
- Velocity stabilization
- GPS-denied flight assistance

---

# RC Receiver

**SBUS Receiver**

The RC receiver allows manual pilot input when autonomous control is disabled.

**Key Features**

- SBUS protocol
- Low latency control signal
- Compatible with Pixhawk controllers

**Role in System**

- Manual override
- Safety control
- Flight testing

---

# ESC and Motors

**Brushless Motors with ESC**

The drone propulsion system consists of four brushless motors controlled by Electronic Speed Controllers (ESC).

**Key Features**

- PWM control from Pixhawk
- High efficiency propulsion
- Standard quadcopter X configuration

**Role in System**

- Thrust generation
- Drone maneuvering
- Flight stabilization

---

# Power System

The drone is powered using a **4S LiPo battery pack** supplying power to:

- Pixhawk flight controller
- ESC and motors
- Companion computer via power module

**Power Distribution**

- Battery → Power Module
- Power Module → Pixhawk
- Battery → ESC Power Distribution
- Regulated output → Companion computer

---

# Hardware Summary

| Component | Model |
|----------|------|
| Flight Controller | Pixhawk 6C |
| Companion Computer | Jetson Orin Nano |
| Camera | ZED2i Stereo Camera |
| Optical Flow | MTF-01P |
| Telemetry | CUAV PW-Link |
| Receiver | SBUS RC Receiver |
| Motors | Brushless Motors |
| ESC | PWM ESC |
| Battery | 4S LiPo |

---
