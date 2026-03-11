Sensor Input
  ├─ LWIR wide-FOV stream
  ├─ MWIR narrow-FOV stream
  ├─ Optional visible / laser / IMU
  ↓
Radiometric & Image Correction
  ├─ NUC / gain-offset correction
  ├─ bad-pixel correction
  ├─ denoise
  ├─ local contrast enhancement
  └─ multi-band registration
  ↓
Target Detection
  ├─ full-frame thermal candidate detection
  ├─ clutter suppression
  └─ candidate ROI extraction
  ↓
Tracking
  ├─ track initialization
  ├─ KCF / Kalman / DeepSORT / JPDA
  ├─ track maintenance
  └─ re-detection on target loss
  ↓
Discrimination / Classification
  ├─ spectral features
  ├─ spatial morphology features
  ├─ temporal motion features
  ├─ context features
  └─ rule-based / ML / deep fusion classifier
  ↓
Decision Output
  ├─ target type
  ├─ confidence
  ├─ trajectory
  ├─ threat level
  └─ handoff to operator / fire-control / higher-level fusion
