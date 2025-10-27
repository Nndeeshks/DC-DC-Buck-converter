# ⚡ DC–DC Buck Converter (LM2596-ADJ)

This project implements a **DC–DC Buck Converter** using the **LM2596 adjustable regulator IC**.  
It efficiently steps down a higher DC voltage (9–24V) to a stable output (~7.38V).

---

## 🔧 Features
- Input fuse and reverse polarity protection  
- Adjustable output via feedback resistors  
- LED output indicator  
- Compact 2-layer PCB in KiCad  

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

