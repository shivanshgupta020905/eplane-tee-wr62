# Theoretical Background — E-Plane Tee Junction

## 1. Rectangular Waveguide Fundamentals

A rectangular waveguide is a hollow metallic tube that guides electromagnetic waves by total internal reflection off its conducting walls. For a waveguide with broad wall `a` and narrow wall `b`:

- Only **TE** (Transverse Electric) and **TM** (Transverse Magnetic) modes propagate.
- The **TE₁₀ mode** is the dominant mode with the lowest cutoff frequency.

### Cutoff Frequency (TE₁₀)

$$f_{c,10} = \frac{c}{2a}$$

For WR-62 (`a = 15.8 mm`):

$$f_c = \frac{3 \times 10^8}{2 \times 0.0158} \approx 9.49 \text{ GHz}$$

### Electric Field of TE₁₀ Mode

$$E_y = E_0 \sin\left(\frac{\pi x}{a}\right) e^{-j\beta z}$$

- Field is **zero at sidewalls** (x = 0 and x = a)
- **Maximum at centre** (x = a/2)
- Oriented entirely along **Y-axis** (transverse to propagation)

---

## 2. E-Plane Tee — Structure and Classification

An E-plane Tee (also called a **Series Tee**) is formed by introducing a branch waveguide through the **narrow wall (broad face)** of the main guide such that:

- The branch arm lies in the **E-field plane** (YZ plane for TE₁₀)
- The junction is symmetric about the mid-plane

### Port Designation

| Port | Role |
|------|------|
| Port 1 | Collinear arm (−Z direction) |
| Port 2 | Collinear arm (+Z direction) |
| Port 3 | E-arm / shunt arm (Y direction) |

---

## 3. Scattering Matrix of an Ideal E-Plane Tee

For a lossless, matched, symmetric E-plane Tee, the S-matrix takes the form:

$$[S] = \begin{bmatrix} 0 & 0 & \frac{1}{\sqrt{2}} \\ 0 & 0 & -\frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}} & -\frac{1}{\sqrt{2}} & 0 \end{bmatrix}$$

Key observations:
- **S₁₃ = 1/√2, S₂₃ = −1/√2** → equal magnitude, opposite sign → 180° phase difference
- **S₁₂ = 0** → no direct coupling between the two collinear ports (when E-arm is matched)
- **S₃₃ = 0** → matched at Port 3

> Note: In practice (unmatched junction), S₃₃ ≠ 0 and there is noticeable reflection at Port 3.

---

## 4. Physical Explanation of 180° Phase Difference

When a signal enters Port 3 (E-arm):

1. **Wave propagation**: The signal travels down the E-arm and reaches the T-junction.
2. **Splitting**: At the junction, the wave divides into two components propagating in +Z (toward Port 2) and −Z (toward Port 1) directions.
3. **E-field boundary condition**: The transverse E-field (Eᵧ) must be **continuous** across the junction. However, since the two output waves propagate in **opposite directions**, the field orientation relative to each port reference plane is **opposite**.
4. **Result**: The signal arriving at Port 1 has its E-field pointing in one direction, while the signal at Port 2 has its E-field pointing in the exact opposite direction — a **180° phase difference**.

This can also be understood from the symmetry of the junction: the E-plane Tee is **antisymmetric** about the junction mid-plane when excited from Port 3, whereas the H-plane Tee is symmetric (hence in-phase outputs).

---

## 5. Comparison: E-Plane vs H-Plane Tee

| Property | E-Plane Tee | H-Plane Tee |
|----------|-------------|-------------|
| Branch arm plane | E-field plane | H-field plane |
| Output phase | 180° out of phase | In phase |
| Also called | Series Tee | Shunt Tee |
| S-matrix sign of S₁₃, S₂₃ | Opposite | Same |
| Application | Power divider with phase inversion | In-phase power divider |

---

## 6. Power Division

For an ideal, lossless E-plane Tee excited at Port 3:
- Each output port receives **half the input power**
- In dB: 10 log(0.5) = **−3 dB**

In practice (unmatched junction), the actual value is lower (more negative) due to:
- Impedance mismatch at the junction
- Reflection back into Port 3
- For this simulation: **−4.46 dB** (approximately 1.46 dB excess loss)

---

## 7. Standing Waves and Mismatch

The unmatched junction causes partial reflection of the incident wave at Port 3. The superposition of the incident and reflected waves creates a **standing wave pattern** visible in the E-field magnitude plots (Figs. 5 & 6). This is characterised by alternating field maxima and minima along the E-arm, with a period of λg/2 (half the guide wavelength).
