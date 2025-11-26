---
marp: true
theme: default
paginate: true
math: katex
size: 16:9
title: "Embodied Excitability"
description: "15.09.25 Meeting"
---

<!-- _class: lead -->

# Monday Meeting
### 15.09.25 Meeting


---

# Research Summary



- **Characterization of the tests to be performed on the Analog-to-Spike chip**
- **Implementation of the Multi-scale neuron on Brian2** -> Towards Neuromorphic PLL
- **SSCS PICO Open-Source Chipathon 2025** -> Layout Programming using GLayout (Python)
- **Summer School on ASIC Design + SOCN Summer School**

---

# Characterization of the tests of the chip

- Test the Digital Programming Chain
- Characterize amplifiers frequency response (Bode plot) + added linearities
- Quantify leakage observed in simulation (if happens on physical chip)
- DPI Neuron firing rate characterization (FI curve) + V-I Converter characterization
- Per taxel Power Consumption + Total chip Power Consumption
- FPGA, PCB ... specs

---

# Implementation of the Multi-Scale neuron on Brian2


$$
\begin{cases}
\tau \frac{dV}{dt} = -V - I_f^- - I_s^+ - I_s^- - I_u^+ + I_{app} \\
I_f^- = \alpha_f^- * \tanh(V - \delta_f^-)\\
I_s^- = \alpha_s^- * \tanh(V_s^- - \delta_s^-)\\
\tau_s \frac{dV_s^-}{dt} = V - V_s^-\\
I_s^+ = \alpha_s^+ * \tanh(V_s^+ - \delta_s^+)\\
\tau_s \frac{dV_s^+}{dt} = V - V_s^+\\
I_u^+ = \alpha_u^+ * \tanh(V_u^+ - \delta_u^+)\\
\tau_u \frac{dV_u^+}{dt} = V - V_u^+\\

\end{cases}
$$

---

# Implementation of the Multi-Scale neuron on Brian2

<p>
<img src="multi_scale_sim.png" width=60% />
</p>

<style scoped>
p { text-align: center; }
</style>

---

# Towards Neuromorphic PLL

<p>
<img src="pll_structure.png" width=60% />
</p>

<style scoped>
p { text-align: right; }
</style>

- **Phase Detector:** Type-III neuron that spikes at input zero-crossing (or offset)
- **Active Loop Filter:** Injects small perturbation on fast-timescale and tunes slower-timescales gain
- **Voltage-Controlled-Oscillator (VCO):** Multi-scale neuron

---

# Neuromorphic PLL : Next Steps

- Read about Phase-Response curves + Looking at paper [R. Schmetterling, F. Forni, A. Franci and R. Sepulchre, "Neuromorphic Control of a Pendulum"]

- Derive bandwidth of such a PLL to construct multi-PLLs in parallel system for texture recognition

---

# Chipathon on Analog Chip Design

<p>
<img src="cascoded_circuit.png" width=90% />
</p>

<style scoped>
p { text-align: center; }
</style>

--- 

# Chipathon on Analog Chip Design

<p>
<img src="cascoded_sim.png" width=90% />
</p>

<style scoped>
p { text-align: center; }
</style>

---

# Chipathon on Analog Chip Design

- Layout is done using GLayout -> using Python code to generate MOS instances in layout

- Ability to generate layout blocks with transistors sizes as parameters -> reusability of design

- Not available for TECH_XP018_HD PDK yet but supports SKY130 and Global Foundries 180

---

# Chipathon on Analog Chip Design

<p>
<img src="cascoded_layout.png" width=30% />
</p>

<style scoped>
p { text-align: center; }
</style>

---

# Summer School on ASIC Design + SOCN Summer School

- **ASIC**:
  - Introduction to Analog/Digital chip design workflow
  - Good practice for chip design

- **SOCN**:
  - Introduction to Port-Hamiltonian Systems (grasped the idea but not deep details)
---

# Planned Journal Submission / Conferences

- ?