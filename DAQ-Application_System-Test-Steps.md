DAQ = 把各种传感器信号（光、电、温度、振动等）实时采集 → 变成数字数据 → 分析系统性能 --- Data acquisition is the process of collecting physical sensor signals, converting them into digital data, and recording them for analysis.
光学系统里，DAQ就是 “所有测试数据的入口”。
## 1. Main Purpose in Imaging Systems
DAQ systems are used for:
- Optical system performance testing
- Environmental testing (thermal / vibration)
- Flight test telemetry
- Hardware-in-the-loop validation
  #####
| 用途      | 说明           |
| ------- | ------------ |
| 系统测试    | 测试光学系统是否达到指标 |
| 环境测试    | 振动、温度对光学影响   |
| 飞行/地面遥测 | 记录系统运行状态     |

## 2. Typical Signals Collected

In imaging EO optical systems, DAQ collects synchronized measurements from multiple sensors.

| Sensor Type | Measurement |
|-------------|-------------|
| Photodiode | Optical power |
| CCD / IR detector | Image signal |
| Thermocouple | Temperature |
| Strain gauge | Structural deformation |
| Accelerometer | Vibration |
| Voltage monitor | Power stability |

DAQ采集的信号

| 传感器               | 采的数据  |
| ----------------- | ----- |
| Photodiode        | 光功率   |
| CCD / IR detector | 图像信号  |
| Thermocouple      | 温度    |
| Strain gauge      | 结构形变  |
| Accelerometer     | 振动    |
| Voltage monitor   | 电源稳定性 |


## 3. Wavefront-Based Error Diagnosis in Optical Systems  
### DAQ + Wavefront Analysis + Error Modeling Workflow
This document summarizes how measured **wavefront distortions** can be used to diagnose the **physical source of optical errors** in aerospace optical systems.  
The workflow integrates:
- Data Acquisition (DAQ)
- Wavefront sensing
- Zernike decomposition
- Error source identification
- Model reconstruction and validation
  
##  4.System Measurement Architecture
 - Wavefront-Based Error Diagnosis + Error Model Rebuild (DAQ / WFS / Zernike)
 - Goal: Use **measured wavefront shape** (WFE map / Zernike) + **DAQ sensors** (T, accel, strain) to:    
    1) infer **which physical part** caused the error, and  
    2) rebuild a **parametric error model** for simulation / STOP / tolerance.
####  End-to-End Architecture (Measurement → Diagnosis → Model Update)

```text
[Optical Hardware]
 (Components mounts, structure, detector)
            |
            v
[Disturbances Applied / Occurring]
 (thermal gradient, vibration, gravity vector, alignment shift)
            |
            v
[Measurements]
  - Wavefront Sensor / Phase Retrieval  -> WFE(x,y,t)
  - DAQ sensors (sync time-stamped)
      * Temperature T_i(t)
      * Accelerometer a_i(t)
      * Strain g_i(t)
      * Power/voltage monitors
            |
            v
[Wavefront Feature Extraction]
  - Remove piston
  - Zernike fit: Z_k(t)
  - Spatial features: RMS, PV, PSD bands, symmetry metrics
            |
            v
[Root-Cause Inference]
  - "Mode → Mechanism" mapping
  - Multi-sensor correlation (Z_k vs T/a/g)
  - Hypothesis ranking + parameter estimation
            |
            v
[Error Model Rebuild]
  - Build parametric error state vector p
    (tilts, decenters, spacing, figure modes, thermal modes)
  - Forward model: WFE_pred(p)
  - Fit p via least squares / Bayesian
            |
            v
[Validation Loop]
  - Compare WFE_pred vs WFE_meas
  - Update priors / regularization / coupling
  - Freeze into STOP / Monte-Carlo tolerance model

```

## 5.误差分析一些example
Wavefront is diagnostic - because different physical errors produce distinct symmetry + Zernike signatures.
 ### 5.1 Rigid-body misalignment (alignment / boresight / LOS)
Signature:
- Dominant Tilt (Z2/Z3)  -> LOS shift
- Coma (Z7/Z8)           -> decenter/tilt of powered optic
- Low high-frequency content (mostly low-order modes)
Likely sources:
- Mirror mount shift / fasteners slip
- Kinematic seat motion
- Mechanism backlash / actuator offset
### 5.2 Spacing / focus (axial separation changes)
Signature:
- Defocus (Z4) dominant
- Often correlated with uniform temperature or CTE-driven expansion
Likely sources:
- Barrel / bench expansion
- Secondary spacing change
- Focus mechanism error
### 5.3 Mount stress / structural bending (quasi-static)
Signature:
- Astigmatism (Z5/Z6) dominant (2-lobed)
- Sometimes plus coma depending on constraint geometry
- Strong correlation with strain gauges or gravity vector
Likely sources:
- Over-constraint in mounts
- Gravity sag in one axis
- Thermal gradient across structure
### 5.4 Surface figure deformation (mirror/lens figure)
Signature:
- Mid/high-order Zernikes elevated
- Spatial WFE map shows localized features
- PSD shows more mid/high-frequency energy
Likely sources:
- Thermoelastic figure change
- Print-through from supports
- Polishing/figure residuals (static)
### 5.5 Vibration / jitter (dynamic)
Signature:
- Time-domain: WFE modes oscillate at specific frequencies
- Tilt terms may spike with accelerometer peaks
- If imaging: blur / jitter increases, MTF drops

