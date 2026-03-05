**Optical Aberrations Summary Table：**
| Aberration                            | Type          | Physical Cause                                         | Field Location | Wavefront Aberration Term        | Typical Image Effect                                | Key System Factors                         | Common Correction                            |
| ------------------------------------- | ------------- | ------------------------------------------------------ | -------------- | -------------------------------- | --------------------------------------------------- | ------------------------------------------ | -------------------------------------------- |
| **Spherical Aberration**              | Monochromatic | Marginal rays focus differently than paraxial rays     | On-axis        | W040 * rho^4                     | Circular blur spot                                  | aperture size, surface curvature, f-number | aspheric surface, aperture stop optimization |
| **Coma**                              | Monochromatic | Different pupil zones produce different magnifications | Off-axis       | W131 * rho^3 * h * cos(theta)    | Comet-shaped blur                                   | field angle, aperture size, stop location  | symmetric design, stop placement             |
| **Astigmatism**                       | Monochromatic | Tangential and sagittal rays focus at different planes | Off-axis       | W222 * rho^2 * h^2 * cos(2theta) | Line or elliptical blur                             | field height, lens symmetry                | balanced lens groups                         |
| **Field Curvature**                   | Monochromatic | Petzval sum causes curved image surface                | Off-axis       | W220 * rho^2 * h^2               | Image best focus lies on curved surface             | optical power distribution                 | field flattener                              |
| **Distortion**                        | Monochromatic | Magnification varies across field                      | Off-axis       | W311 * rho * h^3 * cos(theta)    | Barrel or pincushion distortion                     | field angle, principal ray geometry        | lens group redistribution                    |
| **Longitudinal Chromatic Aberration** | Chromatic     | Refractive index varies with wavelength                | On-axis        | focal length = f(lambda)         | Different colors focus at different axial locations | glass dispersion, wavelength band          | achromatic doublet                           |
| **Lateral Chromatic Aberration**      | Chromatic     | Magnification varies with wavelength                   | Off-axis       | magnification = m(lambda)        | Color fringing at edges                             | field height, glass dispersion             | apochromatic design                          |





####
**像差与光学参数关系**
| 参数                             | 主要影响像差                      |
| ------------------------------ | --------------------------- |
| **Aperture / f-number**        | spherical aberration、coma   |
| **Field of View**              | coma、astigmatism、distortion |
| **Optical power distribution** | field curvature             |
| **Stop location**              | coma、distortion             |
| **Wavelength band**            | chromatic aberrations       |
| **Principal plane location**   | distortion、field curvature  |
| **Lens symmetry**              | coma、distortion             |


####
**主点-** The cardinal points of an optical system include two focal points, two principal points, and two nodal points. These six points describe the first-order imaging properties of a system.
#####
**主平面-** Principal planes are reference planes in an optical system where refraction is assumed to occur in the equivalent thin-lens model.
When the refractive indices of object space and image space are the same, the nodal points coincide with the principal points.
Principal plane（主平面）的位置取决于系统的“光焦度分布（optical power distribution）
- 正光焦度在前 → principal plane 往后移
- 负光焦度在前 → principal plane 往前移



####
**设计实例-**
Telephoto lens 的 principal plane 在镜头外面，复杂镜组改变了H' location。导致 EFL >> physical length
In a telephoto design, a positive front group is combined with a negative rear group.
The negative rear group effectively increases the focal length while shortening the physical length of the lens.
As a result, the principal plane shifts forward and can even lie in front of the lens system.



Wide-angle lenses often use a retrofocus design with a negative front group and a positive rear group.
The negative front group expands the field of view and increases the back focal distance.
This optical power distribution shifts the principal plane into the interior of the system.

| System Type       | Structure                             | Field of View | Principal Plane Location | BFL        | Typical Use           |
| ----------------- | ------------------------------------- | ------------- | ------------------------ | ---------- | --------------------- |
| Normal Lens       | symmetric positive lenses             | moderate      | near center of lens      | small      | standard cameras      |
| Wide-Angle Lens   | strong negative front + positive rear | large         | inside system            | large      | landscape, smartphone |
| Retrofocus Lens   | negative front group                  | very large    | inside system            | very large | DSLR wide-angle       |
| Telephoto Lens    | positive front + negative rear        | narrow        | in front of lens         | short      | long focal length     |
| Inverse Telephoto | another name for retrofocus           | large         | inside                   | large      | wide-angle SLR        |
