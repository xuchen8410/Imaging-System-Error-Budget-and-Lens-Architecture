### Overview
A feedback-based ISP tuning framework that evaluates **final output color** and iteratively updates upstream modules (AWB, CCM, CLUT) using perceptual error metrics.
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
