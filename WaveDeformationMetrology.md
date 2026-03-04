
## Waves Theory  VS. Particles Theory


```
Wavefront error
        ↓
Slope change
        ↓
Focus intensity shift
        ↓
Knife-edge blocking
        ↓
Brightness pattern
```
## Knife edge test
- Wavefront error → slope variation → focal intensity redistribution → partial blocking by knife → brightness contrast
- Knife-edge measures wavefront slope, not phase directly.

- 波前误差 → 波前斜率变化 → 焦面能量重新分布 → 刀口遮挡 → 亮度对比变化。核心本质： 刀口测试测量的是 波前一阶导数（斜率），不是相位本身。

## 结果
```
| Method         | Measures  |      Accuracy        |
| -------------- | --------- | ----------- | -----  |
| Knife-edge     | Slope     | Qualitative | 斜率定性|
| Shack-Hartmann | Slope map | Medium      | 斜率定量|
| Fizeau         | Phase     | λ/100       | 高精度相位|
 ```
## 应用场景
- Optical Alignment 光学对准
- Telescope alignment
- Seeker boresight tuning
- Focus optimization
- Mirror Polishing 镜面抛光，实时观察表面变化。
- Stray Light Diagnosis 杂散光诊断 -Pupil clipping； Ghost focus； Asymmetric scattering
- STOP Validation 用于验证：Thermal deformation；Mount stress effects; Wavefront tilt due to structure

## Example
- 1. 检测抛光后的凹面镜形状 pinhole source → mirror → focus → knife edge → camera/eye。 The light source is placed at the mirror's center of curvature.  
The knife edge is positioned at the focal point.Ideal mirror → pupil darkens uniformly； Surface error → uneven shadow pattern。 
**Engineering Use** Used during mirror polishing to quickly identify: center high； edge high； zonal errors ---对斜率误差非常敏感， 适合镜面抛光与光学对准

## 数据分析原理
Knife-edge measurements typically follow an error-function model.
- Reference Optica published model: 
- Link: https://opg.optica.org/viewmedia.cfm?r=1&rwjcode=ao&uri=ao-64-8-1912&html=true
- https://github.com/derekburrell/camera-evaluation 
- Gaussian beam I(x) = I0 exp(-2x² / w²); 
- Knife-edge integration P(x) = P0/2 * (1 + erf(√2 x / w)),
- Meaning ：The measured power curve follows an **error function profile**.
This allows extraction of: beam waistk beam position, beam width.
