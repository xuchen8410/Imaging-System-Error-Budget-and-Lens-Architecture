### Overview
A feedback-based ISP tuning framework that evaluates **final output color** and iteratively updates upstream modules (AWB, CCM, CLUT) using perceptual error metrics.
- ISP standardizes: Sensor → Display Color Conversion; Converts sensor-native RGB (device-dependent)→ to standard color spaces: sRGB (most common), Adobe RGB, Display P3. Ensures images look consistent across devices- AWB (Auto White Balance): Estimates scene illumination and applies per-channel gains (R/G/B) to neutralize color cast, aligning white/gray to a reference neutral.
- CCM (Color Correction Matrix): A 3×3 linear transform mapping sensor RGB to a target color space (e.g., standard RGB), correcting spectral mismatch and global color bias.
- CLUT (Color Lookup Table): A nonlinear color mapping (typically 3D LUT) that refines color rendering—adjusting hue, saturation, and tone beyond linear correction
### Problem
Conventional ISP tuning is **feedforward**:
- Operates in RAW / early stages
- Ignores downstream transformations
- Fails under varying illumination
- Suffers from sensor–human perception mismatch (metamerism)

### Key Idea
> Perform color evaluation at ISP output and **feed error back upstream**.
### Pipeline
```
RAW → ISP (AWB → CCM → CLUT → Tone) → Output
↓
Post-ISP Statistics
↓
Error Computation
↓
Parameter Update (AWB/CCM/CLUT)
↓
Feedback
```

### Core Modules

### 1. Post-ISP Statistics
- Operates on final image
- Converts to perceptual space (CIELAB / LCH)
- Extracts: L*, C*, H*

### 2. Error Computation
- Compare measured vs target color
- Metrics: ΔL*, ΔC*, ΔH* (or equivalent distance)

### 3. Parameter Update
- **AWB** → channel gains (R/G/B)
- **CCM** → linear transform matrix
- **CLUT** → nonlinear color mapping


### Algorithm

1. Run ISP → output image  
2. Compute perceptual color statistics  
3. Evaluate error vs target  
4. Update AWB / CCM / CLUT  
5. Apply to next frame (iterate)


### Design Properties

- Closed-loop control (frame-to-frame)
- Output-driven (perceptual accuracy)
- Cross-module consistent
- Supports ROI-based statistics


### Color Space

- Use **CIELAB / LCH**
  - Device-independent
  - Perceptually uniform
  - Enables stable hue/chroma/lightness correction

### Implementation Notes

- Post-ISP stats block required (HW or DSP)
- Feedback applied with delay (next frame)
- Needs stability control:
  - gain limits
  - smoothing
  - convergence constraints

### Contribution

A **post-ISP, perceptual, closed-loop ISP optimization** method that replaces static tuning with adaptive feedback-driven correction.


#### Reference： 
- Closed-Loop Color Refinement in Camera ISP via Post-ISP Color Feedback, Author: Huanzhao Zeng (Google), link: https://library.imaging.org/admin/apis/public/api/ist/website/downloadArticle/ei/38/10/HVEI-213?utm_source=chatgpt.com 
