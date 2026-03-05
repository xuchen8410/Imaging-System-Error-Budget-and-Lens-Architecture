**Physics → Materials → Detector → Noise → Optical System → Performance Modeling → System Architecture** 组织。
| Band                     | Wavelength Range | Typical Use                         |
| ------------------------ | ---------------- | ----------------------------------- |
| **VIS**                  | 0.4 – 0.7 µm     | human vision                        |
| **NIR (Near IR)**        | **0.7 – 1.4 µm** | fiber optics, night vision          |
| **SWIR (Short-Wave IR)** | **1.4 – 3 µm**   | imaging through haze, laser sensing |
| **MWIR (Mid-Wave IR)**   | **3 – 5 µm**     | missile seekers, hot targets        |
| **LWIR (Long-Wave IR)**  | **8 – 14 µm**    | thermal imaging                     |
| **VLWIR / FIR**          | >14 µm           | astronomy                           |


atmospheric windows:
| Window   | Range      | Reason                            |
| -------- | ---------- | --------------------------------- |
| **SWIR** | 1–2.5 µm   | low atmospheric absorption        |
| **MWIR** | 3–5 µm     | hot target emission               |
| **LWIR** | 8–12/14 µm | room-temperature thermal emission |

| Material               | Transmission Range | Notes                         |
| ---------------------- | ------------------ | ----------------------------- |
| **Fused Silica**       | 0.18 – 3.5 µm      | VIS + NIR                     |
| **BK7**                | 0.35 – 2.5 µm      | visible optics                |
| **Sapphire (Al₂O₃)**   | 0.2 – 5.5 µm       | very strong, missile domes    |
| **CaF₂**               | 0.2 – 8 µm         | good IR imaging material      |
| **BaF₂**               | 0.2 – 11 µm        | fragile but wide transmission |
| **MgF₂**               | 0.12 – 7 µm        | UV → MWIR                     |
| **Silicon (Si)**       | **1.2 – 7 µm**     | common MWIR optics            |
| **Germanium (Ge)**     | **2 – 14 µm**      | dominant LWIR material        |
| **ZnS**                | **0.4 – 12 µm**    | multispectral windows         |
| **ZnSe**               | **0.5 – 20 µm**    | CO₂ laser optics              |
| **Chalcogenide glass** | **1 – 14 µm**      | molded IR optics              |



# 1 Infrared Radiation Physics
红外探测的基础来自 **热辐射物理 (Thermal Radiation)**。

## 1.1 普朗克黑体辐射
目标辐射功率由 Planck 定律决定：
\[
L_\lambda(T)=\frac{2hc^2}{\lambda^5}\frac{1}{e^{hc/\lambda kT}-1}
\]
其中：
|符号|含义|
|---|---|
|h|Planck 常数|
|c|光速|
|k|Boltzmann 常数|
|T|目标温度|
|λ|波长|

### Wien 位移定律
\[
\lambda_{max} = \frac{2898}{T} (\mu m\cdot K)
\]
典型情况：
|目标|峰值波段|
|---|---|
|导弹尾焰 (~1000K)|MWIR|
|飞机机体 (~300K)|LWIR|
|地面背景|LWIR|
# 2 大气窗口 (Atmospheric Windows)
红外系统主要工作在两个窗口：
|波段|范围|特点|
|---|---|---|
|MWIR|3–5 µm|高温目标对比度高|
|LWIR|8–12 µm|常温目标探测|
原因：
- CO₂ / H₂O 吸收较小
- 大气透过率高

# 3 红外探测器材料

红外探测器材料决定系统性能。

## 3.1 HgCdTe (MCT)

最重要的红外材料之一。
特点：
- 可调 bandgap
- MWIR / LWIR 可覆盖
- 极高探测率 D*
材料特性：
\[
E_g(x)= -0.302 + 1.93x - 0.81x^2
\]
通过调整 **Cd 组分 x** 控制波段。
缺点：
- 暗电流高
- 需要 **77K 低温冷却**
暗电流：
\[
I_d \propto e^{-E_g/kT}
\]
温度降低 → 暗电流指数下降。

## 3.2 InSb
典型 MWIR 探测器。 特性：
|参数|说明|
|---|---|
|波段|3–5 µm|
|响应速度|很快|
|噪声|较低|
|冷却|需要|
应用：
- 高速 IR 成像
## 3.3 Microbolometer (非制冷)
常见材料：
- VOx
- a-Si
特点：
|属性|说明|
|---|---|
|波段|LWIR|
|冷却|不需要|
|成本|低|
|速度|较慢|

