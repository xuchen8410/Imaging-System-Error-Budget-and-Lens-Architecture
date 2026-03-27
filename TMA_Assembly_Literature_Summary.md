
 # TMA Mirror Curvature vs First-Order Optics (Concise)

## Sign Convention
- Concave mirror: `R > 0`
- Convex mirror: `R < 0`

---

## 1. Mirror Focal Length
- `f_i = R_i / 2`
- Primary (`R1`) sets system speed (F/#):
  - Smaller `R1` → faster system → higher aberration sensitivity

---

## 2. Secondary Magnification (Key Coupling)
- `m2 = - f1 / f2 = - R1 / R2`

**Implications:**
- Controls pupil location
- Controls beam compression/expansion
- Larger |m2| → smaller internal beam → smaller M3 but harder aberration control

---

## 3. Effective Focal Length (System Level)
- `F ≈ (f1 * f3) / |m2|`

**Coupling:**
- Faster primary (`R1 ↓`) → must increase |m2| or adjust `R3`
- System EFL is NOT independent → tightly coupled to all three mirrors

---

## 4. Pupil Imaging (Critical for IR systems)
- M1 + M2 ≈ Mersenne beam compressor
- Secondary creates **real pupil** between M2–M3

**Design impact:**
- Enables cold stop placement (IR critical)
- Pupil size ∝ `|m2|`

---

## 5. Petzval / Field Curvature Balance
- Mirror contribution:
  - `Ci = 2 / Ri`

- Total: C_total = 2/R1 + 2/R2 + 2/R3
- Flat field condition: 2/R1 - 2/|R2| + 2/R3 ≈ 0

**Engineering insight:**
- If `R1 ↓` (faster primary):
→ Must decrease |R2| or adjust `R3`
→ Otherwise field curvature explodes

---

## 6. Aberration Distribution (Physical Roles)

### M1 (Primary)
- Sets convergence
- Introduces strong **positive spherical aberration**

### M2 (Convex, negative power)
- Introduces **negative spherical aberration**
- Controls:
- pupil position
- coma balance
- beam diameter

### M3 (Tertiary)
- Residual correction:
- astigmatism
- field curvature
- distortion

---

## 7. Beam Behavior (Why mirrors grow in off-axis systems)
- M2 compresses beam → smaller footprint
- M3 expands beam → larger footprint
- Off-axis:
- footprint is decentered → mirror must cover:
  ```
  clear aperture ≈ marginal ray + chief ray shift + margin
  ```

---

## 8. Key Design Coupling Summary

| Parameter Change | System Impact |
|----------------|-------------|
| `R1 ↓` (faster) | ↑ aberrations, ↑ sensitivity |
| `ABS R2 ↓` (stronger secondary) | ↑ pupil shift, ↑ aberration correction |
| `ABS m2 ↑` | ↓ beam size at M3, ↑ alignment sensitivity |
| `R3 adjust` | field flattening + distortion correction |

---

## 9. Practical Design Workflow

1. Set system requirements:
 - EFL, F/#, FOV
2. Choose `R1` → defines speed
3. Select `m2` → sets pupil & packaging
4. Solve `R2 = -R1 / m2`
5. Adjust `R3` to:
 - flatten field
 - balance residual aberrations
6. Optimize in Zemax/Code V:
 - variables: `R1, R2, R3, spacing`
 - monitor:
   - WFE
   - beam walk
   - vignetting

---

## Core Insight (Design Review Level)

> TMA is NOT 3 independent mirrors —  
> it is a **coupled system where R1 sets the problem, R2 redistributes it, and R3 cleans it.**


- For TMA alignment, nodal aberration theory and practical alignment literature show that third-order misalignment behavior is dominated (over the used field) by a field-constant coma pattern and a field-linear astigmatism pattern, with a “benign misalignment” subspace that can mask misalignment if you only monitor a limited set of aberration patterns。
