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

---

## 🧮 Analytical Calculations

All analytical computations are performed using Python and follow fundamental acoustics and electromechanical transduction principles. Below is a breakdown of key formulas and results.

---

### 🎛️ 1. Voice Coil Design

**Number of Turns**  
\[
N = \frac{l_{\text{coil}} \times \text{layers}}{2 \times r_{\text{wire}}} = 533.3
\]

**Wire Length**  
\[
l_{\text{wire}} = 2\pi r_{\text{coil}} \times N = 6.7 \, \text{m}
\]

**Mass of Voice Coil**  
\[
M_{\text{wire}} = \frac{N(2r_{\text{coil}})\pi^2 (2r_{\text{wire}})^2 \rho}{4} = 1.01 \, \text{g}
\]

**Electrical Resistance**  
\[
R_E = \frac{4 r_{\text{coil}} l_{\text{coil}} \rho}{(2r_{\text{wire}})^3} = 6.9 \, \Omega
\]

**Inductance**  
\[
L_E = \frac{\mu_r \mu_0 N^2 \pi r_{\text{coil}}^2}{h_{\text{coil}}} = 0.561 \, \text{mH}
\]

---

### 🪶 2. Diaphragm & Cabinet Calculations

**Diaphragm Area**  
\[
S_D = \pi r^2 = 0.0154 \, \text{m}^2
\]

**Cabinet Volume**  
\[
V = H \times W \times D = 0.2 \times 0.192 \times 0.18 = 0.00691 \, \text{m}^3
\]

**Cabinet Stiffness**  
\[
K_{\text{cab}} = \frac{\rho_0 c_0^2 S_D^2}{V} = 4755.84 \, \text{N/m}
\]

**Total Stiffness**  
\[
K_T = K_{\text{suspension}} + K_{\text{cab}} = 2800 + 4755.84 = 7555.84 \, \text{N/m}
\]

**Diaphragm Mass**  
\[
M_D = \rho \times S_D \times t = 10.1 \, \text{g}
\]

**Total Moving Mass**  
\[
M_{\text{MS}} = M_D + M_{\text{wire}} = 11.11 \, \text{g}
\]

---

### 🔁 3. Thiele-Small Parameters

| Parameter | Value       | Unit    |
|-----------|-------------|---------|
| Resonant Frequency (\(f_s\)) | 131.56     | Hz      |
| Compliance (\(C_{MS}\))      | \(3.57 \times 10^{-4}\) | m/N     |
| Stiffness (\(K_T\))          | 7555.84    | N/m     |
| Moving Mass (\(M_{MS}\))     | 11.11      | g       |
| Force Factor (\(BL\))        | 6.7        | T·m     |
| Quality Factor (Qms)         | 1.52       | —       |
| Electrical Q (Qes)           | 1.40       | —       |
| Total Q (Qts)                | 0.73       | —       |

---

### 🔊 4. Sound Pressure Level (SPL)

Using:

\[
P(f) = \frac{\rho_0 \omega Q_v}{2\pi r}
\]

Where volume velocity \( Q_v \) is derived from the electromechanical model.

SPL is then:

\[
SPL = 20 \log_{10} \left(\frac{P(f)}{20 \mu Pa} \right)
\]

---

### 📉 5. Displacement Amplitude

\[
X(f) = \frac{Q_v}{j \omega S_D}
\]

- Max displacement: 0.35 mm at low frequencies
- Controlled at resonance via damping

---

### ⚡ 6. Electrical Impedance

\[
Z_E = R_E + j\omega L_E + \frac{(BL)^2}{Z_M}
\]

Where mechanical impedance:

\[
Z_M = R_M + j(\omega M_{MS} - \frac{1}{\omega C_{MT}})
\]

---

### 🔋 7. Electroacoustic Efficiency

\[
\eta_{EA} = \frac{W_A}{W_E} \times 100
\]

Where:

- \(W_A = \frac{|Q_v|^2 \cdot \text{Re}(Z_{acoustic})}{2}\)
- \(W_E = \frac{|I|^2 R_E}{2}\)

- Peak Efficiency: **~3.5%**
- Midrange Efficiency: **~1.5%**

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
