**Optical Aberrations Summary Table：**
| Aberration                            | 类型 | 主要产生原因                      | 发生位置 | 波像差主项              | 典型像斑特征              | 影响因素                            | 常见校正方法                             |
| ------------------------------------- | -- | --------------------------- | ---- | ------------------ | ------------------- | ----------------------------------- | ---------------------------------- |
| **Spherical Aberration**              | 单色 | 边缘光线与近轴光线焦点不同               | 轴上   | (W_{040}\rho^4)    | 圆形模糊斑               | aperture size、surface curvature、f/# | aspheric surface、stop optimization |
| **Coma**                              | 单色 | pupil 不同区域放大率不同             | 离轴   | (W_{131}\rho^3h)   | 彗星形尾巴               | field angle、aperture、stop location  | 对称设计、stop shift                    |
| **Astigmatism**                       | 单色 | tangential 与 sagittal 焦点不同  | 离轴   | (W_{222}\rho^2h^2) | 线形 / 椭圆             | field height、system symmetry        | lens group balancing               |
| **Field Curvature**                   | 单色 | Petzval curvature           | 离轴   | (W_{220}\rho^2h^2) | 最佳像面为曲面             | system optical power distribution   | field flattener                    |
| **Distortion**                        | 单色 | 放大率随视场变化                    | 离轴   | (W_{311}\rho h^3)  | barrel / pincushion | field angle、principal ray path      | lens group redistribution          |
| **Longitudinal Chromatic Aberration** | 色差 | 折射率随波长变化                    | 轴上   | (f(\lambda))       | 不同颜色焦点不同            | glass dispersion、wavelength band    | achromatic doublet                 |
| **Lateral Chromatic Aberration**      | 色差 | magnification vs wavelength | 离轴   | (m(\lambda))       | 彩色边缘                | field height、dispersion             | apochromatic design                |

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
####
**设计实例-**
Telephoto lens 的 principal plane 在镜头外面，复杂镜组改变了H' location。导致 EFL >> physical length

