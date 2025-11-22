# DSB--SC-MODULATION-AND-DEMODULATION-USING-PYTHON

## AIM:

To generate a Double Sideband Suppressed Carrier (DSB-SC) signal in Python (Google Colab), transmit it (optionally add noise), and recover the message using coherent (synchronous) demodulation with a low-pass filter. Observe time and frequency domain waveforms and measure demodulation performance

## APPARATUS REQUIRED:

Google Colab (or any Python environment)

Python libraries: numpy, matplotlib, scipy (scipy.signal)

## Theory:

DSB-SC signal: s(t) = m(t) · cos(2πf_c t)
Coherent demodulation: multiply received s(t) by a synchronized carrier cos(2πf_c t) then low-pass filter (LPF) to remove double-frequency components:

r(t) = s(t)·cos(2πf_c t) = m(t)·cos²(2πf_c t) = 0.5 m(t) + 0.5 m(t)·cos(4πf_c t)
LPF extracts 0.5·m(t) → scale by 2 to recover m(t).

## Procedure:

1) Import libraries and set parameters
2) Define message and carrier signals
3) Generate DSB-SC signal (modulation)
4) View spectra (FFT) of message and DSB-SC
5) (Optional) Add noise
6) Coherent demodulation (multiply by synchronized carrier)
7) Low-pass filter to recover message

## Program:
```
import numpy as np
import matplotlib.pyplot as plt

Am=9.4
fm=510
Ac=18.8
fc=5100
fs=51000

t=np.arange(0, 3/fm, 1/fs)

m = Am*np.cos(2*3.14*fm*t)
plt.subplot(3,1,1)
plt.plot(t,m)

c = Ac*np.cos(2*3.14*fc*t)
plt.subplot(3,1,2)
plt.plot(t,c)

s1=(Ac+m)*np.cos(2*3.14*fc*t)
s2=(Ac-m)*np.cos(2*3.14*fc*t)

s=s1-s2
plt.subplot(3,1,3)
plt.plot(t,s)
```

## Tabulation:
![WhatsApp Image 2025-11-22 at 13 11 19_c1d93eb9](https://github.com/user-attachments/assets/b49deb45-bb03-42f7-a683-083c0158f4af)

## Output:
<img width="1080" height="802" alt="Screenshot 2025-11-16 220042" src="https://github.com/user-attachments/assets/8126fa1b-39ba-4c1e-8a2d-27f563d150dc" />


## Result:

Hence the DSB-SC is performed using python and output is verified
