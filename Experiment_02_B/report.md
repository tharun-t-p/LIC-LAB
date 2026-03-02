# Experiment – 02 B 
# CMOS Amplifier Analysis (DC,AC, Small-Signal and Transient Analysis)

---

## 1. Aim
To perform DC analysis, verify saturation conditions, determine small-signal parameters, and calculate the theoretical and practical voltage gain of a CMOS amplifier.

---

## 2. Given Parameters

- Supply Voltage, VDD = 1.5 V  
- Threshold Voltage (NMOS), VTHn = 0.366 V  
- Threshold Voltage (PMOS), |VTHp| = 0.39 V  
- Drain Current, ID = 300 µA  
- Channel Length Modulation (NMOS), λn = 0.1 V⁻¹  
- Channel Length Modulation (PMOS), λp = 0.12 V⁻¹  
- Input Vpp = 20 mV  
- Output Vpp = 32 mV  

---

## 3. Circuit Description

The circuit consists of:

- M1 → PMOS active load  
- M2 → NMOS amplifying transistor  
- M3 → NMOS current source  

The output is taken at the drain of M2.

<img width="1918" height="998" alt="Screenshot 2026-03-02 212123" src="https://github.com/user-attachments/assets/b7ee2857-7730-4832-96ef-f83a8ece5cf9" />


## DC Analysis:

The MOSFETs are biased to operate in the saturation region by establishing a proper DC operating point (Q-point) using VDD = 1.5 V and ID = 300 µA.  
The overdrive voltage VOV = VGS − VTH ensures sufficient channel formation for amplification.  
The calculated VOUT ≈ 1.05 V confirms correct biasing and stable operation of the CMOS amplifier.

<img width="848" height="629" alt="Screenshot 2026-03-02 212624" src="https://github.com/user-attachments/assets/7494f699-aa2d-4670-8019-a5e97a8a8cdf" />



## Transient Analysis:

A small sinusoidal input of 20 mV peak-to-peak is applied to evaluate time-domain response of the amplifier.  
The measured output peak-to-peak voltage is 32 mV, indicating signal amplification with phase inversion.  
The practical voltage gain is Av = Vout/Vin = 32/20 = −1.6 V/V, confirming proper dynamic operation.

Vin

<img width="1919" height="1003" alt="Screenshot 2026-03-02 212215" src="https://github.com/user-attachments/assets/108b14e5-3ef0-411e-a76e-ba341110b4e3" />
 
 Vout

 <img width="1913" height="1002" alt="Screenshot 2026-03-02 212302" src="https://github.com/user-attachments/assets/bd969dca-c2d9-4ad7-bbb8-21b70c4147ed" />

## AC Analysis:

Small-signal analysis is performed by replacing MOSFETs with their hybrid-π models to determine frequency-domain gain.  
The transconductance gm = 2ID/VOV and output resistance ro = 1/(λID) are used to compute voltage gain.  
The theoretical midband gain is Av = −gm(ro1 || ro2), showing inverting amplification behavior.

<img width="1914" height="999" alt="Screenshot 2026-03-02 213425" src="https://github.com/user-attachments/assets/5e6cb820-8b38-42ce-ab33-29960f394c8d" />


---

# 4. DC Analysis

## 4.1 Overdrive Voltage

For PMOS:

VOV = VSG − |VTHp|

VSG = 0.25 + 0.39  
VSG = 0.64 V  

VOV = 0.64 − 0.39  
VOV = 0.25 V  

---

## 4.2 Gate Voltage Calculation

For NMOS:

VGS − VTHn = VOV  

VGS = 0.25 + 0.366  
VGS = 0.6166 V  

Assume source voltage:

VS = 0.3 V  

VG = VGS + VS  

VIN = 0.6166 + 0.3  
VIN = 0.916 V  

---

## 4.3 Output Voltage

VOUT = (VDD / 2) + VS  

VOUT = 0.75 + 0.3  

VOUT = 1.05 V  

---

# 5. Saturation Region Verification

## 5.1 For NMOS (M2)

Saturation condition:

VDS ≥ VGS − VTHn  

0.75 ≥ 0.6166 − 0.366  
0.75 ≥ 0.25  

Hence, M2 operates in saturation region.

---

## 5.2 For PMOS (M1)

VSD = VDD − VOUT  

VSD = 1.5 − 0.95  
VSD = 0.55 V  

Saturation condition:

VSD ≥ VSG − |VTHp|  

0.55 ≥ 0.64 − 0.39  
0.55 ≥ 0.25  

Hence, M1 operates in saturation region.

---

# 6. Small Signal Analysis

## 6.1 Output Resistance

ro = 1 / (λ ID)

For M2 and M3:

ro2 = ro3 = 1 / (0.1 × 300 × 10⁻⁶)  
ro2 = 33.33 × 10³ Ω  

For M1:

ro1 = 1 / (0.12 × 300 × 10⁻⁶)  
ro1 = 27.77 × 10³ Ω  

---

## 6.2 Transconductance

gm = 2ID / VOV  

gm = (2 × 300 × 10⁻⁶) / 0.25  

gm = 2.4 × 10⁻³ S  

---

## 6.3 Theoretical Voltage Gain

Av = −gm (ro1 || ro2) / (1 + gm ro2)

Effective parallel resistance:

ro1 || ro2 ≈ 15.15 × 10³ Ω  

Substituting values:

Av ≈ −0.44 V/V  

Gain in dB:

Av(dB) = 20 log |Av|  

Av ≈ 6.935 dB  

---

# 7. Transient Analysis

Input peak-to-peak voltage:

Vin(pp) = 20 mV  

Output peak-to-peak voltage:

Vout(pp) = 32 mV  

Voltage Gain:

Av = Vout(pp) / Vin(pp)  

Av = 32 / 20  

Av = −1.6 V/V  

|Av| = 1.6  

Gain in dB:

Av(dB) = 20 log(1.6)  

Av(dB) ≈ 4.32 dB  

---

# 8. Results

• All MOSFETs operate in saturation region.  
• DC operating point is properly established.  
• Theoretical Gain ≈ −0.44 V/V  
• Practical Gain ≈ −1.6 V/V  
• Practical Gain in dB ≈ 4.32 dB  

---

# 9. Inference
 The CMOS amplifier is properly biased with all transistors operating in saturation region, ensuring stable amplification.  
The small-signal and transient analyses confirm inverting behavior with measurable voltage gain.  
The deviation between theoretical and practical gain is due to non-ideal effects such as channel length modulation and model approximations.

# 10. Conclusion

The CMOS amplifier was successfully analyzed under DC and small-signal conditions.  
All devices satisfy saturation criteria ensuring proper amplification.  
The practical gain obtained from transient analysis is higher than the theoretical value due to small-signal approximations and modeling assumptions.

---


