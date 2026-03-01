#  Experiment – 02  A 
# Design of Common Source Amplifier Using 180nm CMOS Technology (PMOS Active Load)

---

## 1️ Aim

To design and analyze a **Common Source (CS) amplifier** using **180nm CMOS technology** with a **PMOS active load**, satisfying given power and frequency specifications.

---

## 2️ Given Specifications

 Parameter   Value 

 Supply Voltage (VDD)  1.5 V 
 
 Maximum Power  ≤ 0.5 mW 
 
 Load Capacitance (CL)  1 pF
 
 Threshold Voltage (VT)  0.36 V
 
 Overdrive Voltage (VOV)| 0.25 V
 
 Source Voltage (VRS)  0.2 V
 
 Technology  180 nm CMOS 

---
## Theory – Common Source Amplifier (180nm CMOS with PMOS Active Load)

A Common Source (CS) amplifier is a MOSFET amplifier configuration in which the source terminal is common to both input and output. 
The input signal is applied at the gate and the output is taken from the drain. 
In this experiment, NMOS acts as the amplifying device and PMOS acts as an active load.

---

 DC Analysis (Biasing Condition)

For MOSFET to operate in saturation region:

VDS ≥ VGS − VT

Overdrive voltage:

VOV = VGS − VT

Drain current in saturation:

ID = (1/2) μn Cox (W/L) (VGS − VT)²

or

ID = (1/2) kn (VOV)²

Where:

kn = μn Cox (W/L)

Gate voltage:

VG = VGS + VS

Source resistor:

RS = VRS / ID

Power dissipation:

P = VDD × ID

---

 Small Signal Parameters

Transconductance:

gm = ∂ID / ∂VGS

gm = 2ID / VOV

Output resistance (due to channel length modulation):

ro = 1 / (λ ID)

Total output resistance (with PMOS active load):

ro(total) = ro_n || ro_p

---

 Voltage Gain

Without source degeneration:

Av = − gm ro

With source degeneration:

Av = − gm ro / (1 + gm RS)

Negative sign indicates 180° phase shift.

---

Frequency Response

High frequency cutoff:

fH = 1 / (2π ro CL)

Unity Gain Bandwidth:

UGB = |Av| × fH

Bandwidth:

BW = fH − fL

For high-pass coupling:

fL = 1 / (2π RC)

---


Gain depends on gm and ro.  
gm depends on ID and VOV.  
ro depends on channel length modulation (λ).  
Bandwidth depends on load capacitance and output resistance.
## Circuit Description
without capacitor
<img width="1918" height="996" alt="Screenshot 2026-03-01 223628" src="https://github.com/user-attachments/assets/08a0baae-a866-47e1-81dc-a8272fe63116" />
with capacitor
<img width="1916" height="1001" alt="Screenshot 2026-03-01 223859" src="https://github.com/user-attachments/assets/2dae2cde-89f6-4a51-90f6-8c9ee9966507" />
## DC Analysis

DC analysis is used to determine the operating point (Q-point) of the MOSFET by calculating bias voltages and drain current.  
In DC condition, capacitors act as open circuits and only biasing network is considered.  
Proper DC bias ensures the transistor operates in saturation region for correct amplification.

<img width="847" height="621" alt="Screenshot 2026-03-01 223134" src="https://github.com/user-attachments/assets/27b036f1-a2b9-4bf7-8aa0-f270c6ee4920" />

## Transient Analysis

Transient analysis is used to study the time-domain response of the amplifier for a given input signal.  
It shows how the output voltage varies with time and verifies amplification and phase inversion.  
This analysis helps observe rise time, fall time, delay, and signal distortion.

Vin
<img width="1918" height="998" alt="Screenshot 2026-03-01 223334" src="https://github.com/user-attachments/assets/c760e5ed-ecd0-4b29-aeec-47a0a844caf7" />
Vout
<img width="1919" height="997" alt="Screenshot 2026-03-01 223507" src="https://github.com/user-attachments/assets/4a7d9a6e-46cf-4815-afa8-75456986b5d0" />

