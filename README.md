# 📢 Loudspeaker Design & Analysis

![Python](https://img.shields.io/badge/Code-Python-blue?logo=python)
![COMSOL](https://img.shields.io/badge/Simulation-COMSOL-informational)
![Project Type](https://img.shields.io/badge/Acoustic_Engineering-critical)

This project presents the **design, analytical modeling, and numerical simulation** of a midrange **moving coil loudspeaker**. The system is designed to reproduce speech and music in the 150 Hz – 5 kHz range with **controlled SPL**, **efficient diaphragm motion**, and **realistic cabinet modeling**.

---

## 🧰 Methodology

### 1. 📐 Mechanical & Electrical Design
- Designed key loudspeaker components: magnet, coil, diaphragm, spider, cabinet.
- Calculated **Thiele-Small Parameters** using Python scripts.

### 2. 🧮 Analytical Modelling (Python)
- Used numerical methods to compute SPL, impedance, displacement, and efficiency.
- Created graphs to visualize acoustic and electrical performance.

### 3. 📊 Numerical Simulation (COMSOL)
- Simulated magnetomechanics, pressure acoustics, and solid mechanics.
- Used Perfectly Matched Layers (PML) and mesh refinement to validate analytical results.

---

## 🎯 Design Specifications

| Parameter               | Value               | Unit         |
|------------------------|---------------------|--------------|
| **Diaphragm Material** | Polypropylene       | —            |
| **Magnet Type**        | Neodymium (B = 1 T) | —            |
| **Cabinet Volume**     | 6.91                | Litres       |
| **Diaphragm Area**     | 0.0154              | m²           |
| **Resonance Frequency**| 131.56              | Hz           |
| **BL Factor**          | 6.7                 | T·m          |
| **Total Stiffness**    | 7555.84             | N/m          |
| **Efficiency (Peak)**  | 3.5%                | —            |
| **Total Cost**         | £75                 | GBP          |

---

## 🧮 Analytical Calculations

All analytical computations are performed using Python based on standard electroacoustic formulas. Here's a breakdown of major formulas and results:

---

### 🎛️ 1. Voice Coil Design

- **Number of Turns:**  
  N = (l_coil × layers) ÷ (2 × r_wire) = **533.3**

- **Wire Length:**  
  l_wire = 2π × r_coil × N = **6.7 m**

- **Mass of Voice Coil:**  
  M_wire = [N × (2 × r_coil) × π² × (2 × r_wire)² × ρ] ÷ 4 = **1.01 g**

- **Electrical Resistance:**  
  R_E = [4 × r_coil × l_coil × ρ] ÷ (2 × r_wire)³ = **6.9 Ω**

- **Inductance:**  
  L_E = [μ_r × μ₀ × N² × π × r_coil²] ÷ h_coil = **0.561 mH**

---

### 🪶 2. Diaphragm & Cabinet Calculations

- **Diaphragm Area:**  
  S_D = π × r² = **0.0154 m²**

- **Cabinet Volume:**  
  V = H × W × D = 0.2 × 0.192 × 0.18 = **0.00691 m³**

- **Cabinet Stiffness:**  
  K_cab = (ρ₀ × c₀² × S_D²) ÷ V = **4755.84 N/m**

- **Total Stiffness:**  
  K_T = K_suspension + K_cab = 2800 + 4755.84 = **7555.84 N/m**

- **Diaphragm Mass:**  
  M_D = ρ × S_D × t = **10.1 g**

- **Total Moving Mass:**  
  M_MS = M_D + M_wire = **11.11 g**

---

### ⚙️ 3. Thiele-Small Parameters

| Parameter               | Value           |
|-------------------------|-----------------|
| Resonant Frequency (f_s)| 131.56 Hz       |
| Compliance (C_MS)       | 3.57×10⁻⁴ m/N   |
| Total Stiffness (K_T)   | 7555.84 N/m     |
| Moving Mass (M_MS)      | 11.11 g         |
| Force Factor (BL)       | 6.7 T·m         |
| Mechanical Q (Q_ms)     | 1.52            |
| Electrical Q (Q_es)     | 1.40            |
| Total Q (Q_ts)          | 0.73            |

---

### 🔊 4. Sound Pressure Level (SPL)

**Pressure Formula:**  
P(f) = (ρ₀ × ω × Q_v) ÷ (2π × r)

**SPL Formula:**  
SPL = 20 × log₁₀(P / 20 μPa)

---

### 📉 5. Displacement Amplitude

**Displacement:**  
X(f) = Q_v ÷ (j × ω × S_D)

Max displacement occurs below 150 Hz — controlled near resonance.

---

### ⚡ 6. Electrical Impedance

**Electrical Impedance:**  
Z_E = R_E + jωL_E + (BL)² ÷ Z_M

**Mechanical Impedance:**  
Z_M = R_M + j(ωM_MS - 1 ÷ (ωC_MT))

---

### 🔋 7. Efficiency

**Electroacoustic Efficiency:**  
η_EA = (W_A ÷ W_E) × 100

- W_A = |Q_v|² × Re(Z_acoustic) ÷ 2  
- W_E = |I|² × R_E ÷ 2  
- Peak: **3.5%**, Midrange: **~1.5%**

---

## 📈 Visual Analysis

### 🔊 Sound Pressure Level (SPL)

| ![SPL Graph](./figures/spl_plot.png) |
|:--:|
| *Figure: SPL across frequency (flat from 150 Hz to 5 kHz)* |

---

### 🧷 Diaphragm Displacement

| ![Displacement](./figures/displacement_plot.png) |
|:--:|
| *Figure: Maximum displacement occurs <150 Hz, controlled at resonance* |

---

### ⚡ Electrical Impedance 

| ![Impedance](./figures/impedance_plot.png) |
|:--:|
| *Figure: Peak impedance near resonance (14 Ω), nominal 8 Ω* |

---

### 📊 Electroacoustic Efficiency

| ![Efficiency](./figures/efficiency_plot.png) |
|:--:|
| *Figure: Peaks at 3.5% near 131 Hz, ~1.5% midrange typical for sealed-box drivers* |

---

### ⚙️ Real & Imaginary Parts of Impedance

| ![Real/Imag Impedance](./figures/real_imag_impedance_plot.png) |
|:--:|
| *Figure: Real and imaginary parts of impedance — shows energy dissipation and phase behavior across frequency* |


## 🔍 Insights

### ✅ Strengths
- Flat **midrange SPL** (85 dB ±3 dB)
- **Controlled diaphragm excursion** for low distortion
- **Robust driver and magnet design**
- Affordable and simple **sealed cabinet**

### ⚠️ Limitations
- Low-frequency roll-off under 150 Hz (not suitable for bass)
- Lower efficiency compared to ported enclosures
- Sharp cabinet edges may cause diffraction

---

## 🏗️ Future Enhancements

- Use vented cabinet to improve bass response
- Optimize voice coil for higher BL product
- Apply **internal bracing and fillets** to reduce diffraction
- Replace polypropylene with **carbon fiber cone** for higher stiffness

---

## 📁 Project Structure

```bash
📦 Loudspeaker-Design
├── 📂 models
│   ├── analytical_model.py       # Python model with SPL, impedance, etc.
│   └── comsol_model/             # COMSOL project files and setup
├── 📂 figures
│   ├── spl_plot.png
│   ├── displacement_plot.png
│   ├── impedance_plot.png
│   └── efficiency_plot.png
├── 📄 report.pdf                 # Full detailed report
└── README.md                    # This file
