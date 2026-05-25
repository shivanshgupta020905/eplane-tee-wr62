# S-Parameter Results

## Key Values at Operating Frequency (15 GHz)

| Parameter | Value |
|-----------|-------|
| S₁₃ (magnitude) | −4.46 dB |
| S₂₃ (magnitude) | −4.46 dB |
| ∠S₁₃ | ~+90° |
| ∠S₂₃ | ~−90° |
| ∠S₁₃ − ∠S₂₃ | **+180.14°** |

## Phase Difference at Multiple Frequencies

| Frequency (GHz) | ∠S₁₃ − ∠S₂₃ |
|------------------|--------------|
| 13 GHz | −179.88° |
| 15 GHz | +180.14° |

> Phase difference remains ≈ 180° across the entire Ku-band, confirming broadband phase opposition.

## Power Division Comparison

| Metric | Ideal (Lossless, Matched) | Simulated (Unmatched) |
|--------|--------------------------|----------------------|
| S₁₃ | −3.00 dB | −4.46 dB |
| S₂₃ | −3.00 dB | −4.46 dB |
| Phase difference | 180.00° | ~180° |
| Excess loss | 0 dB | ~1.46 dB |

Excess loss source: Impedance mismatch at the T-junction (unmatched E-plane Tee).

## Figure Reference

| Figure | Description |
|--------|-------------|
| Fig. 2 | S₁₃ and S₂₃ magnitude vs frequency; markers at fc and 15 GHz |
| Fig. 3 | Polar plot of S₁₃ and S₂₃ — mirror images confirming 180° opposition |
| Fig. 4 | Rectangular plot of ∠S₁₃ − ∠S₂₃ = ±180° across band |
| Fig. 5 | Mag_E on YZ plane — equal amplitude at both ports |
| Fig. 6 | Mag_E on XZ plane — TE₁₀ mode standing wave pattern |
| Fig. 7 | Vector_E on YZ plane — opposite-direction arrows at Port 1 & Port 2 |
