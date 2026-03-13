### Why MEMS Scanning Is Used in In-Vivo Cancer Detection / Laser Ablation Optical Probes
In medical optical probes for **in-vivo cancer detection, nonlinear microscopy, and laser ablation guidance** (e.g., CARS, multiphoton, confocal, OCT), a **MEMS scanning mirror or scanning fiber** is commonly integrated inside the probe instead of using a simple wide-field optical architecture.
The reasons are driven by **physics (signal formation), probe geometry constraints, and detector coupling requirements**.
#### 1. High Local Intensity Requirement (Nonlinear / Laser-Based Imaging)
Many advanced cancer-detection modalities rely on **nonlinear or confocal optical processes**, including:
- Coherent Anti-Stokes Raman Scattering (CARS)
- Two-photon fluorescence
- Confocal fluorescence
- Optical coherence tomography (OCT)
These techniques require:
• tight beam focusing  
• high peak intensity  
• point illumination  
Wide-field illumination spreads optical power over a large area, drastically reducing nonlinear signal generation.
Therefore systems use:
Point-scanning laser illumination → raster scanning → image reconstruction.
Endomicroscopy systems typically build the image **point-by-point via a scanning laser spot**, which provides optical sectioning and suppresses out-of-focus background. 
#### 2. MEMS Enables Miniaturization of the Probe
A major requirement for in-vivo probes is **extreme miniaturization**.
Typical targets:
probe diameter: 2–5 mm  
catheter probes: ~1–3 mm  
MEMS mirrors are widely used because they provide:
- mm-scale mirrors
- ±20–30° scan angles
- low power consumption
- high scan frequency
- microfabricated integration
MEMS scanning technology has become a key enabler for **miniaturized fiber-optic endoscopy systems** that can provide cellular-level imaging inside the body. 
Without MEMS, the system would require bulky galvo scanners which cannot fit inside endoscopic probes.
#### 3. Optical Sectioning and Signal-to-Noise Ratio
Wide-field imaging in tissue suffers from:
- strong scattering
- out-of-focus fluorescence
- background signals
Scanning microscopy (confocal or nonlinear) provides **optical sectioning**:
Advantages:
• rejects out-of-focus light  
• improves contrast in scattering tissue  
• allows cellular-resolution imaging  
This is essential for **early cancer detection**, where lesions may be only a few microns in size. 
#### 4. Fiber Delivery Constraints
Most in-vivo probes deliver laser light through **single-mode optical fibers**.
Typical architecture:
laser source  
→ fiber delivery  
→ collimation optics  
→ MEMS scanner  
→ focusing optics  
→ tissue
Reasons fiber delivery is preferred:
• flexible routing through the body  
• minimal probe diameter  
• stable beam quality  
Scanning the beam **after the fiber** allows a single fiber to generate a 2D image.
Scanning fiber endoscopes can achieve high-resolution imaging while maintaining ultra-thin probe diameters (<1 mm). 
#### 5. Field-of-View vs Resolution Tradeoff
Wide-field probes using coherent fiber bundles suffer from:
- limited pixel count (fiber core count)
- poor resolution when probe diameter shrinks
Scanning systems avoid this limitation because the image resolution depends on:
optical NA + scan sampling
rather than fiber bundle pixel count.
#### 6. Chief Ray Angle Constraints at the Detector
For imaging probes using photodiodes, PMTs, or camera sensors, **chief ray angle (CRA)** must remain within the detector acceptance angle.
Reasons:
• photodiodes have angular sensitivity limits  
• large CRA causes reduced quantum efficiency  
• microlens arrays on sensors assume near-normal incidence  
MEMS scanning designs typically keep the **detection path near coaxial (epi-detection)** so that:
signal light returns through the same objective and fiber path.
This ensures:
• controlled CRA at detector  
• high coupling efficiency  
• better SNR.
#### 7. Integration with Laser Ablation
In cancer surgery probes, the same optical path may support:
diagnosis → therapy.
Example workflow:
scan tissue → identify malignant region → laser ablation.
MEMS scanning enables:
• precise beam steering  
• micron-scale targeting  
• rapid switching between imaging and ablation modes.
# 8. Typical MEMS Probe Optical Architecture
laser source
    ↓
single-mode delivery fiber
    ↓
collimator
    ↓
MEMS scanning mirror
    ↓
scan lens / objective
    ↓
focused beam on tissue
    ↓
backscattered signal
    ↓
epi collection optics
    ↓
fiber or detector (PMT / photodiode / spectrometer)

MEMS scanners are used in in-vivo optical probes because they enable **high-intensity point-scanning microscopy inside millimeter-scale probes**, allowing nonlinear imaging, high-contrast optical sectioning, and fiber-delivered laser scanning while maintaining acceptable detector coupling and chief-ray angles.
