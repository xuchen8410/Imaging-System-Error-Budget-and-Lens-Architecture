### Imaging System Error budget
An optical imaging system “error budget” is most useful when it follows the physics chain wavefront → PSF → OTF/MTF → sampling (Nyquist) → detector/pixel coupling → SNR/task performance, and when each stage has a measurable metric and a clear allocation knob (e.g., f/#, pupil size, defocus, jitter, pixel pitch).

For common camera-lens architectures, principal planes and pupils are the “hidden geometry” that explains why the same focal length can package very differently. 
* A telephoto objective is explicitly characterized by system focal length longer than overall system length, enabled by placing net positive power up front and net negative power toward the rear;
* a retrofocus (inverse-telephoto) objective is the “mirror-clearance” inverse: net negative power in front followed by net positive power, producing a back focal distance larger than the focal length. 

For incoherent imaging, OTF(fx, fy) = FT{PSF(x, y)} and MTF = abs(OTF). 
When subsystems are approximately linear shift-invariant, MTF_total ≈ Π MTF_i (lens × detector × motion, etc.).

## Optical Imaging System Error Budget Table

| Budget Item | What it Means | Primary Metrics | Plain ASCII Equations / Checks | Typical Design Knobs | Where it Shows Up |
|--------------|--------------|----------------|--------------------------------|----------------------|------------------|
| **Wavefront Error (WFE)** | Phase / OPD departure from ideal wavefront at exit pupil. Direct driver of diffraction performance. | WFE_rms, OPD_PV, Strehl Ratio (S) | Strehl ≈ exp(-(2π·WFE_rms / λ)^2) | Surface figure, alignment tolerance, defocus, thermal drift, stop location | Broadens PSF, reduces peak intensity, depresses MTF |
| **PSF (Point Spread Function)** | Image of a point source; system impulse response. | PSF(x,y), FWHM, peak intensity, wing energy | PSF(x,y) ∝ |FT{Pupil}|² (diffraction theory) | f/#, aperture shape, obscuration, WFE, scattering | Image blur kernel; PSF core vs wings affect EE and SNR |
| **MTF / OTF** | Contrast transfer vs spatial frequency. | MTF(f), MTF50, MTF@Nyquist | OTF = FT{PSF}; MTF = |OTF| | Aberration balancing, stop placement, field correction | Predicts contrast and resolvable detail (lp/mm) |
| **Optical Cutoff Frequency (fc)** | Diffraction-limited maximum spatial frequency transmitted by optics. | fc (lp/mm) | fc ≈ 1 / (λ·F#) = 2NA / λ (incoherent circular pupil) | F#, wavelength, numerical aperture | Sets theoretical resolution limit of optical system |
| **Detector Nyquist Frequency (fN)** | Maximum spatial frequency sensor can sample without aliasing. | fN (lp/mm) | fN = 1 / (2p), where p = pixel pitch | Pixel pitch, binning, demosaic | Frequencies above fN alias into lower frequencies |
| **Sampling Ratio (Q)** | Measures optical resolution vs detector sampling. | Q = fN / fc | Q = (λ·F#) / (2p) | Joint choice of pixel pitch and F# | Q << 1 undersampled; Q ≈ 1 matched; Q > 1 oversampled |
| **Pixel MTF (Integration Effect)** | Pixel integrates light over finite area (low-pass filtering). | MTF_pixel(f) | 1D: MTF_pixel(f) = sinc(π f w); typically w ≈ p | Pixel size, fill factor, microlens | Reduces high-frequency contrast even with perfect optics |
| **Encircled / Ensquared Energy** | Energy within a radius (EE) or pixel box (ensquared). Indicates coupling efficiency to detector. | EE(r), Ensquared Energy | EE(r₀) = (1/E) ∫∫ I(r,θ) r dθ dr | Focus, aberrations, scattering, pixel size | Directly affects per-pixel signal and detection sensitivity |
| **SNR Impact (Imaging Task)** | Contrast loss and energy spreading reduce detection SNR at target frequency. | SNR(f), output contrast | C_out(f) = C_in(f) · MTF_total(f) | Optics MTF, pixel MTF, jitter, detector noise | Lower contrast at target frequency reduces detection margin |

**Optical Aberrations Summary Table：**
| Aberration                            | Type          | Physical Cause                                         | Field Location | Wavefront Aberration Term        | Typical Image Effect                                | Key System Factors                         | Common Correction                            |
| ------------------------------------- | ------------- | ------------------------------------------------------ | -------------- | -------------------------------- | --------------------------------------------------- | ------------------------------------------ | -------------------------------------------- |
| **Spherical Aberration**              | Monochromatic | Marginal rays focus differently than paraxial rays     | On-axis        | W040 * rho^4                     | Circular blur spot                                  | aperture size, surface curvature, f-number | aspheric surface, aperture stop optimization |
| **Coma**                              | Monochromatic | Different pupil zones produce different magnifications | Off-axis       | W131 * rho^3 * h * cos(theta)    | Comet-shaped blur                                   | field angle, aperture size, stop location  | symmetric design, stop placement             |
| **Astigmatism**                       | Monochromatic | Tangential and sagittal rays focus at different planes | Off-axis       | W222 * rho^2 * h^2 * cos(2theta) | Line or elliptical blur                             | field height, lens symmetry                | balanced lens groups                         |
| **Field Curvature**                   | Monochromatic | Petzval sum causes curved image surface                | Off-axis       | W220 * rho^2 * h^2               | Image best focus lies on curved surface             | optical power distribution                 | field flattener                              |
| **Distortion**                        | Monochromatic | Magnification varies across field                      | Off-axis       | W311 * rho * h^3 * cos(theta)    | Barrel or pincushion distortion                     | field angle, principal ray geometry        | lens group redistribution                    |
| **Longitudinal Chromatic Aberration** | Chromatic     | Refractive index varies with wavelength                | On-axis        | focal length = f(lambda)         | Different colors focus at different axial locations | glass dispersion, wavelength band          | achromatic doublet                           |
| **Lateral Chromatic Aberration**      | Chromatic     | Magnification varies with wavelength                   | Off-axis       | magnification = m(lambda)        | Color fringing at edges                             | field height, glass dispersion             | apochromatic design                          |





####
**像差与光学参数关系**
| 参数                             | 主要影响像差                      |
| ------------------------------ | --------------------------- |
| **Aperture / f-number**        | spherical aberration、coma   |
| **Field of View**              | coma、astigmatism、distortion |
| **Optical power distribution** | field curvature             |
| **Stop location**              | coma、distortion             |
| **Wavelength band**            | chromatic aberrations       |
| **Principal plane location**   | distortion、field curvature  |
| **Lens symmetry**              | coma、distortion             |


####
**主点-** The cardinal points of an optical system include two focal points, two principal points, and two nodal points. These six points describe the first-order imaging properties of a system.
#####
**主平面-** Principal planes are reference planes in an optical system where refraction is assumed to occur in the equivalent thin-lens model.
When the refractive indices of object space and image space are the same, the nodal points coincide with the principal points.
Principal plane（主平面）的位置取决于系统的“光焦度分布（optical power distribution）
- 正光焦度在前 → principal plane 往后移
- 负光焦度在前 → principal plane 往前移



####
**设计实例-**
Telephoto lens 的 principal plane 在镜头外面，复杂镜组改变了H' location。导致 EFL >> physical length
In a telephoto design, a positive front group is combined with a negative rear group.
The negative rear group effectively increases the focal length while shortening the physical length of the lens.
As a result, the principal plane shifts forward and can even lie in front of the lens system.



Wide-angle lenses often use a retrofocus design with a negative front group and a positive rear group.
The negative front group expands the field of view and increases the back focal distance.
This optical power distribution shifts the principal plane into the interior of the system.

| System Type       | Structure                             | Field of View | Principal Plane Location | BFL        | Typical Use           |
| ----------------- | ------------------------------------- | ------------- | ------------------------ | ---------- | --------------------- |
| Normal Lens       | symmetric positive lenses             | moderate      | near center of lens      | small      | standard cameras      |
| Wide-Angle Lens   | strong negative front + positive rear | large         | inside system            | large      | landscape, smartphone |
| Retrofocus Lens   | negative front group                  | very large    | inside system            | very large | DSLR wide-angle       |
| Telephoto Lens    | positive front + negative rear        | narrow        | in front of lens         | short      | long focal length     |
| Inverse Telephoto | another name for retrofocus           | large         | inside                   | large      | wide-angle SLR        |
