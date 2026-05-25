# E-Plane Tee Junction — WR-62 Waveguide (HFSS Simulation)

> **Microwave Engineering Project** | Department of Electronics & Communication Engineering  
> The LNM Institute of Information Technology, Jaipur

---

## Overview

This project presents the **full-wave electromagnetic simulation** of an air-filled **E-Plane Tee junction** designed for the **WR-62 rectangular waveguide** using Ansys HFSS. The design demonstrates:

- ✅ **Equal power division** — S₁₃ = S₂₃ = −4.46 dB at 15 GHz
- ✅ **180° phase opposition** between the two collinear output ports
- ✅ **TE₁₀ mode** propagation confirmed via field distribution plots
- ✅ Operation across the **Ku-band (12–18 GHz)**

---

## Table of Contents

- [Background Theory](#background-theory)
- [Waveguide Specifications](#waveguide-specifications)
- [Simulation Setup](#simulation-setup)
- [Results](#results)
- [Analysis](#analysis)
- [Key Takeaways](#key-takeaways)
- [Repository Structure](#repository-structure)
- [Author](#author)

---

## Background Theory

An **E-Plane Tee** (Series Tee) is a three-port waveguide junction formed by attaching a shunt arm to the **broad wall** of a main rectangular waveguide. It is classified as an E-plane junction because the auxiliary arm lies in the plane of the dominant **TE₁₀ electric field** (Y-axis).

### Why 180° Phase Difference?

When a signal enters via the **E-arm (Port 3)**:

1. It excites the TE₁₀ mode in the main guide.
2. At the junction, the wave splits and travels in **+Z and −Z directions** toward Port 1 and Port 2.
3. The **boundary conditions** require the transverse E-field to **reverse direction** for one of the output arms.
4. This geometrical antisymmetry produces a **180° phase opposition** between the two outputs — the defining characteristic of an E-plane junction.

> This behaviour distinguishes the E-Plane Tee from the **H-Plane Tee**, where both outputs are in-phase.

---

## Waveguide Specifications

| Parameter | Value |
|-----------|-------|
| Waveguide Standard | WR-62 |
| Broad wall width `a` | 15.8 mm |
| Narrow wall height `b` | 7.9 mm |
| Fill medium | Air (εᵣ = 1) |
| Dominant mode | TE₁₀ |
| Theoretical cutoff frequency | ~9.49 GHz |
| Operating frequency | 15 GHz (Ku-band) |
| Simulation tool | Ansys HFSS 2025 R2 |

**Cutoff frequency calculation:**

$$f_c = \frac{c}{2a} = \frac{3 \times 10^8}{2 \times 15.8 \times 10^{-3}} \approx 9.49 \text{ GHz}$$

---

## Simulation Setup

- **Structure:** Three-port E-plane Tee junction modelled in HFSS 3D Modeller
- **Boundaries:** Perfect Electric Conductor (PEC) on all walls
- **Excitation:** Wave ports at all three ports (Port 1, Port 2, Port 3)
- **Analysis:** Frequency sweep from 7.5 GHz to 22.5 GHz
- **Field plots:** YZ and XZ surface cut planes for E-field distribution

### Port Configuration

```
        Port 3 (E-arm)
            |
            |   ← Signal Input
            |
Port 1 ----[T]---- Port 2
   (−Z)            (+Z)
```

---

## Results

### S-Parameter Magnitude (Fig. 2)

- **S₁₃ = S₂₃ = −4.46 dB** at 15 GHz — equal power to both output ports
- Curves overlap throughout the Ku-band (9.5–20 GHz), confirming symmetry
- Excess loss beyond the ideal −3 dB is due to **junction impedance mismatch** (inherent to unmatched E-plane Tee)

### Phase Difference (Figs. 3 & 4)

- Polar plot of S₁₃ and S₂₃ shows **mirror-image traces** → 180° opposition
- Phase plot confirms: **∠S₁₃ − ∠S₂₃ ≈ +180.14°** at 15 GHz and **≈ −179.88°** at 13 GHz

### E-Field Distribution

| Plot | Observation |
|------|-------------|
| **Mag_E (YZ plane)** | Equal field amplitude at Port 1 & Port 2 at 15 GHz |
| **Mag_E (XZ plane)** | Sinusoidal variation across broad wall → confirms TE₁₀ mode; standing wave pattern visible due to junction mismatch |
| **Vector_E (YZ plane)** | Vectors point **+Y at Port 1** and **−Y at Port 2** simultaneously → direct visual proof of 180° phase opposition |

---

## Analysis

### TE₁₀ Mode Verification
The XZ cross-section (Fig. 6) shows a sinusoidal E-field with a maximum at the centre and nulls at the sidewalls — the hallmark of the dominant TE₁₀ mode. No higher-order modes are excited within the operating band.

### Equal Power Division
S₁₃ = S₂₃ = −4.46 dB confirms equal power division. The ~1.46 dB excess loss (compared to ideal −3 dB) is attributed to the impedance mismatch at the unmatched junction — expected behaviour for a simple E-plane Tee without matching networks.

### Phase Opposition Mechanism
The E-field reversal arises from the geometry of the junction. Waves exiting toward Port 1 (−Z) and Port 2 (+Z) travel in opposite directions; the boundary conditions at the junction force the transverse E-field component to flip sign for one arm. The vector plot (Fig. 7) provides a direct spatial snapshot of this antisymmetry.

### Standing Waves
The standing wave pattern in Figs. 5 & 6 is caused by superposition of incident and reflected waves at the unmatched junction — consistent with poor return loss at Port 3 for an unmatched E-plane Tee.

---

## Key Takeaways

1. **E-Plane Tee = 180° hybrid** — any signal entering the E-arm splits equally with a 180° phase difference between outputs.
2. The junction is inherently unmatched; matching networks (e.g., inductive posts, diaphragms) are needed for practical applications.
3. HFSS simulation closely matches theoretical predictions for both cutoff frequency and power division symmetry.
4. Vector field plots are a powerful tool for visually verifying phase relationships in waveguide components.

---

## Repository Structure

```
eplance-tee-wr62/
│
├── README.md                  ← You are here
├── docs/
│   ├── theory.md              ← Detailed theoretical background
│   └── simulation_notes.md    ← HFSS setup notes and solver settings
├── results/
│   ├── s_parameters.md        ← Tabulated S-parameter data
│   └── figures/               ← Simulation screenshots (HFSS plots)
│       ├── fig1_hfss_model.png
│       ├── fig2_s_param_magnitude.png
│       ├── fig3_polar_plot.png
│       ├── fig4_phase_difference.png
│       ├── fig5_mag_e_yz.png
│       ├── fig6_mag_e_xz.png
│       └── fig7_vector_e_yz.png
└── report/
    └── 24UEC228_Project28_EplaneTee.pdf   ← Full project report
```

---

## Author

**Shivansh Gupta**  
Roll No.: 24UEC228  
B.Tech Electronics & Communication Engineering  
The LNM Institute of Information Technology, Jaipur

*Course: Microwave Engineering Theory | Project No. 28*  
*Submitted: May 2026*

---

## References

1. D. M. Pozar, *Microwave Engineering*, 4th ed., Wiley, 2012.
2. Ansys HFSS Documentation, 2025 R2.
3. R. E. Collin, *Foundations for Microwave Engineering*, 2nd ed., IEEE Press, 2001.
4. WR-62 Waveguide Standard — IEEE Standard 521.
