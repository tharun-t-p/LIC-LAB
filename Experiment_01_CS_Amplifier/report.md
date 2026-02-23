Experiment No 01

Aim:
To design and simulate a Common Source (CS) amplifier using an NMOS transistor with 180 nm technology in LTspice.

Given Specifications

1.Supply Voltage (VDD) = 1.5 V
2.Maximum Power Consumption ≤ 0.5 mW
3.Load Capacitance (CL) = 1 pF
4.Channel Length (L) = 180 nm
5.Technology Node = 180 nm CMOS
6.Type of Amplifier = Common Source (CS)

Theory
A Common Source (CS) amplifier is one of the simplest and most widely used MOSFET amplifier configurations. In this circuit, the source terminal is connected to ground, the input signal is given to the gate, and the output is taken from the drain. It is called a common source amplifier because the source terminal is common to both the input and the output sides of the circuit. When the NMOS transistor is properly biased in the saturation region, even a small change in the gate-to-source voltage causes a change in the drain current. This change in drain current creates a corresponding voltage variation across the drain resistor, which results in an amplified output signal. One important characteristic of the CS amplifier is that the output signal is inverted compared to the input, producing a 180° phase shift.

The voltage gain of the CS amplifier mainly depends on the transconductance of the transistor and the value of the drain resistance. For correct operation and proper amplification, the transistor must operate in the saturation region and satisfy the condition 
𝑉
𝐷
𝑆
≥
𝑉
𝐺
𝑆
−
𝑉
𝑇
𝐻
V
DS
	​

≥V
GS
	​

−V
TH
	​

. In this design, the amplifier works with a low supply voltage of 1.5 V, and the power dissipation is limited to 0.5 mW to ensure low-power operation. The presence of a 1 pF load capacitance influences the frequency response by limiting the bandwidth of the amplifier. Overall, the Common Source amplifier successfully provides voltage amplification with phase inversion while meeting the given power and technology requirements.

