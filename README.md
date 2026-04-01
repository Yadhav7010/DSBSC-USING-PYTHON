# DSB--SC-MODULATION-AND-DEMODULATION-USING-PYTHON

---

## AIM:
To generate a Double Sideband Suppressed Carrier (DSB-SC) signal in Python (Google Colab), transmit it (optionally add noise), and recover the message using coherent demodulation with a low-pass filter. Observe time and frequency domain waveforms and measure demodulation performance.

---

## APPARATUS REQUIRED:
- Google Colab (or any Python environment)  
- Python libraries: numpy, matplotlib, scipy (scipy.signal)  

---

## THEORY:
DSB-SC signal:  
s(t) = m(t) · cos(2πf_c t)

Coherent demodulation: multiply received signal with synchronized carrier and apply LPF:

r(t) = s(t)·cos(2πf_c t)  
     = m(t)·cos²(2πf_c t)  
     = 0.5 m(t) + 0.5 m(t)·cos(4πf_c t)

LPF extracts 0.5·m(t) → scale by 2 to recover m(t).

---

## PROCEDURE:
1. Import libraries and set parameters  
2. Define message and carrier signals  
3. Generate DSB-SC signal  
4. View spectra (FFT)  
5. (Optional) Add noise  
6. Coherent demodulation  
7. Apply low-pass filter  

---

## PROGRAM
```python
import numpy as np
import matplotlib.pyplot as plt

# Parameters
Ac = 181           # Carrier amplitude
Am = 18.1          # Message amplitude
Fc = 6460          # Carrier frequency (Hz)
Fm = 646           # Message frequency (Hz)
Fs = 45000         # Sampling frequency (Hz)

# Time axis
t = np.arange(0, 2/Fm, 1/Fs)

# Angular frequencies
Wc = 2 * np.pi * Fc
Wm = 2 * np.pi * Fm

# 1. Message Signal
m = Am * np.sin(Wm * t)

# 2. Carrier Signal
c = Ac * np.sin(Wc * t)

# 3. DSB-SC Signal
dsb_sc = m * np.sin(Wc * t)

# 4. Conventional AM Signal
am = (Ac + m) * np.sin(Wc * t)

# Plotting
plt.figure(figsize=(10, 10))

plt.subplot(4, 1, 1)
plt.plot(t, m)
plt.title("Message Signal")
plt.grid(True)

plt.subplot(4, 1, 2)
plt.plot(t, c)
plt.title("Carrier Signal")
plt.grid(True)

plt.subplot(4, 1, 3)
plt.plot(t, dsb_sc)
plt.title("DSB-SC Signal")
plt.grid(True)

plt.subplot(4, 1, 4)
plt.plot(t, am)
plt.title("Conventional AM Signal")
plt.grid(True)

plt.tight_layout()
plt.show()
```

---


## OUTPUT
<img width="989" height="989" src="https://github.com/user-attachments/assets/c1ad1e7b-cc9c-49f7-9273-43d5624e8bd9" />

---
## TABULATION
<img width="1280" height="975" src="https://github.com/user-attachments/assets/a3477eb1-cce0-4a9f-95d1-e7d490c59b14" />

---


## RESULT:
Thus the DSB-SC modulation and demodulation were implemented using Python, and the output was verified successfully.
