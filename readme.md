# 🏎️ UC Berkeley ROAR Autonomous Racing Pipeline

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white" alt="OpenCV" />
  <img src="https://img.shields.io/badge/CARLA-Simulator-green?style=for-the-badge" alt="CARLA Simulator" />
  <img src="https://img.shields.io/badge/PID-Control-blue?style=for-the-badge" alt="PID Control" />
  <img src="https://img.shields.io/badge/Awards-3rd%20Place%20Berkeley%20ROAR-bronze?style=for-the-badge" alt="Award" />
  <img src="https://img.shields.io/badge/License-MIT-brightgreen?style=for-the-badge" alt="License" />
</p>

This repository contains the autonomous vehicle perception, control, and path-planning pipeline developed for the **UC Berkeley Robot Open Autonomous Racing (ROAR)** competition. Built to run both in the high-fidelity **CARLA simulator** and on physical **NVIDIA Jetson** autonomous hardware, the system combines real-time computer vision lane detection with adaptive control loops to navigate complex race tracks at maximum speed.

🏆 **Award**: Placed **3rd Place globally** in the UC Berkeley ROAR Autonomous Racing Competition.

---

## 🌟 Key Features

- 👁️ **Computer Vision Perception**: Robust lane detection using OpenCV color masking, edge detection, and Inverse Perspective Mapping (IPM) for bird's-eye view track analysis.
- 🎮 **Adaptive PID & Control Loops**: Dual-axis Proportional-Integral-Derivative (PID) and Pure Pursuit controllers tuned for high-speed cornering and lateral stability.
- 📍 **Waypoint & Racing-Line Planning**: Custom trajectory generators and waypoint shift utilities (`shiftwaypoints.py`) to compute optimal racing lines.
- 🌉 **Multi-Target Hardware Deployment**: Bridges for:
  - **CARLA Simulator** (`runner_sim.py`)
  - **NVIDIA Jetson Edge Hardware** (`runner_jetson.py`)
  - **iOS Sensor Streaming** (`runner_ios.py`)
- 📊 **Real-Time Telemetry & Evaluation**: Built-in competition evaluator (`runner_competition_evaluator.py`) to measure lap times, speed profiles, and trajectory deviations.

---

## 📂 Repository Structure

```
ROARSummer/
├── ROAR/
│   ├── perception/          # OpenCV lane & obstacle detection algorithms
│   ├── control/             # PID, Pure Pursuit, and lateral/longitudinal controllers
│   ├── planning/            # Waypoint generators and racing line planners
│   └── configurations/      # Vehicle & simulator parameter YAML configurations
├── ROAR_Sim/                # CARLA simulator bridge interface
├── ROAR_Jetson/             # NVIDIA Jetson hardware hardware-in-the-loop driver
├── ROAR_iOS/                # Mobile camera & sensor stream receiver
├── runner_sim.py            # Primary entry point for CARLA simulation racing
├── runner_competition_evaluator.py  # Official ROAR competition benchmark runner
├── runner_jetson.py         # Entry point for physical Jetson hardware testing
├── shiftwaypoints.py        # Track waypoint optimization utility
├── requirements.txt         # Python dependencies
└── README.md                # Project documentation
```

---

## 🚀 Quickstart Guide

### 1. Prerequisites

- **Python**: 3.8 or 3.9
- **CARLA Simulator**: 0.9.12 or 0.9.13 (for simulation testing)
- **OpenCV & NumPy**: Installed via pip

### 2. Installation

Clone the repository and install required Python packages:

```bash
git clone https://github.com/krishaygarg/ROARSummer_Krishay_Garg.git
cd ROARSummer_Krishay_Garg
pip install -r requirements.txt
```

### 3. Running in CARLA Simulator

1. Launch your CARLA simulator server instance:
   ```bash
   ./CarlaUE4.sh -world-port=2000
   ```
2. In a separate terminal, start the autonomous driving agent:
   ```bash
   python runner_sim.py
   ```

### 4. Running Competition Evaluation

To benchmark lap performance and vehicle stability:

```bash
python runner_competition_evaluator.py
```

---

## 🔬 System Architecture

```
┌─────────────────┐       ┌─────────────────┐       ┌─────────────────┐
│ Camera / Sensors│ ────> │  OpenCV Vision  │ ────> │ Waypoint & Path │
│ (CARLA / Jetson)│       │  Lane Detection │       │    Planner      │
└─────────────────┘       └─────────────────┘       └────────┬────────┘
                                                             │
┌─────────────────┐       ┌─────────────────┐                │
│ Vehicle Actuation│ <──── │ Adaptive PID   │ <──────────────┘
│ (Steer/Throttle)│       │ Control System  │
└─────────────────┘       └─────────────────┘
```

---

## 📜 License

Distributed under the [MIT License](LICENSE).
