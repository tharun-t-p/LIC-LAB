# Experiment 01 

# Design of Common Source (CS) Amplifier using NMOS (180 nm)

## 1. Objective

To design and analyze a Common Source (CS) amplifier using an NMOS transistor in 180 nm technology in LTspice with the following specifications:

- VDD = 1.5 V  
- Power ≤ 0.5 mW  
- CL = 1 pF  
- Channel Length (L) = 180 nm  

---


## 2. Circuit Description

The Common Source amplifier consists of:

- NMOS transistor  
- Drain resistor (RD)  
- DC supply (VDD)  
- Input applied at gate  
- Output taken from drain  
- Source grounded  

The source terminal is common to both input and output, hence the name Common Source amplifier.
<img width="1139" height="812" alt="Screenshot 2026-02-24 115942" src="https://github.com/user-attachments/assets/9426d024-2ac5-4332-814b-28236b6fd3fd" />


---

## 3. Theory

The Common Source (CS) amplifier operates by biasing the MOSFET in the saturation region so that it can provide voltage amplification. For proper operation, the MOSFET must satisfy the saturation condition:

$$
V_{DS} \ge V_{GS} - V_{TH}
$$

This ensures that the transistor remains in the active region where the drain current is controlled mainly by the gate-to-source voltage rather than the drain voltage.

In the saturation region, the drain current is given by:

$$
I_D = \frac{1}{2} \mu_n C_{ox} \left(\frac{W}{L}\right) (V_{GS} - V_{TH})^2
$$

This equation shows that the drain current depends on carrier mobility ($\mu_n$), oxide capacitance ($C_{ox}$), device dimensions ($W/L$), and the overdrive voltage $(V_{GS} - V_{TH})$. By properly choosing the device dimensions and bias voltage, the desired operating current can be achieved.

The small-signal parameter that determines amplification is the transconductance:

$$
g_m = \frac{2I_D}{V_{GS} - V_{TH}}
$$

Transconductance represents how effectively a small change in gate voltage controls the drain current. A higher $g_m$ results in higher voltage gain.

The voltage gain of the Common Source amplifier is given by:

$$
A_v = - g_m R_D
$$

The negative sign indicates a 180° phase shift between the input and output signals, meaning the output is inverted. The magnitude of gain depends on the product of transconductance and drain resistance.

---

## 4. DC Design Calculations

### 4.1 Bias Point Selection

For maximum symmetrical output swing:

VDS = VDD / 2  
VDS = 1.5 / 2 = 0.75 V

---

### 4.2 Power Constraint

P = VDS × ID  

0.5 × 10⁻³ = 0.75 × ID  

ID = (0.5 × 10⁻³) / 0.75  

ID = 0.67 mA  

To maintain safe margin:

ID = 200 µA

---

### 4.3 Drain Resistance Calculation

VDD = ID RD + VDS  

RD = (VDD − VDS) / ID  

RD = (1.5 − 0.75) / (200 × 10⁻⁶)  

RD = 3.75 kΩ

---

## 5. Device Sizing

Given:

VTH = 0.36 V  
VGS = 0.9 V  

Using saturation equation:

ID = (1/2) Kn (W/L) (VGS − VTH)²  

Kn = μn Cox  

Kn = 2.303 × 10⁻⁴  

Solving for W:

W = [2 ID L] / [Kn (VGS − VTH)²]

W = 1.072 µm  

After simulation tuning:

W = 1.58 µm 

## 6. Procedure

1. Open LTspice and create a new schematic file.

2. Place the required components: NMOS transistor (set L = 180nm), 
   drain resistor (RD), input voltage source (Vin), DC supply (VDD = 1.5V), 
   and load capacitor (CL = 1pF).

3. Connect the circuit in Common Source configuration:
   - Source → Ground
   - Gate → Input source
   - Drain → RD → VDD
   - CL connected from Drain to Ground

4. Set the NMOS parameters:
   - Channel Length (L) = 180nm
   - Choose suitable Width (W) as per design
   - Ensure the transistor model corresponds to 180nm technology.

5. Apply DC biasing:
   - Set VDD = 1.5V
   - Adjust gate DC voltage so that the transistor operates in saturation
     (VDS ≥ VGS − VTH).

6. Check power constraint:
   - Run .op (Operating Point) analysis
   - Verify that ID ≤ 333µA
   - Confirm power (P = VDD × ID) ≤ 0.5mW.

7. Perform AC analysis:
   - Add AC amplitude to input source
   - Run .ac analysis
   - Observe voltage gain and confirm 180° phase shift.

8. Perform Transient analysis:
   - Apply small sinusoidal input signal
   - Run .tran simulation
   - Verify amplified and inverted output waveform.

9. Observe frequency response:
   - Confirm bandwidth considering CL = 1pF
   - Ensure amplifier meets design specifications.
### A. DC Operating Point

