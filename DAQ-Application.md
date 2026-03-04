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

# Wavefront-Based Error Diagnosis + Error Model Rebuild (DAQ / WFS / Zernike)

Goal: Use **measured wavefront shape** (WFE map / Zernike) + **DAQ sensors** (T, accel, strain) to:
1) infer **which physical part** caused the error, and  
2) rebuild a **parametric error model** for simulation / STOP / tolerance.

---

## 1) End-to-End Architecture (Measurement → Diagnosis → Model Update)

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



'''
