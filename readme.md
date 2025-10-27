---

## 🧭 Introduction
A **buck converter** is a type of **DC–DC switching regulator** that efficiently steps down a higher voltage to a lower voltage.  
Unlike linear regulators that waste power as heat, a buck converter uses **high-frequency switching** to achieve high efficiency (up to 90%).  

The **LM2596-ADJ** is a monolithic integrated circuit that provides all active functions for a step-down (buck) switching regulator.  
It can drive a 3A load with excellent line and load regulation.  
This project demonstrates the design, simulation, and PCB implementation of a **DC–DC Buck Converter** capable of stepping down **9–24V DC** input to a regulated **7.38V output**.


---

## 🧩 Components
| Component | Value / Part No | Description |
|------------|----------------|-------------|
| LM2596S-ADJ | — | Regulator IC |
| L1 | 100 µH | Power inductor |
| D2 | 1N5822 | Schottky diode |
| C1 | 100 µF / 35V | Input capacitor |
| C2, C3 | 220 µF / 100 µF | Output capacitors |
| R1, R2 | 10kΩ / 2kΩ | Feedback resistors |
| D3 | LED | Output indicator |
| R3 | 470Ω | LED resistor |
| Fuse | 1A | Input protection |

---

## ⚙️ Block Diagram
```mermaid
graph LR
A[INPUT Connector] --> B[Fuse & Reverse Diode Protection]
B --> C[Input Filter Circuit]
C --> D[LM2596 Buck Converter IC]
D --> E[Inductor]
E --> F[Output Filter]
F --> G[LED Indicator]
G --> H[OUTPUT Connector]


## ⚙️ Working Principle
The LM2596 operates based on **Pulse Width Modulation (PWM)**.  
It continuously switches the internal transistor **ON and OFF** at a frequency of around **150 kHz**.  

- **When the switch is ON:**  
  Current flows from the input through the inductor (L1), storing energy in its magnetic field.

- **When the switch is OFF:**  
  The inductor releases the stored energy through the **Schottky diode (D2)** to the **output capacitor (C2)** and **load**, maintaining a stable output voltage.

The **feedback resistors (R1 and R2)** divide the output voltage and feed it back to the feedback pin of the IC to regulate the duty cycle.  
This maintains a constant output voltage regardless of variations in load or input.

### 📘 Output Voltage Formula:
\[
V_{OUT} = 1.23 \times \left(1 + \frac{R1}{R2}\right)
\]

Using R1 = 10 kΩ and R2 = 2 kΩ:
\[
V_{OUT} = 1.23 \times (1 + 5) = 7.38V
\]

---

## ⚡ Input and Output Specifications

| Parameter | Symbol | Typical Value | Remarks |
|------------|---------|----------------|----------|
| Input Voltage | VIN | 9 – 24 V DC | Recommended operating range |
| Output Voltage | VOUT | 7.38 V DC | Adjustable via R1, R2 |
| Output Current | IOUT | Up to 1 A | Based on thermal design |
| Efficiency | η | 80–90% | Depends on load |
| Switching Frequency | fSW | 150 kHz | Fixed internal frequency |
| Operating Temperature | — | 0°C to +125°C | Standard operating limit |

---

## 🧮 Inductor Selection Equation

The inductor value determines output current ripple and converter stability.

\[
L = \frac{V_{OUT} \times (V_{IN} - V_{OUT})}{V_{IN} \times f_{SW} \times \Delta I_L}
\]

Where:  
- \( V_{IN} \) = Input voltage  
- \( V_{OUT} \) = Output voltage  
- \( f_{SW} \) = Switching frequency (150 kHz)  
- \( \Delta I_L \) = Inductor ripple current (typically 20–40% of IOUT)

For best performance, select an inductor with:  
- **Saturation current ≥ 1.5 × IOUT**  
- **Low DCR (resistance)** to minimize losses  

In this design:  
L = 100 µH provides stable operation and low ripple.

---

## 🧪 Testing Procedure

1. **Input Setup:**  
   Connect a regulated DC power supply (e.g., 12 V) to the input terminal.

2. **Output Measurement:**  
   Use a multimeter to measure output voltage at the output terminal.  
   - Expected Output ≈ **7.38 V DC**

3. **Load Testing:**  
   Attach a resistive load (e.g., 10 Ω, 1 A) and monitor voltage regulation.  
   - The output should remain within ±3% of the nominal value.

4. **Ripple Verification:**  
   Observe the output waveform on a CRO (oscilloscope).  
   - Verify minimal voltage ripple (typically <50 mVpp).

5. **LED Indicator:**  
   The LED glows when output voltage is present — confirming proper operation.

6. **Thermal Check:**  
   Operate for 10–15 minutes under load; ensure LM2596 and inductor remain within safe temperature limits.

---
## 🔧 Features
- Input fuse and reverse polarity protection  
- Adjustable output via feedback resistors  
- LED output indicator  
- Compact 2-layer PCB in KiCad  
---

## 📐 PCB Design Overview

The PCB is designed as a **2-layer board** in **KiCad**, featuring:  
- Wide copper traces for high-current paths  
- Mounting holes for stability  
- Screw terminals for easy connections  
- Thermal relief pads around the regulator and diode  
- Input and output filtering placed close to the IC for noise reduction  

### 🧾 Schematic
![Schematic](schematic%20of%20pcb.png)

### 🖥️ PCB Layout
![PCB Layout](pcb%20layout%20design%20.png)

### ⚙️ PCB Front Face
![Front Face](front%20face%20of%20pcb.png)

### ⚙️ PCB Back Face
![Back Face](backphase%20pf%20pcb.png)

---

## 🧠 Conclusion
The designed **LM2596-based DC–DC Buck Converter** successfully steps down higher DC voltages to stable, lower voltages with high efficiency and minimal heat loss.  
This project demonstrates practical PCB design, component selection, and verification of a switching regulator — essential skills for embedded and power electronics engineering.

---

## 👨‍🔬 Author
**Nandeesh K. S**  
*Electronics and Communication Engineering*  
Dayananda Sagar Academy of Technology and Management  

📍 Bengaluru, India  
💡 Passionate about Embedded Systems, PCB Design, and Power Electronics.

---
