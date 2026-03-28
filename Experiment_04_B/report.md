# CMOS Differential Amplifier with Active Load (TSMC 0.18µm)

---

## 1. Aim

To design and analyze a CMOS differential amplifier satisfying:
- VDD = 0.9 V, VSS = -0.9 V  
- Vin,CM = 0 V, Vout,CM = 0 V  
- Power ≤ 1.8 mW  
- Source voltage VS ≈ -0.7 V  
- MOSFETs operating in saturation  

---

## 2. Given Specifications

VDD = +0.9 V  
VSS = -0.9 V  
Vin,CM = 0 V  
Vout,CM = 0 V  
Tail current ≈ 1 mA  
VS ≈ -0.7 V  
Channel length L = 480 nm  

---

## 3. Circuit Description

- NMOS differential pair: M1, M2  
- PMOS active load: M3, M4  
- Tail current source: M5  
- Outputs taken at vout1 and vout2  
- Symmetrical design ensures equal current sharing

  <img width="1256" height="994" alt="Screenshot 2026-03-28 213701" src="https://github.com/user-attachments/assets/d09ecb5e-5606-4510-bbfa-541ed302802c" />


---

## 4. Simulation Results (LTspice)

### Node Voltages

<img width="851" height="627" alt="Screenshot 2026-03-28 213720" src="https://github.com/user-attachments/assets/fbf16655-65a0-40ef-b7d6-4cf5a27be7c4" />


VDD = 0.9 V  
VSS = -0.9 V  

V(vout1) = 0.000614048 V  
V(vout2) = 0.000614048 V  

V(vp) = -0.695219 V  

Transient Analysis

Vout 1

<img width="1918" height="1010" alt="Screenshot 2026-03-28 214243" src="https://github.com/user-attachments/assets/b89a5fec-94e3-4d1d-b862-55e32e1d81eb" />

Vout 2

<img width="1919" height="998" alt="Screenshot 2026-03-28 214329" src="https://github.com/user-attachments/assets/5ba538ab-5fde-4b5c-8f56-d1efd91b2819" />


---

### Currents

Tail current:
I(M5) = 0.0010018 A  

Drain currents:
Id(M1) = 0.0005009 A  
Id(M2) = 0.0005009 A  

PMOS currents:
Id(M3) = 0.0005009 A  
Id(M4) = 0.0005009 A  

---

## 5. Calculations

---

### 5.1 Current Distribution

ISS ≈ 1 mA  

ID1 = ID2 = ISS / 2  

ID = 1 mA / 2  
ID = 0.5 mA  

From simulation:

ID1 = ID2 = 0.0005009 A  

✔ Matches theoretical value  

---

### 5.2 Output Voltage

Since active load is used:

PMOS current = NMOS current  

Net current at output node ≈ 0  

Thus output voltage ideally:

Vout ≈ 0 V  

From simulation:

Vout1 = Vout2 = 0.000614 V ≈ 0 V  

✔ Very small offset → acceptable  

---

### 5.3 Source Voltage

From simulation:

VS = V(vp) = -0.695219 V  

Approx:

VS ≈ -0.7 V  

✔ Matches requirement  

---

### 5.4 Power Dissipation

Total supply voltage:

Vtotal = VDD - VSS  
Vtotal = 0.9 - (-0.9) = 1.8 V  

Tail current:

ISS ≈ 1 mA  

Power:

P = V × I  
P = 1.8 × 0.001  

P = 0.0018 W  
P = 1.8 mW  

✔ Meets constraint  

---

### 5.5 Output Common Mode Voltage

Vout,CM = (Vout1 + Vout2) / 2  

Vout,CM = (0.000614 + 0.000614) / 2  

Vout,CM = 0.000614 V ≈ 0 V  

✔ Requirement satisfied  

---

### 5.6 Saturation Condition

For NMOS:

VDS = VD - VS  

VD ≈ 0.000614 V  
VS ≈ -0.695 V  

VDS = 0.000614 - (-0.695)  
VDS ≈ 0.6956 V  

✔ NMOS in saturation  

For PMOS:

Source at 0.9 V, drain near 0 V  

|VSD| large → saturation  

✔ PMOS in saturation  

---

### 5.7 Current Consistency (KCL)

Total NMOS current:

ID1 + ID2 = 0.5009 mA + 0.5009 mA  
= 1.0018 mA  

Matches:

Tail current ≈ 1.0018 mA  

✔ KCL satisfied  

---

## 6. Result and Inference

### Result

- Vout1 = 0.000614 V  
- Vout2 = 0.000614 V  
- VS ≈ -0.695 V  
- ID1 = ID2 ≈ 0.5 mA  
- Tail current ≈ 1 mA  
- Power ≈ 1.8 mW  

---

### Inference

- Equal current splitting achieved  
- Output common mode is approximately 0 V  
- Very small offset (~0.6 mV) indicates good symmetry  
- Power constraint satisfied  
- All MOSFETs operate in saturation  
- Active load improves amplifier performance  

Hence, the circuit satisfies all design requirements.

---

## 7. Conclusion

The CMOS differential amplifier with active load is successfully designed and verified:

- Meets all given specifications  
- Maintains proper biasing  
- Ensures saturation operation  
- Produces stable and symmetrical output  

Thus, the circuit is suitable for analog applications.

---
