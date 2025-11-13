# Smart Passive Battery Management System (BMS) – Simulink Model

## 📌 Overview
This project implements a **Smart Passive Battery Management System (BMS)** using MATLAB Simulink.  
It simulates a **6-cell Li-ion battery pack** with:
- SOC estimation using **Coulomb counting**
- Voltage modeling via **OCV(SOC) curve + internal resistance**
- **Thermal dynamics** using a first-order heat model
- **Passive cell balancing** using bleed resistors
- Mean-voltage comparison + hysteresis logic
- Graphical outputs for **Voltage, SOC, Temperature, and BalCmd**

The model is fully discrete and designed for academic understanding of BMS behavior.

---

## ⚡ Features
- 🧮 **Accurate Cell Modeling**
  - Open-Circuit Voltage lookup table  
  - Internal resistance drop  
  - Cell-wise SOC integrators  
  - Temperature rise using α-based thermal model

- 🔋 **Passive Balancing Implementation**
  - Automatic detection of over-voltage cells  
  - Discharge through simulated resistor (Rbal)  
  - Balancing command Demux for all 6 cells  

- 📊 **Visualization Scopes**
  - `Plot_V` – Cell voltages  
  - `Plot_SOC` – State of Charge  
  - `Plot_T` – Temperature  
  - `Plot_BalCmd` – Balancing activity  

- 🧠 **Balancing Logic**
  - Computes pack mean voltage  
  - Applies hysteresis thresholds (dV_on, dV_off)  
  - Ensures stable balancing without oscillation  

---

## 🏗️ System Architecture (High-Level)
Ipack -----> [Cell Models × 6] -----> Voltage Vector -----> Mean_V
| | | |
Tamb SOC, T Balancing Logic <----|
BalCmd -----> Bleed Paths