工作原理：

吸收 IR → 温度变化 → 电阻变化。

热时间常数：

\[
\tau = \frac{C}{G}
\]
C = 热容  
G = 热导
τ 越大 → 响应越慢。

## 3.4 Type-II Superlattice (T2SL)
新一代红外材料：
InAs / GaSb
优点：
- 更低暗电流
- 抑制 Auger recombination
- 工艺可控
未来可能替代 MCT。

# 4 红外探测器结构
现代 IR 系统主要使用：
## FPA (Focal Plane Array)
二维阵列：






# 5 噪声模型 (Noise Model)

红外系统设计的关键。

## 5.1 Shot Noise
光子统计噪声：
\[
i_{shot}=\sqrt{2qI\Delta f}
\]

## 5.2 Johnson Noise

热噪声：
\[
i_{johnson}=\sqrt{4kT\Delta f/R}
\]

## 5.3 1/f Noise
低频电子噪声。
影响：
- 长时间积分
- 低频系统

## 5.4 Photon Noise
光子统计噪声：
\[
\sigma_{photon} = \sqrt{N}
\]
N = photon count

# 6 BLIP 条件

BLIP：Background Limited Infrared Photodetection
条件：






### 光学设计
Optical power distribution. TMAs consist of three conic mirrors: a concave primary (M1) that provides most of the converging power, a convex secondary (M2) that typically has negative optical power and relays the pupil, and a concave tertiary (M3) that refocuses the beam to a flat focal plane. In some designs a folding flat (M4) is included to redirect the optical path.
三镜消像差系统曲率与一阶光学指标关系

在三镜消像差系统中，主镜（M1）、次镜（M2）和三镜（M3）的曲率半径直接决定了有效焦距、瞳位置以及像差的分布。以下用简单公式总结它们与一阶光学参数之间的关系（假设凹面镜曲率半径为正，凸面镜为负）：

单镜焦距

单镜焦距：镜面的等效焦距与其曲率半径有关。凹面镜的焦距 f_i 满足 f_i = R_i / 2；凸面镜焦距也为 R_i / 2 但为负值。主镜焦距 f_1 决定系统的收敛速度（F/#），焦距越短，系统越“快”，像差敏感性越高。

次镜放大率

次镜放大率：次镜的放大率 m_2 与主镜和次镜焦距之比近似为 m_2 = - f_1 / f_2 = - R_1 / R_2。负号表示形成倒像。放大率的绝对值越大，入瞳被压缩或放大的程度越大，影响后续镜面光束直径和瞳位置。

有效焦距

系统有效焦距：三镜组合的有效焦距 F 可用主镜、次镜和三镜的焦距近似表示，例如：

F ≈ (f_1 * f_3) / |m_2|

当主镜更快（R_1 减小）或次镜放大率增加时，为保持相同 F，三镜需要相应调整曲率。

实像瞳位置

实像瞳位置：凹面主镜与凸面次镜组成类似 Mersenne 光束压缩器。次镜将入口瞳像到有限位置，其位置由两镜焦距和间距决定。负放大率 m_2 将瞳从无穷远拉回实像，使设计者能够在次镜和三镜之间放置光阑或冷阑。

像面曲率和像差再分配

像面曲率 (Petzval 和场曲)：对于反射面，Petzval 曲率贡献 C_i 可表示为 C_i = 2 / R_i，凹面为正，凸面为负。系统的净像面曲率为各贡献之和：

∑ C_i = 2/R_1 + 2/R_2 + 2/R_3

若要获得平坦焦面，需要调整三镜曲率使总和约为零，即：

2/R_1 - 2/|R_2| + 2/R_3 ≈ 0

因此，当 R_1 减小（主镜更快）时，需要减小 R_2 或 R_3 的绝对值，以抵消新增的场曲。

像差再分配：次镜不仅决定瞳位置，还引入负球差以抵消凹面镜的正球差；其曲率越小（|R_2| 越小），负球差越强。三镜的曲率和位置用于抑制剩余的像散和彗差，并调整视场中心与边缘的像质平衡。

总结

这些关系说明了各镜曲率半径与一阶光学指标的耦合：

调整主镜半径改变系统焦长和 F 数；

次镜曲率通过放大率控制瞳尺寸和光束压缩，并平衡像差；

三镜曲率用于修正场曲和畸变，确保焦面平坦。

设计时通常先根据任务需求确定主镜口径和有效焦距，再用上述关系初估各镜曲率和间距，随后在光学设计软件中微调，满足具体的像差和结构限制。
