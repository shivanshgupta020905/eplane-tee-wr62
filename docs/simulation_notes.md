# HFSS Simulation Setup Notes

## Software
- **Tool:** Ansys Electronics Desktop (HFSS) 2025 R2
- **Module:** 3D Modeller (Modal Network)
- **Solution type:** Modal

---

## Geometry

### Main Waveguide
- Cross-section: 15.8 mm × 7.9 mm (WR-62 standard)
- Length: Sufficient to support wave port excitation and avoid evanescent field overlap

### E-Arm (Port 3)
- Same cross-section as main guide
- Connected perpendicular to the broad wall (narrow wall junction)
- Centred along the Z-axis of the main guide

### Material
- All volumes: **Air** (εᵣ = 1, μᵣ = 1)
- All boundaries: **Perfect Electric Conductor (PEC)**

---

## Meshing
- Adaptive mesh refinement enabled
- Convergence criterion: ΔS < 0.02 between adaptive passes
- Maximum number of passes: 20

---

## Excitation

| Port | Type | Mode |
|------|------|------|
| Port 1 | Wave Port | TE₁₀ |
| Port 2 | Wave Port | TE₁₀ |
| Port 3 | Wave Port | TE₁₀ |

- Integration line set along Y-axis for each port (consistent with TE₁₀ E-field orientation)

---

## Analysis Setup

| Setting | Value |
|---------|-------|
| Sweep type | Fast |
| Start frequency | 7.5 GHz |
| Stop frequency | 22.5 GHz |
| Step size | 0.05 GHz |
| Solution frequency | 15 GHz |

---

## Post-Processing

### S-Parameter Plots
1. **S₁₃ and S₂₃ magnitude (dB) vs Frequency** — confirms equal power division
2. **Polar plot of S₁₃ and S₂₃** — shows mirror-image traces for 180° phase confirmation
3. **ang(S₁₃) − ang(S₂₃) vs Frequency** — direct phase difference measurement

### Field Plots
1. **Mag_E on YZ surface cut** — magnitude of E-field showing equal power at both arms
2. **Mag_E on XZ surface cut** — TE₁₀ mode pattern verification (sinusoidal across broad wall)
3. **Vector_E on YZ surface cut** — direction of E-field vectors showing anti-phase relationship

Field plots generated at:
- **Frequency:** 15 GHz
- **Phase:** 60° (chosen to clearly show field directions at both ports simultaneously)

---

## Key Simulation Results Summary

| Quantity | Value |
|----------|-------|
| Simulated cutoff frequency | ~9.49 GHz |
| S₁₃ at 15 GHz | −4.46 dB |
| S₂₃ at 15 GHz | −4.46 dB |
| Phase difference ∠S₁₃ − ∠S₂₃ at 15 GHz | +180.14° |
| Phase difference ∠S₁₃ − ∠S₂₃ at 13 GHz | −179.88° |
| Operating band | 9.5–20 GHz (Ku-band) |

---

## Notes and Observations

- The simulated cutoff frequency matches theory to within numerical error.
- S₁₃ and S₂₃ traces completely overlap in the passband, confirming geometric symmetry of the model.
- The −4.46 dB value (vs ideal −3 dB) is expected for an unmatched E-plane Tee; adding matching elements (inductive posts, diaphragms) would recover the ideal response.
- The standing wave pattern in the XZ field plot is consistent with partial reflection at the unmatched junction (Port 3).
