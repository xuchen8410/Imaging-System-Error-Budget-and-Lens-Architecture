A Mersenne beam compressor is a two-mirror afocal system where all geometry scales linearly with compression ratio `M`, trading beam diameter for divergence while preserving optical invariant.
Assume primary f1=200mm;R1=400mm:
| Commercial family | Compressor magnification (M=D_{out}/D_{in}) | Primary focal length (f_1) (mm) | Secondary focal length (f_2) (mm) | Primary ROC (R_1) (mm) | Secondary ROC (R_2) (mm) | Mirror spacing (d) (mm) |
| ----------------- | ------------------------------------------: | ------------------------------: | --------------------------------: | ---------------------: | -----------------------: | ----------------------: |
| 1.5X family       |                                      0.6667 |                           200.0 |                            -133.3 |                  400.0 |                   -266.7 |                    66.7 |
| 2X family         |                                      0.5000 |                           200.0 |                            -100.0 |                  400.0 |                   -200.0 |                   100.0 |
| 3X family         |                                      0.3333 |                           200.0 |                             -66.7 |                  400.0 |                   -133.3 |                   133.3 |
| 4X family         |                                      0.2500 |                           200.0 |                             -50.0 |                  400.0 |                   -100.0 |                   150.0 |
| 5X family         |                                      0.2000 |                           200.0 |                             -40.0 |                  400.0 |                    -80.0 |                   160.0 |
| 8X family         |                                      0.1250 |                           200.0 |                             -25.0 |                  400.0 |                    -50.0 |                   175.0 |
| 10X family        |                                      0.1000 |                           200.0 |                             -20.0 |                  400.0 |                    -40.0 |                   180.0 |

The compression power, and the bending:


### Key Relationships
### 1) Linear Scaling
- Secondary mirror properties scale linearly with `M`:
  - `|f2| ∝ M`
  - `|R2| ∝ M`

- Mirror spacing:
  - `d ∝ (1 - M)`



### 2) Compression Behavior

| Compression strength | M value | Mirror behavior | System length |
|---|---|---|---|
| Weak compression | M → 1 | Strong convex mirror (large |R2|) | Compact (small d) |
| Moderate (typical) | 0.25–0.5 | Balanced | Practical |
| Strong compression | M → 0 | Weak convex mirror (small |R2|) | Long (large d) |


### 3) Physical Interpretation

- Beam transformation:
  - Diameter ↓ by factor `M`
  - Divergence ↑ by factor `1/M`
- Optical invariant conserved:
- D · θ = constant
### 4) Degrees of Freedom
The system has only **two independent variables**:
- f1 → sets physical scale
- M → sets compression ratio
Everything else is deterministically derived.

### 5) Practical Design Insight

- Commercial systems cluster at discrete values:

- Reasons:
  - Clean curvature ratios (`R2 = -M·R1`)
  - Predictable spacing (`d = f1(1-M)`)
  - Manufacturable mirror powers
  - Compact vs performance trade balance
