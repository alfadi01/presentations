---
marp: true
theme: default
paginate: true
math: katex
size: 16:9
title: "IIT Monday Meeting"
description: "29.09.25 Meeting"
---

<!-- _class: lead -->

# **Update Meeting October 2025**



---


# **Tactile processing pipeline for texture classification/regression.**

**Three main tasks:**

- Data Recording

- Frequency extraction model

- Spiking Neural Network Derivation


---

# **Data Recording**

**Two options:**

- Use software encoding to get FAI and SAII spikes (from Simon).

- Use hardware encoding : Ella's chip (for now) and then new chip to get tactile recordings.

---


# **Software Encoding**

<div style="display: flex; justify-content: center;">
  <img src="../images/software_encoding.png" style="width:40%;">
</div>

---

# **Hardware Encoding**

Use Omega robot with Robert's piezo sensor + bought capacitive sensor with Ella's chip.

**TODOs:**

- Merge Simon's code with Simeon code. 

- Print 3D support to attach sensors to Omega robot.

- Test setup with different tactile gratings.

---

# **Tactile Gratings**


<div style="display: flex; justify-content: center;">
  <img src="../images/tactile_grating.png" style="width:40%;">
</div>

---

# **Piezoelectric Sensors**

<div style="display: flex; justify-content: center;">
  <img src="../images/piezo_sensor.jpeg" style="width:40%;">
</div>

---


# **Frequency Extraction Model**

**Implemented Elisabetta's sPLL in Brian2.**

- sPLL's TDE is silent only if perfect frequency match.

- All other sPLL fires many spikes.

---
# **Time Difference Encoder**
<p>
<img src="../images/tde_delta_paper.png" width=60% />
<img src="../images/tde_delta.png" width=60% />
</p>

---

# **No-match Frequencies (Input : 30Hz | CCO : 20Hz)**

<div style="display: flex; justify-content: center;">
  <img src="../images/non_match_pll.png" width=60%>
</div>

---

# **Matching Frequencies (20 Hz)**

<div style="display: flex; justify-content: center;">
  <img src="../images/match_pll.png" width=60%>
</div>

---


# **Matching Frequencies (20 Hz) with noise**

<div style="display: flex; justify-content: center;">
  <img src="../images/match_pll_noise.png" width=60%>
</div>

---

# **Improvement for a PLL**

- Decomposition in a selected bandwidth (neuromorphic cochlea).

- Spiking or bursting neuron with tunable bandwidth.


---

# **Processing Pathway**

Inspiration from Predictive Coding:


<div style="display: flex; justify-content: center;">
  <img src="../images/hierarchical_network.png" width=60%>
</div>

- Unclear how to implement in SNNs.

---

# **Predictive Coding Light**

Concrete implementation in SNNs.

<div style="display: flex; justify-content: center;">
  <img src="../images/pcl_network.png" width=50%>
</div>

---

# **Advantages of PCL**

- No residual errors propagation.

- Suppresses most predictable spikes.

- Concrete implementation in SNNs.

- Uses inhibitory STDP (online learning).

---

# **Functioning of PCL**

<div style="display: flex; justify-content: center;">
  <img src="../images/spike_suppression.png" width=40%>
</div>

---

# **Steps to implement PCL-like network**


- Simple SNN with STDP learning rule.

- Addition of inhibitory connections.

- Understand receptive fields for texture recognition.

- Derive appropriate network configuration for the task.

---

# **STDP Synapses**

<div style="display: flex; justify-content: center;">
  <img src="../images/stdp_schema.png" width=80%>
</div>

---

# **STDP Synapses**

<div style="display: flex; justify-content: center;">
  <img src="../images/stdp_theory.png" width=70%>
</div>

---

# **STDP Synapses Brian2**

<div style="display: flex; justify-content: center;">
  <img src="../images/stdp_time.png" width=70%>
</div>

---

# **STDP Synapses with LIF (Pre rate > Post rate)**

<div style="display: flex; justify-content: center;">
  <img src="../images/stdp_trace.png" width=60%>
</div>

---


# **C-STDP Synapses**

- More biologically plausible.

- Uses a single transient calcium trace.

- $\tau \frac{d\rho}{dt} = -\rho (1 - \rho)(\rho_* - \rho) + \gamma_p(1-\rho)\Theta(c(t)-\theta_p)\\ \\ - \gamma_d\rho\Theta(c(t)-\theta_d) + Noise(t)$

---


# **C-STDP Synapses**

<div style="display: flex; justify-content: center;">
  <img src="../images/c_stdp_time.png" width=60%>
</div>