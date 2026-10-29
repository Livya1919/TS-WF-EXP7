## Ex-07: Spectral Analysis, Spectral Density and Time-Invariant Linear Filters
## NAME : LIVYA DHARSHINI G
## REGISTER NUMBER : 23050001013
## Aim
To perform spectral analysis on a simulated time series, identify dominant frequencies using a
periodogram, apply a moving-average filter, and compare the spectral density before and after
filtering.
## Objectives
1. To generate a time series containing multiple frequencies and random noise.
  
2. To calculate and plot the periodogram.
   
3. To identify the dominant frequency in the time series.
   
4. To apply a moving-average linear filter.
   
5. To compare the original and filtered time series.
   
6. To study the effect of changing the signal frequency, filter window size, and noise.
    
7. To observe the effect of adding another frequency component.
    
## Program
```
import numpy as np
import matplotlib.pyplot as plt
from scipy import signal
np.random.seed(42)
n = 500
t = np.arange(n)

x = (
    np.sin(2 * np.pi * 0.05 * t)
    + 0.5 * np.sin(2 * np.pi * 0.20 * t)
    + 0.3 * np.random.randn(n)
)

plt.figure(figsize=(10, 4))
plt.plot(t, x)
plt.title('Simulated Time Series')
plt.xlabel('Time')
plt.ylabel('X(t)')
plt.grid(True)
plt.tight_layout()
plt.show()
frequency, power = signal.periodogram(x)

plt.figure(figsize=(10, 4))
plt.plot(frequency, power)
plt.title('Periodogram / Estimated Spectral Density')
plt.xlabel('Frequency')
plt.ylabel('Power')
plt.grid(True)
plt.tight_layout()
plt.show()

peak_index = np.argmax(power)
dominant_frequency = frequency[peak_index]
print('Dominant frequency:', round(dominant_frequency, 4))
window = 5
filtered = np.convolve(x, np.ones(window) / window, mode='same')

plt.figure(figsize=(10, 4))
plt.plot(t, x, label='Original', alpha=0.8)
plt.plot(t, filtered, label='Filtered', linewidth=2)
plt.title('Original vs Filtered Time Series')
plt.xlabel('Time')
plt.ylabel('Value')
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()
f_original, p_original = signal.periodogram(x)
f_filtered, p_filtered = signal.periodogram(filtered)

plt.figure(figsize=(10, 4))
plt.plot(f_original, p_original, label='Original')
plt.plot(f_filtered, p_filtered, label='Filtered')
plt.title('Spectral Density Before and After Filtering')
plt.xlabel('Frequency')
plt.ylabel('Power')
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()

```
## Output

<img width="931" height="722" alt="image" src="https://github.com/user-attachments/assets/4c2dc26c-4423-4a82-89bf-951c904415d8" />

<img width="942" height="713" alt="image" src="https://github.com/user-attachments/assets/9f9c575c-4419-4f22-8d7a-45cc7d47a164" />



## Result

Spectral analysis was performed successfully using the periodogram to identify dominant
frequencies. A moving-average filter was applied to smooth the time series, and the spectral
density before and after filtering was compared. The effects of changing frequency, removing noise,
increasing the filter window, and adding another frequency component were studied.
