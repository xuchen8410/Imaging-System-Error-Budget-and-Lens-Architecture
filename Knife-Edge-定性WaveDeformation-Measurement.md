
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

## 总结
- 在望远镜主镜加工与抛光过程中，Knife-edge（Foucault）测试常用于检测凹面反射镜的面形质量，工程上通常将点光源放置在镜面的曲率中心，在焦点位置放置刀口并缓慢横向扫描，通过观察镜面不同区域变暗的先后顺序来判断中心高、边缘高或局部区域误差，从而指导下一步抛光修正。
- 在光学实验室的标准光学平台上，Knife-edge 测试通常由激光或 LED 点光源、针孔空间滤波器、被测光学系统、安装在微调平移台上的刀口以及相机或功率计组成，通过移动刀口并记录透射光强随位置变化的曲线，实现对焦点能量分布和系统对准状态的快速评估。
- 在激光工程中，Knife-edge 扫描被广泛用于测量激光光束的束腰和光斑尺寸，工程师通过横向移动刀口并测量透射功率，将实验数据拟合为误差函数（error function）曲线，从而提取高斯光束半径、中心位置和发散特性，该方法因实现简单且结果可靠而被广泛采用。
- 在光学系统装调和对准过程中，Knife-edge 测试可作为快速诊断工具，用于识别系统倾斜、彗差或像散等问题，其对波前斜率误差高度敏感，能够在干涉仪测试之前帮助工程师迅速定位对准或装配误差。
- 在镜头或成像系统分析中，Knife-edge 方法还可用于测量系统入瞳或有效孔径尺寸，通过在瞳面或等效焦面位置进行刀口扫描并记录光强变化，工程上可以定量估算系统的几何瞳参数并与设计模型进行对比验证。
- 由于 Knife-edge 测试装置简单、成本低且响应直观，实际工程中通常由工程师自行编写 Python、MATLAB 或 LabVIEW 程序完成数据采集和误差函数拟合分析，而不是依赖专用商业软件，这使其成为光学工程和光学计量中非常实用的基础测试方法。
