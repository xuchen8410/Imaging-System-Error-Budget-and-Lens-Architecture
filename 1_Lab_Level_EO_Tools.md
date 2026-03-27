### Tool Sets
| Tool              | DOF              | Function            | Used With                   |
| ----------------- | ---------------- | ------------------- | --------------------------- |
| Tip-tilt mount    | θx, θy           | Beam steering       | Mirrors, lenses             |
| Translation stage | X, Y, Z          | Positioning         | Fiber, detector             |
| Rotation stage    | θz               | Rotate optic        | Polarization optics         |
| Goniometer        | Angular arc      | Precise angle scan  | BSDF / scatter              |
| Kinematic mount   | Fixed repeatable | Fast swap alignment | Mirrors                     |
| Piezo stage       | nm-scale XYZ     | Ultra-fine tuning   | Interferometry              |
| Hexapod           | 6 DOF            | Full alignment      | High-end systems (KLA-type) |


### Core Experimental Workflow

| Step | Action              | Tool Used               | Purpose                        | Key Metric                    |
| ---- | ------------------- | ----------------------- | ------------------------------ | ----------------------------- |
| 1    | Rough placement     | Translation stage (XYZ) | Bring optic into beam path     | Visibility / beam overlap     |
| 2    | Beam steering       | Tip-tilt mount          | Direct beam along optical axis | Beam centering downstream     |
| 3    | Position refinement | Translation stage (XY)  | Center beam on optic           | Symmetry / power              |
| 4    | Focus / spacing     | Z stage                 | Optimize axial distance        | Spot size / coupling          |
| 5    | Fine optimization   | Tip-tilt + XYZ          | Maximize performance           | Power / MTF / fringe contrast |
| 6    | Lock & verify       | All                     | Stability check                | Drift / repeatability         |

(A) Fiber Coupling
| Item                    | Description                                                                                                                                                  |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Goal**                | Maximize optical power into fiber                                                                                                                            |
| **Setup**               | Laser → mirror (tip-tilt) → lens → fiber (XYZ stage)                                                                                                         |
| **Procedure**           | 1. Use **tip-tilt** to aim beam into fiber core<br>2. Use **XY stage** to center fiber<br>3. Use **Z stage** to find best focus<br>4. Iterate tip-tilt + XYZ |
| **Tools**               | Tip-tilt mount, XYZ stage, power meter                                                                                                                       |
| **Optimization signal** | Coupled power (maximize)                                                                                                                                     |
| **Physics**             | Mode overlap integral (Gaussian ↔ fiber mode)                                                                                                                |
| **Key sensitivity**     | Angular error → large coupling loss                                                                                                                          |

(B) Free-Space Beam Alignment

| Item                    | Description                                                                                                                          |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **Goal**                | Align beam along a defined optical axis                                                                                              |
| **Setup**               | Laser → multiple mirrors → target                                                                                                    |
| **Procedure**           | 1. Place irises along path<br>2. Use **tip-tilt** to pass beam through all irises<br>3. Use translation stages for optic positioning |
| **Tools**               | Tip-tilt mounts, irises, posts                                                                                                       |
| **Optimization signal** | Beam passes through apertures                                                                                                        |
| **Physics**             | Ray propagation / angular alignment                                                                                                  |
| **Key sensitivity**     | Small angular error → large lateral drift downstream                                                                                 |

(C) Interferometer Alignment (Zygo / Fizeau / Michelson)

| Item                    | Description                                                                                                                  |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **Goal**                | Achieve high fringe contrast & correct wavefront                                                                             |
| **Setup**               | Reference arm + test arm                                                                                                     |
| **Procedure**           | 1. Use **tip-tilt** to overlap beams<br>2. Use **Z stage** to match path length<br>3. Fine adjust tilt to straighten fringes |
| **Tools**               | Tip-tilt mount, translation stage                                                                                            |
| **Optimization signal** | Fringe contrast / straightness                                                                                               |
| **Physics**             | Wavefront phase matching                                                                                                     |
| **Key sensitivity**     | Tilt → fringe density; Z → OPD                                                                                               |

(D) Imaging System Alignment (Lens + Detector)
| Item                    | Description                                                                                                                |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Goal**                | Achieve best image quality (MTF / focus)                                                                                   |
| **Setup**               | Object → lens → sensor                                                                                                     |
| **Procedure**           | 1. Use **XYZ stage** to position sensor<br>2. Use **tip-tilt** to remove tilt-induced aberrations<br>3. Adjust Z for focus |
| **Tools**               | XYZ stage, tip-tilt mount                                                                                                  |
| **Optimization signal** | MTF / spot size                                                                                                            |
| **Physics**             | Field curvature, defocus, tilt aberration                                                                                  |
| **Key sensitivity**     | Tilt → coma/astigmatism; Z → defocus                                                                                       |



