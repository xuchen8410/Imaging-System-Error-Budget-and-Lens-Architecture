```text
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

```

## Thermal Imaging Sensors Comparison

| Sensor | Size | Weight | Resolution | Frame Rate | Radiometric | Power | Platform | Cost | Year |
|------|------|------|------|------|------|------|------|------|------|
| Thermal-Eye 2000B | 282×279×290 mm | 4.54 kg | 320×240 | 12.5 Hz | No | 28 W | UGV | n/a | early |
| Gobi-640-GigE | 49×49×79 mm | 263 g | 640×480 | 50 Hz | No | 4.5 W | UGV | n/a | 2008 |
| Miricle 307K | 45×52×48 mm | 95 g | 640×480 | 15 Hz | No | 3.3 W | UAV | n/a | 2006 |
| FLIR Tau2 | 44.5×44.5×30 mm | <70 g | 640×480 | 60 Hz | Yes | 1 W | UAV | $6500 | 2015 |
| FLIR A65 | 120×125×280 mm | 200 g | 640×512 | 30 Hz | Yes | 3.5 W | UAV | $7895 | 2016 |

---

### Reference

1. https://pmc.ncbi.nlm.nih.gov/articles/PMC8540138/