Likely sources:
- Reaction wheels / cryocooler
- Fan/pump harmonics
- Structural resonance
3) Diagnosis Workflow (From WFE to “Which Part”)
Step 1: Preprocess
- Align pupil / register WFE maps
- Remove piston; optionally remove mean tilt if needed
Step 2: Decompose
- Fit Zernike: Z_k(t)
- Compute: RMS(t), PV(t), PSD(f), symmetry metrics
Step 3: Classify signature
- Low-order dominated? -> alignment / spacing / sag
- Astig-heavy?         -> mount stress / bench bend
- Mid/high-order heavy?-> surface figure / print-through
- Strong time tones?   -> vibration source
Step 4: Correlate with DAQ
- Corr(Z_k, T_i), Corr(Z_k, a_i), Corr(Z_k, g_i)
- Look for time lag (thermal) vs instantaneous (vibration)
Step 5: Hypothesis ranking
- Choose top N causes
- Convert to param vector p for model rebuild

## 6. Error Model Rebuild (Parametric + Fit)
Define a compact error state vector (example):
p = [
  θx, θy,            # rigid-body tilt
  dx, dy, dz,        # decenter / spacing
  A_ast0, A_ast45,   # astig components (mount/sag)
  A_comaX, A_comaY,  # coma components (decenter/tilt)
  {A_fig_m}          # selected surface/thermal modes
]

Forward model:

WFE_pred(x,y,t) = F(p, x, y)          # optical forward model
Z_pred_k(t)     = G_k(p)              # if fitting in Zernike space

Fit / inference:

p* = argmin_p  || Z_meas - Z_pred(p) ||^2  +  λ || L p ||^2
(or Bayesian: p ~ N(p0, Σ0), update with likelihood)

Validation:

Compare:
- Zernike residuals: Z_meas - Z_pred
- Spatial residual map: WFE_meas - WFE_pred
- Frequency residuals (if dynamic)
5) “What Signal Might Be Caused By What” (DAQ Link Table)
Observation (Wavefront/Perf)	Most sensitive DAQ channel	Typical cause
Tilt spikes / LOS jitter	Accelerometers	vibration / resonance
Defocus drift	Temperature (uniform)	CTE spacing change
Astig grows with gravity angle	Strain + gravity vector	sag / over-constraint
Coma increases after handling	none (event-based)	decenter/tilt shift
Mid/high-order grows with thermal gradient	multi-point temperature	thermoelastic figure
Random spikes (non-physical)	voltage/ground	EMI / grounding
6) Minimal Test Steps (Paste-Ready)
1) Baseline
   - Record WFE(x,y,t) + DAQ sensors at steady state
2) Thermal Step
   - Apply controlled ΔT (uniform + gradient)
   - Record WFE + T_i(t) to map thermal sensitivities
3) Vibration Sweep
   - Inject sine / random vibration (or measure operational)
   - Record WFE + a_i(t) to find jitter coupling
4) Gravity / Orientation
   - Rotate / change elevation (if possible)
   - Record WFE + strain to identify sag modes
5) Alignment Perturbation
   - Known small tilt/decenter (if allowed)
   - Confirm signature library (coma/tilt mapping)
6) Rebuild + Validate Model
   - Fit p using the collected dataset
   - Predict WFE under new condition and verify
##### 通常的判断思路是先看测得的波前形状并做 Zernike 分解，如果主要是 Tilt（Z2/Z3）像一个斜坡，一般先怀疑光轴或镜子倾斜，再看振动或指向数据，如果 tilt 随振动变化说明是机械抖动，如果稳定不变多半是装调偏差；如果主要是 Defocus（Z4）呈圆对称弯曲，通常意味着光学间距变化，再检查温度传感器，如果 defocus 随温度线性变化基本可以确定是结构热膨胀导致焦距漂移；如果主要是 Astigmatism（Z5/Z6）呈两瓣形状，通常与结构应力或重力挠曲有关，可以改变系统姿态或看应变计，如果 astig 随重力方向变化就是结构弯曲；如果出现明显 Coma（Z7/Z8）像彗星尾巴，一般说明光学元件偏心或倾斜，再判断它是否随温度或振动变化来区分是装调误差还是热结构变形；如果波前中出现大量高阶 Zernike 或局部起伏，则更可能是镜面或透镜的表面形变，再结合温度梯度或结构传感器判断是否为热弹性变形，总体来说就是先通过波前模式判断误差类型，再结合 DAQ 的温度、振动和应变数据做相关分析，逐步缩小范围并最终确定具体的物理误差来源。
