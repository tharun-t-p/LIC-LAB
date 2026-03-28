# CMOS Differential Amplifier Design Report (TSMC 0.18µm)

---

## 1. Aim

To design and analyze a CMOS differential amplifier that satisfies:
- VDD = 0.9 V, VSS = -0.9 V  
- Vin,CM = 0 V, Vout,CM = 0 V  
- Power ≤ 1.8 mW  
- Proper saturation operation  

---

## 2. Given Specifications

VDD = +0.9 V  
VSS = -0.9 V  
Vin,CM = 0 V  
Vout,CM = 0 V  
Tail Current (ISS) = 1 mA  
Source Voltage VS ≈ -0.7 V  
Load Resistance R1 = R2 = 1.8 kΩ  
Channel Length L = 480 nm  

---

## 3. Circuit Description

The circuit consists of:
- Two NMOS transistors (M1, M2) forming a differential pair  
- A constant tail current source (ISS = 1 mA)  
- Two load resistors (R1 and R2 = 1.8 kΩ)  
- Symmetrical structure for equal current distribution


 <img width="993" height="923" alt="Screenshot 2026-03-28 211845" src="https://github.com/user-attachments/assets/e7028118-8b84-498b-bd94-c881e09647a6" />



---

## 4. Simulation Results

### Node Voltages

<img width="852" height="632" alt="Screenshot 2026-03-28 211949" src="https://github.com/user-attachments/assets/16387a6c-2ca4-46ba-acfe-a0dc13fb2cf3" />



VDD = 0.9 V  
VSS = -0.9 V  

V(out1) = 0 V  
V(out2) = 0 V  

V(source node, VS) = -0.700789 V  

Transient Analysis

Vout 1

<img width="1920" height="1200" alt="Screenshot 2026-03-27 193504" src="https://github.com/user-attachments/assets/b5aa496d-33bc-4a0b-817c-d5f59a947217" />

Vout 2

<img width="1920" height="1200" alt="Screenshot 2026-03-27 193529" src="https://github.com/user-attachments/assets/8ce7dd66-8460-4b99-8cdc-c40118456000" />





---

### Currents

Tail current:
ISS = 0.001 A  

Drain currents:
ID1 = 0.0005 A  
ID2 = 0.0005 A  

Resistor currents:
IR1 = 0.0005 A  
IR2 = 0.0005 A  

---

## 5. Calculations

---

### 5.1 Current Distribution

ISS = 1 mA  

ID1 = ID2 = ISS / 2  

ID = 1 mA / 2  
ID = 0.5 mA  

Convert:
ID = 0.0005 A  

✔ Matches simulation:
ID1 = ID2 = 0.0005 A  

---

### 5.2 Output Voltage

Formula:

Vout = VDD - (ID × RD)

Substitute:

Vout = 0.9 - (0.5 mA × 1.8 kΩ)

Convert units:

0.5 mA = 0.0005 A  
1.8 kΩ = 1800 Ω  

Calculation:

Vout = 0.9 - (0.0005 × 1800)  
Vout = 0.9 - 0.9  
Vout = 0 V  

✔ Matches simulation:
V(out1) = 0 V  
V(out2) = 0 V  

---

### 5.3 Source Voltage

From simulation:

VS = -0.700789 V  

Approximation:

VS ≈ -0.7 V  

✔ Matches requirement  

---

### 5.4 Power Dissipation

Total supply voltage:

Vtotal = VDD - VSS  
Vtotal = 0.9 - (-0.9)  
Vtotal = 1.8 V  

Power formula:

P = V × I  

Substitute:

P = 1.8 × 1 mA  

Convert:

1 mA = 0.001 A  

Calculation:

P = 1.8 × 0.001  
P = 0.0018 W  
P = 1.8 mW  

✔ Meets power constraint  

---

### 5.5 Output Common Mode Voltage

Formula:

Vout,CM = (Vout1 + Vout2) / 2  

Calculation:

Vout,CM = (0 + 0) / 2  
Vout,CM = 0 V  

✔ Requirement satisfied  

---

### 5.6 Saturation Check

Formula:

VDS = VD - VS  

Substitute:

VD = 0 V  
VS = -0.7 V  

Calculation:

VDS = 0 - (-0.7)  
VDS = 0.7 V  

Condition:

VDS > (VGS - VT)  

✔ MOSFET operates in saturation  

---

### 5.7 Load Current Verification

Formula:

IR = (VDD - Vout) / R  

Substitute:

IR = (0.9 - 0) / 1.8 kΩ  

Convert:

1.8 kΩ = 1800 Ω  

Calculation:

IR = 0.9 / 1800  
IR = 0.0005 A  
IR = 0.5 mA  

✔ Matches simulation  

---

## 6. Final Verification

| Parameter | Expected | Obtained | Status |
|----------|---------|---------|--------|
| ID1 = ID2 | 0.5 mA | 0.5 mA | ✔ |
| Vout | 0 V | 0 V | ✔ |
| VS | -0.7 V | -0.7008 V | ✔ |
| Power | ≤1.8 mW | 1.8 mW | ✔ |
| Region | Saturation | Saturation | ✔ |

---

## 7. Result 

The CMOS differential amplifier was successfully simulated and analyzed. The obtained results are as follows:

- Output voltages:
  - V(out1) = 0 V  
  - V(out2) = 0 V  

- Source node voltage:
  - VS = -0.7008 V (≈ -0.7 V)

- Drain currents:
  - ID1 = 0.5 mA  
  - ID2 = 0.5 mA  

- Tail current:
  - ISS = 1 mA  

- Power dissipation:
  - P = 1.8 mW  

- Output common mode voltage:
  - Vout,CM = 0 V  

## 8. Inference

- The differential pair achieves equal current splitting due to symmetry.  
- The output voltages are centered at 0 V, satisfying the required common-mode condition.  
- The power consumption (1.8 mW) meets the specified constraint.  
- The source node is properly biased at approximately -0.7 V.  
- The MOSFETs operate in saturation, ensuring correct amplifier operation.  

Hence, the circuit is correctly designed and meets all given specifications.

## 9. Conclusion

The CMOS differential amplifier is successfully designed and verified:

- Equal current distribution achieved  
- Output voltage centered at 0 V  
- Power consumption within specified limit  
- MOSFETs operate in saturation region  

Hence, the circuit satisfies all given design requirements.

---
