# Machine Learning Based Fault-Detection and Protection Method for Three-Phase Inverter

## Overview
This repository presents a **Research project** focused on **Real-time fault detection and protection of a three-phase Voltage Source Inverter (VSI)** using **Machine Learning and Residual current analysis**.

The work was carried out as part of an **International research-based project internship (Dec. 2025)** under the guidance of Kuntal Mandal, PhD - Research & Development Engineer, E-Powertrain, IDIADA Automotive Technology, 43710 - Santa Oliva (Tarragona), Spain. 
The objective of the project is to design a **robust, fast, and interpretable fault diagnosis framework** that overcomes the limitations of conventional threshold-based protection methods.

---

## Problem Statement
Three-phase inverters used in electric vehicles, motor drives, and renewable energy systems are vulnerable to **open-phase and short-circuit faults**, which can lead to severe hardware damage if not detected promptly.

Conventional protection techniques:
- Are sensitive to noise  
- Depend on fixed thresholds  
- Struggle under varying operating conditions  

This project addresses these challenges by integrating **Model-based residual generation** with **Machine learning–based fault classification** and **PWM shutdown logic**.

---

<p align="center">
  <img src="Model_Workflow.png" alt="ML-based fault detection workflow for three-phase inverter" width="750">
</p>
<p align="center">
  <em>Figure: Model workflow of residual current–based machine learning fault detection and PWM protection for a three-phase inverter.</em>
</p>

---
## System Architecture
The proposed framework consists of the following stages:

1. **Three-Phase VSI Modeling**
   - 2-level VSI with sinusoidal PWM
   - Balanced RL load
   - Implemented in MATLAB/Simulink

2. **Residual Current Generation**
   - Phase currents predicted using a discrete RL model
   - Residuals computed as the absolute difference between measured and predicted currents

3. **Feature Extraction**
   - Sliding window approach (20 ms window with 50% overlap)
   - Time-domain features: RMS, mean, peak, peak-to-peak, standard deviation, energy
   - Frequency-domain features: harmonic magnitudes and Total Harmonic Distortion (THD)

4. **Feature Normalization**
   - Mean–Mean-variance normalisation using training data statistics
   - Ensures consistent scaling for ML inference

5. **Machine Learning Classification**
   - Classification Tree (Fine Tree) model
   - Trained offline using labelled simulation data
   - Classes: Healthy, Open-phase fault, Short-circuit fault

6. **Fault Decision & PWM Protection**
   - Persistence counter to suppress false positives
   - Fault latching mechanism
   - PWM gate signals blocked upon confirmed fault

---

## Machine Learning Approach
- Model: **Classification Tree**
- Motivation:
  - Fast inference
  - Low computational complexity
  - Interpretable decision logic
- Training:
  - Offline training using residual-based features
  - 25% Holdout validation applied
- Deployment:
  - Exported to Simulink for real-time simulation

---

## Results
Simulation results demonstrate the effectiveness of the proposed approach:

- **Fault classification accuracy:** ~98–99% 
- **Fault types detected:** Healthy, Open-phase, Short-circuit
- **Protection response:** PWM shutdown triggered within 3 milliseconds after fault confirmation
- **Robustness:** Persistence logic reduces false tripping due to transient disturbances

These results validate the suitability of the framework for **real-time inverter protection applications**.

---

## Tools & Technologies
- MATLAB / Simulink  
- Machine Learning   
- Signal Processing  
- Power Electronics (VSI, PWM, RL modelling)

---

