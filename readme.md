# ⚡ DC–DC Buck Converter (LM2596-ADJ)

This project demonstrates the design and development of a **DC–DC Buck Converter** using the **LM2596 Adjustable Regulator IC**.  
The converter efficiently steps down a higher DC voltage (9–24 V) to a lower, regulated DC voltage (~7.38 V).  
It is designed, simulated, and implemented as a **2-layer PCB** using **KiCad**.

---

## 🧭 1. Introduction
A **Buck Converter** (step-down converter) is a type of **switching voltage regulator** that reduces the input voltage to a desired lower output voltage while maintaining high efficiency.  
It uses an **inductor, a switching transistor (inside LM2596), a diode**, and **filter capacitors** to convert DC levels efficiently.

Unlike linear regulators, which dissipate excess voltage as heat, the buck converter stores and transfers energy using an inductor and switching control, achieving efficiencies of **80–90%**.

---

## 🧱 2. Block Diagram

```mermaid
graph LR
A[Input Terminal] --> B[Fuse & Reverse Diode Protection]
B --> C[Input Filter Capacitor]
C --> D[LM2596 Adjustable Regulator IC]
D --> E[Inductor (L1)]
E --> F[Schottky Diode (D2)]
F --> G[Output Filter Capacitor]
G --> H[Feedback Network (R1, R2)]
H --> I[Output Terminal + LED Indicator]

G --> H[OUTPUT Connector]
