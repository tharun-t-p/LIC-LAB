# Experiment 03


# CHARACTERIZATION AND EXTRACTION OF VARIOUS PARAMETERS OF µA741 IC


---

# AIM

To characterize and extract the parameters of the operational amplifier **µA741** and compare the measured values with the datasheet specifications.

---

# APPARATUS

* µA741 Operational Amplifier IC
* Breadboard
* Connecting wires
* Dual power supply (+15V, −15V)
* Digital multimeter
* Resistors (100Ω, 10kΩ, 470kΩ)
* Capacitors (1000 pF)
* Function generator
* CRO / Oscilloscope

---

# THEORY

An operational amplifier is a high-gain differential amplifier which amplifies the difference between two input signals. Ideally, an op-amp has infinite input impedance and zero output impedance. However, practical op-amps like **µA741** exhibit non-ideal parameters such as input bias current, input offset current, input offset voltage and slew rate.

Input bias current is the average current flowing into the inverting and non-inverting terminals. Input offset current represents the mismatch between these currents. Input offset voltage is the small differential voltage required to make the output voltage zero. Slew rate represents the maximum rate of change of output voltage with respect to time.

---

# FORMULAS

### Input Bias Current

[
I_B = \frac{I_{B1} + I_{B2}}{2}
]

### Input Offset Current

[
I_{OS} = |I_{B1} - I_{B2}|
]

### Input Offset Voltage

[
V_{IO} = \frac{V_O}{1 + \frac{R_F}{R_1}}
]

### Slew Rate

[
SR = \frac{2\pi f_{max} V_m}{10^6} ; V/\mu s
]

---

# PROCEDURE

### Measurement of Input Bias Current

1. Connect the circuit as shown in the diagram.
2. Apply dual power supply of **+15V and −15V**.
3. Measure the output voltage using a multimeter.
4. Use the feedback resistor value to calculate bias current.

---

# CALCULATIONS

## 1️ Inverting Bias Current

<img width="1908" height="1031" alt="Screenshot 2026-03-02 192832" src="https://github.com/user-attachments/assets/13721d87-16a3-44b6-9ec9-aad71e00796c" />


Measured output voltage

[
V_o = 0.024V
]

Feedback resistor

[
R_f = 470k\Omega
]

Formula

[
I_B = \frac{V_o}{R_f}
]

Substituting values

[
I_B = \frac{0.024}{470000}
]

[
I_B = 5.10 \times 10^{-8} A
]

[
I_B = 0.0510 ; \mu A
]

---

## 2️ Input Offset Current

<img width="1913" height="1028" alt="Screenshot 2026-03-02 193208" src="https://github.com/user-attachments/assets/4c6a70dc-b142-4915-9bf9-50a394f85810" />


From experiment

[
I_{OS} = |I_{B1} - I_{B2}|
]

Measured value from experiment

[
I_{OS} = 0.0063 ; \mu A
]

---

## 3️ Input Offset Voltage

<img width="1908" height="1031" alt="Screenshot 2026-03-02 194125" src="https://github.com/user-attachments/assets/3cb1f669-0a50-4de4-98d4-010af887c2e1" />


Measured output voltage

[
V_o = 0.106 V
]

Resistor values

[
R_1 = 100 \Omega
]

[
R_f = 10k\Omega
]

Formula

[
V_{IO} = \frac{V_o}{1 + \frac{R_f}{R_1}}
]

Substituting

[
V_{IO} = \frac{0.106}{1 + \frac{10000}{100}}
]

[
V_{IO} = \frac{0.106}{101}
]

[
V_{IO} = 0.001048V
]

[
V_{IO} = 1.048 ; mV
]

---

# OBSERVATION TABLE

| Sl.No | Parameter             | Datasheet Value | Measured Value |
| ----- | --------------------- | --------------- | -------------- |
| 1     | Input Bias Current    | 80 nA (typical) | 0.0510 µA      |
| 2     | Input Offset Current  | 20 nA (typical) | 0.0063 µA      |
| 3     | Input Offset Voltage  | 2 mV (typical)  | 1.048 mV       |
| 4     | Output Offset Voltage | Depends on gain | Measured       |
| 5     | Slew Rate             | 0.5 V/µs        | Calculated     |

---

# RESULT

The parameters of the **µA741 operational amplifier** such as **input bias current, input offset current and input offset voltage** were measured successfully using the experimental setup. The calculated values are close to the datasheet specifications.

---

# INFERENCE

The experiment demonstrates that practical operational amplifiers exhibit small bias currents and offset voltages due to internal transistor mismatches. These parameters affect precision circuits. The µA741 shows measurable bias current and a limited slew rate, confirming its practical non-ideal behavior.

