# RC Filter Design and Simulation (LTspice)

---

## 🧠 Objective

To design, derive, and simulate:
- Low-pass RC filter
- Band-pass filter (1 kHz to 10 kHz)

---

# 🔹 Low-Pass RC Filter

## Circuit Description
- Resistor (R) in series
- Capacitor (C) connected to ground
- Output taken across capacitor

---

## Step 1: Capacitor Impedance

Zc = 1 / (jωC)

---

## Step 2: Apply Voltage Divider

Vout = Vin × (Zc / (R + Zc))

---

## Step 3: Substitute Zc

Vout = Vin × [ (1 / jωC) / (R + (1 / jωC)) ]

---

## Step 4: Simplification

Multiply numerator and denominator by jωC:

Vout = Vin × [ 1 / (1 + jωRC) ]

---

## ✅ Transfer Function

H(jω) = Vout / Vin = 1 / (1 + jωRC)

---

## Cutoff Frequency

fc = 1 / (2πRC)

---

## Observations

- At low frequency → capacitor behaves like open circuit → output ≈ input  
- At high frequency → capacitor behaves like short circuit → output ≈ 0  
- Slope = -20 dB/decade  

---

# 🔹 Band-Pass Filter

## Design Concept

Band-pass filter is formed by cascading:

- High-pass filter (lower cutoff)
- Low-pass filter (upper cutoff)

---

## Requirements

- Lower cutoff frequency = 1 kHz  
- Upper cutoff frequency = 10 kHz  

---

## Step 1: High-Pass Transfer Function

H_HP(jω) = (jωRC) / (1 + jωRC)

---

## Step 2: Low-Pass Transfer Function

H_LP(jω) = 1 / (1 + jωRC)

---

## Step 3: Cascading (Proof)

Total transfer function:

H(jω) = H_HP × H_LP

---

## Step 4: Final Expression

H(jω) = [(jωR1C1) / (1 + jωR1C1)] × [1 / (1 + jωR2C2)]

---

## Design Values Used

| Component | Value |
|----------|------|
| R1 | 1kΩ |
| C1 | 0.159 µF |
| R2 | 1kΩ |
| C2 | 0.0159 µF |

---

## Observations

- Below 1 kHz → signal attenuated  
- Between 1 kHz and 10 kHz → signal passes  
- Above 10 kHz → signal attenuated  

---

## Key Insight

- Band-pass is achieved by removing:
  - Low frequencies using high-pass
  - High frequencies using low-pass  

- Overall response depends on:
  - Component values
  - Loading effects
  - Order of filter  

---

## Tools Used

- LTspice for simulation

---

## Files Included

- lowpass.asc  
- bandpass.asc  
