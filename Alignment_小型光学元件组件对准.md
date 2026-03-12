
# Optical Axis Alignment Workflow 

A typical alignment workflow is to first establish a **mechanical reference frame**, then define a **reference optical axis**, perform **coarse alignment** of lenses, mirrors, and detectors, and finally use **image quality or wavefront measurements** for precision optimization.

## 1. Establish Mechanical Reference
Before optical alignment, define the bench coordinate system and nominal component locations using mechanical datums or metrology tools such as a laser tracker, CMM, or alignment targets. This ensures the hardware is placed relative to a known reference frame.

## 2. Define the Optical Reference Axis
Use a **high-quality collimated laser** to create the reference beam. Common choices are:
- **He-Ne laser**: very stable, low divergence, excellent beam quality
- **Single-mode fiber-coupled laser + collimator**: compact, clean spatial mode
- **Alignment laser module**: convenient for coarse alignment, but usually lower beam quality

A common setup is:
Laser → Iris 1 → Iris 2 → Reference Optical Axis
- 1  HeNe / fiber laser 建立 reference beam
- 2  两个 iris 定义 reference axis
- 3  粗调光学元件
- 4  用 retro-reflection 校正 mirror
- 5  用 point image 优化成像质量

```text
Mechanical reference
      ↓
Collimated laser reference axis
      ↓
Iris-based coarse axis definition
      ↓
Lens / mirror coarse alignment
      ↓
Retro-reflection check
      ↓
Autocollimator tilt correction
      ↓
Point-source image optimization
      ↓
Interferometric fine alignment
```