The DC operating point (Q-point) is the steady-state bias condition of the MOSFET when no input signal is applied. It sets the values of $I_D$ and $V_{DS}$ around which the AC signal varies. For proper amplification, the transistor must operate in the saturation region to ensure linear operation and maximum symmetrical output swing.
<img width="848" height="629" alt="Screenshot 2026-02-24 120006" src="https://github.com/user-attachments/assets/f6bc0079-a17e-480f-884f-a3d0061ed6b2" />


### B. Transient Analysis

Transient analysis is used to observe the time-domain response of the Common Source amplifier. It shows how the output voltage varies with respect to the applied input signal. From the transient waveform, parameters such as peak-to-peak voltage, gain, and phase inversion can be measured. The output waveform is amplified and inverted, confirming proper amplifier operation.

vin
<img width="1917" height="1003" alt="Screenshot 2026-02-24 120501" src="https://github.com/user-attachments/assets/4e5f7329-9665-4a9f-b282-47fe7c129881" />


vout
<img width="1919" height="1001" alt="Screenshot 2026-02-24 120229" src="https://github.com/user-attachments/assets/483ab88c-2cc8-46ed-8218-726b2fd850b4" />


<img width="1918" height="996" alt="Screenshot 2026-02-24 120658" src="https://github.com/user-attachments/assets/31fc6cce-8ea0-409a-b53e-e4e4c869882d" />

### C. AC Analysis

AC analysis is performed to determine the frequency response of the Common Source amplifier. It shows how the gain varies with frequency and helps in identifying the lower and upper cutoff frequencies. From the AC plot, bandwidth and gain-bandwidth product can be calculated. This analysis verifies the amplifier’s performance over a range of operating frequencies.

<img width="1919" height="995" alt="Screenshot 2026-02-24 120927" src="https://github.com/user-attachments/assets/123174af-6feb-474e-ba01-2f644228950e" />




---

## 7. Small Signal Analysis

### 7.1 Transconductance

gm = 2ID / (VGS − VTH)

gm = [2 × 200 × 10⁻⁶] / (0.9 − 0.36)

gm = 7.407 × 10⁻⁴ S

---

### 7.2 Theoretical Gain

Av = gm RD  

Av = (7.407 × 10⁻⁴) × (3.75 × 10³)

Av = 2.77 V/V

Gain in dB:

Av(dB) = 20 log(2.77)

Av = 8.84 dB

---

## 8. Simulation Results

### 8.1 Input Voltage (Peak-to-Peak)

Vin(p-p) = (909.55 − 890.38) mV  

Vin(p-p) = 19.17 mV  

### 8.2 Output Voltage (Peak-to-Peak)

Vout(p-p) = (769.45 − 725.53) mV  

Vout(p-p) = 43.92 mV  

---

### 8.3 Simulated Gain

Av = Vout / Vin  

Av = 43.92 / 19.17  

Av = 2.29 V/V  

Gain in dB:

Av = 20 log(2.29)

Av = 7.2 dB  

---

## 9. Frequency Response

Without Load Capacitor:

Lower cutoff frequency ≈ 0 Hz  
Upper cutoff frequency ≈ 100 GHz  

Bandwidth:

BW = fH − fL  

BW = 100 GHz  

With CL = 1 pF:

fH = 51.338 MHz  

Gain Bandwidth Product:

GBP = Av × BW  

---

## 10. Comparison Table

| Parameter | Theoretical | Simulated |
|------------|-------------|------------|
| Gain (V/V) | 2.77 | 2.29 |
| Gain (dB) | 8.84 dB | 7.2 dB |
| ID | 200 µA | 198.6 µA |
| W | 1.07 µm | 1.58 µm |

---

## 11. Conclusion

- The Common Source amplifier was successfully designed under the given power constraint.
- The amplifier provides approximately 2.3 V/V gain.
- Theoretical and simulated results are reasonably close.
- Gain deviation is due to channel length modulation and parasitic capacitances.
- Load capacitance significantly reduces bandwidth.
- The amplifier produces 180° phase inversion.

---
## 12. Summary/Inference


The Common Source (CS) amplifier was designed with proper DC biasing to operate in the saturation region, satisfying:

$$
V_{DS} \ge V_{GS} - V_{TH}
$$

The drain current was determined using:

$$
I_D = \frac{1}{2} \mu_n C_{ox} \left(\frac{W}{L}\right) (V_{GS} - V_{TH})^2
$$

The small-signal voltage gain was calculated as:

$$
A_v = - g_m R_D
$$

Transient and AC analyses verified the amplification, phase inversion, and bandwidth characteristics of the amplifier.


The simulated voltage gain closely matches the theoretical gain obtained using:

$$
g_m = \frac{2I_D}{V_{GS} - V_{TH}}
$$

Minor deviations occur due to non-ideal effects such as channel length modulation and parasitic capacitances. The experiment confirms that proper DC biasing ensures linear amplification and that gain is directly proportional to transconductance and drain resistance.
