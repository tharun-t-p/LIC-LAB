#  Experiment – 02 B  
# Design of Common Source Amplifier with Current Source Load (180nm CMOS)

---

## 1️ Aim

To design and analyze a Common Source amplifier using 180nm CMOS technology with NMOS current source and PMOS active load under given power and load specifications.

---

## 2️ Given Specifications

 Parameter  Value 

 VDD  1.2 V
 
 Power (P)  ≤ 0.4 mW
 
 Load Capacitance (CL)  0.5 pF
 
 Technology  180 nm 
 
 Ln  360 nm 

---

## Theory

A Common Source (CS) amplifier is a fundamental MOSFET amplifier configuration in which the input signal is applied at the gate terminal, the output is taken from the drain terminal, and the source terminal is common to both input and output. In 180nm CMOS technology, the amplifier typically consists of an NMOS transistor acting as the amplifying device and a PMOS transistor functioning as an active load, while an additional NMOS may be used as a current source for bias stabilization. For proper amplification, all transistors must operate in the saturation region.

When a MOSFET operates in saturation, the drain current is governed by the square-law equation:

ID = (μn Cox / 2) × (W/L) × (VOV)²

where VOV = VGS − VTH is the overdrive voltage, μn is the carrier mobility, Cox is the oxide capacitance per unit area, and W/L is the transistor aspect ratio. The small-signal transconductance is obtained by differentiating the drain current with respect to VGS, resulting in:

gm = 2ID / VOV

Due to channel length modulation, the transistor exhibits finite output resistance given by:

ro = 1 / (λ ID)

where λ is the channel length modulation parameter. The voltage gain of the common source amplifier with an active load is therefore determined by the product of transconductance and effective output resistance. For a simple active load configuration, the small-signal voltage gain is:

Av = - gm (ro1 || ro3)

If a current source transistor contributes additional output resistance, the gain expression becomes:

Av = - gm (ro1 || ro3) / (1 + gm ro2)

The negative sign indicates a 180° phase shift between input and output. For saturation operation, the conditions VDS ≥ VOV (for NMOS) and VSD ≥ VOV (for PMOS) must be satisfied. The high-frequency response of the amplifier is primarily limited by the load capacitance CL, and the upper cutoff frequency is given by:

fH = 1 / (2π Rout CL)

where Rout is the total output resistance seen at the drain node. Thus, the performance of the common source amplifier depends on transconductance, output resistance, bias current, and load capacitance, which collectively determine gain, bandwidth, and power consumption.

## 3️ Circuit Description

- M1 → NMOS (Amplifying transistor)
- M2 → NMOS (Current source)
- M3 → PMOS (Active load)
- Output taken at drain of M1
- Bias voltages: VB1 and VB2

  without capacitor

---

## 4️ Design Assumptions

Assume:

VOV = 0.2 V  
VTH = 0.366 V  

---

## 5️ DC Bias Calculations

### 5.1 For M1 (NMOS)

VOV = VGS − VTH  

VGS = VOV + VTH  

VGS = 0.2 + 0.366  

VGS = 0.566 V  

Assume:

VS = 0.3 V  

VG = VGS + VS  

VG = 0.566 + 0.3  

VG = 0.866 V  

Output bias:

Vout = VDD / 2  

Vout = 1.2 / 2  

Vout = 0.6 V  

Check saturation:

VDS = Vout − VS  

VDS = 0.6 − 0.3  

VDS = 0.3 V  

Since:

VDS ≥ VOV  

0.3 ≥ 0.2  ✔ (Saturation satisfied)

---

### 5.2 For M2 (NMOS Current Source)

VGS = 0.566 V  

VG = VGS + VS  

VG = 0.566 + 0  

VG = 0.566 V  

---

### 5.3 For M3 (PMOS)

VOV = VSG − |VTH|

0.2 = VSG − 0.39  

VSG = 0.59 V  

Gate voltage:

VG = VDD − VSG  

VG = 1.2 − 0.59  

VG = 0.61 V  

Check saturation:

VSD = VDD − Vout  

VSD = 1.2 − 0.6  

VSD = 0.6 V  

Since:

VSD ≥ VOV  

0.6 ≥ 0.2  ✔ (Saturation satisfied)

---

## 6️ Width Calculations

Using saturation current equation:

ID = (μn εox / tox) × (W/L) × (VOV² / 2)

---

### For M1 and M2 (NMOS)

W ≈ 7.805 μm  

---

### For M3 (PMOS)

W ≈ 18.473 μm  

---

## 7️ Simulation Results

In simulation:

ID = 200 μA  
Vout = 0.6 V  

Optimized widths:

For M1 & M2:

W = 34.305 μm  

For M3:

W = 44.873 μm  

---

## 8️ Transient Analysis

Av = Vout / Vin  

Av = (627.83 × 10⁻³ − 585.94 × 10⁻³) / (20 × 10⁻³)

Av = 2.0945 V/V  

Gain in dB:

Av(dB) = 20 log10(2.0945)

Av(dB) = 6.4216 dB  

---

## 9️ Theoretical Gain Calculation

Gain expression:

Av = - gm1 (ro1 || ro3) / (1 + gm1 ro2)

---

### 9.1 Transconductance

gm1 = 2ID / VOV  

gm1 = (2 × 200 × 10⁻⁶) / 0.2  

gm1 = 2 × 10⁻³ S  

---

### 9.2 Output Resistances

For NMOS:

ro1 = ro2 = 1 / (λ ID)

ro1 = 1 / (0.1 × 200 × 10⁻⁶)

ro1 = 50 kΩ  

For PMOS:

ro3 = 1 / (0.12 × 200 × 10⁻⁶)

ro3 = 41.666 kΩ  

---

### 9.3 Parallel Resistance

ro1 || ro3 = 22.727 kΩ  

---

### 9.4 Final Gain

Av = - (2 × 10⁻³ × 22.727 × 10³) / (1 + 2 × 10⁻³ × 50 × 10³)

Av = -0.45 V/V  

Gain in dB:

Av(dB) = -6.9357 dB  

---

##  Result/Inference

- The amplifier operates in saturation region.
- DC biasing verified.
- Simulated gain = 2.0945 V/V (6.42 dB)
- Theoretical gain = 0.45 V/V
- Design satisfies power constraint.

---

## 1️0 Conclusion

The Common Source amplifier with current source load was successfully designed using 180nm CMOS technology. Proper biasing ensures saturation operation. Simulation and theoretical values show acceptable agreement considering channel length modulation and non-ideal effects.

---

**Submitted By:**  
Tharun Gowda  
Electronics and Communication Engineering  
National Institute of Engineering, Mysore  

