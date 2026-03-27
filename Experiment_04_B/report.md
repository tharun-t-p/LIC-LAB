# CMOS Differential Amplifier with Active Load (TSMC 0.18µm)

---

## 1. Aim

To design and analyze a CMOS differential amplifier with active load that satisfies:
- VDD = 0.9 V, VSS = -0.9 V  
- Vin,CM = 0 V, Vout,CM = 0 V  
- Power ≤ 1.8 mW  
- Source node voltage ≈ -0.7 V  
- Proper saturation operation  

---

## 2. Given Specifications

VDD = +0.9 V  
VSS = -0.9 V  
Vin,CM = 0 V  
Vout,CM = 0 V  
Tail current ≈ 1 mA  
Source voltage VS ≈ -0.7 V  
Channel length L = 480 nm  

---

## 3. Circuit Description

- NMOS differential pair: M1, M2  
- PMOS active load: M3, M4  
- Tail current source: M5  
- Differential inputs applied at gates of M1 and M2  
- Outputs taken at drains (vout1, vout2)  
- Symmetrical configuration ensures equal current distribution


<img width="1905" height="993" alt="Screenshot 2026-03-27 194502" src="https://github.com/user-attachments/assets/079882c9-f907-4df2-9d11-bff65ed45a96" />

---

## 4. Simulation Results (LTspice)

### Node Voltages



<img width="826" height="625" alt="Screenshot 2026-03-27 194600" src="https://github.com/user-attachments/assets/8086ac92-970a-4b50-b5f5-97861cbfabb0" />

VDD = 0.9 V  
VSS = -0.9 V  

V(vout1) = 0.00714762 V  
V(vout2) = 0.00714762 V  

V(vp) = -0.695007 V  

Transient Analysis

Vout 1


<img width="1920" height="1200" alt="Screenshot 2026-03-27 194652" src="https://github.com/user-attachments/assets/a93e1cbe-53eb-449d-b94e-99ac896aff33" />


Vout 2


<img width="1920" height="1200" alt="Screenshot 2026-03-27 194713" src="https://github.com/user-attachments/assets/ae18c5af-ee4b-4eb5-abb3-22f61d3286cc" />

AC Analysis


<img width="1920" height="1200" alt="Screenshot 2026-03-27 194748" src="https://github.com/user-attachments/assets/8f3ce44c-85e0-4d4d-93de-b15bba95de9e" />

---

### Currents

Tail current:
I(M5) = 0.00100073 A  

Drain currents:
Id(M1) = 0.000500365 A  
Id(M2) = 0.000500365 A  

PMOS currents:
Id(M3) = -0.000500365 A  
Id(M4) = -0.000500365 A  

---

## 5. Calculations

---

### 5.1 Current Distribution

ISS ≈ 1 mA  

ID1 = ID2 = ISS / 2  

ID = 1 mA / 2  
ID = 0.5 mA  

From simulation:

ID1 = ID2 = 0.000500365 A  

✔ Matches theoretical value  

---

### 5.2 Output Voltage

For active load, output is near equilibrium (balanced currents):

Since:
PMOS current = NMOS current  

Net current at output node ≈ 0  

Thus:

Vout ≈ small DC offset  

From simulation:

Vout1 = Vout2 = 0.00714762 V ≈ 0 V  

✔ Close to required Vout,CM = 0 V  

---

### 5.3 Source Voltage

From simulation:

VS = V(vp) = -0.695007 V  

Approx:

VS ≈ -0.7 V  

✔ Matches design requirement  

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

Vout,CM = (0.00714762 + 0.00714762) / 2  

Vout,CM = 0.00714762 V ≈ 0 V  

✔ Acceptable (very small offset)  

---

### 5.6 Saturation Condition

For NMOS:

VDS = VD - VS  

VD ≈ 0.007 V  
VS ≈ -0.7 V  

VDS = 0.007 - (-0.7)  
VDS ≈ 0.707 V  

✔ Sufficient for saturation  

For PMOS:

|VSD| is large due to VDD = 0.9 V  

✔ PMOS also in saturation  

---

### 5.7 Current Consistency Check

NMOS current:

ID1 + ID2 ≈ 1.00073 mA  

Matches tail current:

ISS ≈ 1.00073 mA  

✔ KCL satisfied  

---

## 6. Result and Inference

### Result

- Vout1 = 0.0071 V  
- Vout2 = 0.0071 V  
- VS ≈ -0.695 V  
- ID1 = ID2 ≈ 0.5 mA  
- Total current ≈ 1 mA  
- Power ≈ 1.8 mW  

---

### Inference

- Equal current splitting achieved due to symmetry  
- Output common mode is approximately 0 V  
- Small offset (~7 mV) due to practical device mismatch/model effects  
- Power constraint satisfied  
- All MOSFETs operate in saturation  
- Active load improves gain compared to resistive load  

Hence, the circuit is correctly designed and satisfies all specifications.

---

## 7. Conclusion

The CMOS differential amplifier with active load is successfully designed and verified:

- Meets power and bias constraints  
- Produces near-zero output common mode  
- Ensures proper saturation operation  
- Provides stable and symmetrical performance  

Thus, the circuit is suitable for analog amplification applications.

---