## AC Analysis

AC analysis is used to determine the small-signal gain and frequency response of the amplifier.  
It evaluates parameters such as voltage gain, bandwidth, and cutoff frequencies.  
This analysis helps in understanding how the amplifier behaves over a range of frequencies.

without capacitor

<img width="1919" height="1003" alt="Screenshot 2026-03-01 223603" src="https://github.com/user-attachments/assets/9b6d511a-aee3-4d5b-b743-4dd83fdc9b27" />
with capacitor

<img width="1919" height="1001" alt="Screenshot 2026-03-01 224504" src="https://github.com/user-attachments/assets/9ad08a8e-9b75-47a5-b73e-2f6d1d0892f1" />


## 3️ Design Calculations

### 3.1 Drain Current Selection

Power constraint:

P = VDD × ID  

ID = P / VDD  

ID = 0.5 mW / 1.5 V  

ID ≈ 333 µA  

Chosen:

ID = 300 µA  

Power used:

P = 1.5 × 300 µA = 0.45 mW ≤ 0.5 mW  

---

### 3.2 NMOS Gate-Source Voltage

VOV = VGS − VT  

VGS = VOV + VT  

VGS = 0.25 + 0.36  

VGS = 0.61 V  

Gate Voltage:

VG = VGS + VRS  

VG = 0.61 + 0.2  

VG = 0.81 V  

---

### 3.3 Source Resistor Calculation

VRS = ID × RS  

RS = VRS / ID  

RS = 0.2 / (300 × 10⁻⁶)  

RS = 666.66 Ω  

---

### 3.4 Transconductance (gm)

gm = 2ID / VOV  

gm = (2 × 300 × 10⁻⁶) / 0.25  

gm = 2.4 mS  

---

### 3.5 Output Resistance (ro)

From bandwidth relation:

fH = 1 / (2π ro CL)

Given:

fH = 148.74 MHz  

ro = 1 / (2π × 148.74 × 10⁶ × 1 × 10⁻¹²)

ro ≈ 1070 Ω  

---

## 4️ Theoretical Voltage Gain

For CS amplifier with source degeneration:

Av = - gm ro / (1 + gm RS)

Calculate numerator:

gm ro = 0.0024 × 1070 = 2.568

Denominator:

1 + gm RS = 1 + (0.0024 × 666.66)

= 1 + 1.6  

= 2.6  

Therefore:

Av = -2.568 / 2.6  

Av ≈ -0.99 V/V  

---

### Gain in dB

Av(dB) = 20 log10(|Av|)

Av(dB) = 20 log10(0.99)

Av(dB) ≈ -0.087 dB  

---

## 5️ Simulation Results

| Parameter | Value |
|------------|--------|
| Voltage Gain | 8.77 V/V |
| Gain (dB) | 18.859 dB |
| High Frequency (fH) | 148.74 MHz |
| Unity Gain Bandwidth | 2.5 GHz |

---

## 6️ Circuit Description

- NMOS transistor acts as the amplifying device.
- PMOS transistor acts as active load.
- Source resistor provides bias stabilization.
- Output taken from drain of NMOS.
- Load capacitor determines bandwidth.

---

## 7️ Result

The Common Source Amplifier using 180nm CMOS technology was successfully designed.

- Power consumption = 0.45 mW (within limit)
- Theoretical gain ≈ -1 V/V
- Simulated gain ≈ 8.77 V/V (18.859 dB)
- Bandwidth ≈ 148.74 MHz

---

## 8️ Inference

1. Source degeneration reduces gain significantly.
2. Active load increases output resistance.
3. Gain depends strongly on gm and ro.
4. Bandwidth is determined mainly by CL and ro.
5. The design satisfies the given power constraint.

---

## 9️ Conclusion

The CS amplifier with PMOS active load was designed using 180nm CMOS technology.  
The circuit meets the power specification and achieves high bandwidth performance.  
Simulation results validate the amplifier operation.

---


