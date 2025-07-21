# Moving Coil Loudspeaker Design

A complete analytical and numerical study of a **midrange moving coil loudspeaker**, designed for the **ISVR6137 Electroacoustics** module at the University of Southampton. This project models the loudspeaker from first principles, simulates it using COMSOL Multiphysics, and evaluates its performance through SPL, impedance, and efficiency metrics.

---

## 🔧 Project Overview

This repository presents the design, analysis, and simulation of a sealed-enclosure loudspeaker system optimised for speech and music in the midrange frequency range (150 Hz – 5 kHz). The study incorporates:

- Magnetic and mechanical design of the voice coil
- Cabinet configuration using MDF
- Thiele-Small parameter calculation
- Sound pressure level and efficiency estimation
- Electro-mechanical and acoustic coupling
- Python-based analytical modelling
- COMSOL numerical simulation for comparison

---

## 📐 Technical Summary

| Component             | Description                                  |
|-----------------------|----------------------------------------------|
| **Driver Type**       | Moving Coil Loudspeaker                      |
| **Magnet**            | Neodymium (1 T flux density)                 |
| **Diaphragm**         | Polypropylene (10.1 g mass)                  |
| **Cabinet Volume**    | 6.91 L (Sealed MDF Enclosure)                |
| **Resonance Freq.**   | ~131.56 Hz                                   |
| **SPL (Midrange)**    | ~85 dB ±3 dB (150 Hz – 5 kHz)                |
| **Efficiency (ηEA)**  | 1.5% (avg), peak ~3.5%                       |
| **Impedance**         | Nominal 8 Ω, peak ~14 Ω at resonance         |
| **Cost Estimate**     | £75 (Components & Assembly)                  |

---

## 🧮 Features & Analysis

### ✅ Analytical Model (Python)
- Calculates Thiele-Small parameters
- Plots:
  - Sound Pressure Level (SPL)
  - Diaphragm Displacement
  - Electrical Impedance
  - Electroacoustic Efficiency
- Estimates resonance behaviour and power conversion

### ✅ Numerical Model (COMSOL)
- Multiphysics model including:
  - Magnetomechanics
  - Solid mechanics
  - Pressure acoustics
- Incorporates boundary conditions and realistic materials
- Validates analytical predictions up to 10 kHz

---

## 📊 Key Results

- **Flat SPL Response:** 85 dB in midrange; suitable for vocals and general music playback.
- **Controlled Excursion:** Displacement well managed by suspension and cabinet design.
- **Efficiency:** Competitive for sealed-box design, with trade-off between fidelity and power.
- **Impedance Profile:** Resonance clearly visible at 131.56 Hz, with good amplifier compatibility.

---

## 📁 Repository Structure

```bash
📦 Loudspeaker-Design
├── 📂 models
│   ├── analytical_model.py       # Python code for analytical model
│   └── comsol_model_description/ # COMSOL setup and images
├── 📂 figures
│   └── *.png                     # Plots (SPL, Impedance, etc.)
├── 📄 report.pdf                 # Full project write-up
└── README.md                    # This file
