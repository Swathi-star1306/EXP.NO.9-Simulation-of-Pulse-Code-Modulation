# EXP.NO.9-Simulation-of-Pulse-Code-Modulation
9.Simulation of PCM

# AIM
To simulate the process of Pulse Code Modulation (PCM) and observe the quantization, encoding, and reconstruction of a sampled analog signal.

# SOFTWARE REQUIRED
1. Python
2. Colab
   libraries: numpy, matplotlib

# ALGORITHMS
1. Start the program.

2. Initialize parameters like sampling rate, frequency of analog signal, duration, and number of quantization levels.

3. Generate time vector using the sampling rate and duration.

4. Create an analog message signal using a sine wave.

5. Generate a clock signal with a higher frequency to simulate the sampling clock.

6. Quantize the analog message signal using defined quantization levels.

7. Encode the quantized signal into digital form by converting amplitude values to integer levels (PCM).

8. Plot the message signal, clock signal, quantized (PCM) signal, and demodulated signal.

9. End the program.

# PROGRAM
```pythonimport matplotlib.pyplot as plt
import numpy as np

# Parameters
sampling_rate = 5000
duration = 0.1
quantization_levels = 16

# Time base
t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

# Two message signals
frequency1 = 50
frequency2 = 120
message_signal1 = np.sin(2 * np.pi * frequency1 * t)
message_signal2 = np.sin(2 * np.pi * frequency2 * t)

# Quantization function
def quantize(signal, levels):
    step = (max(signal) - min(signal)) / levels
    quantized = np.round(signal / step) * step
    pcm = ((quantized - min(quantized)) / step).astype(int)
    return quantized, pcm

# Quantize both signals
quantized_signal1, pcm_signal1 = quantize(message_signal1, quantization_levels)
quantized_signal2, pcm_signal2 = quantize(message_signal2, quantization_levels)

# Multiplexing the PCM signals by interleaving
multiplexed_pcm = np.empty((pcm_signal1.size + pcm_signal2.size,), dtype=int)
multiplexed_pcm[0::2] = pcm_signal1
multiplexed_pcm[1::2] = pcm_signal2

# Time base for multiplexed signal
t_mux = np.linspace(0, duration, multiplexed_pcm.size, endpoint=False)

# Clock signal for reference
clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))

# Plotting
plt.figure(figsize=(14, 12))

plt.subplot(8, 1, 1)
plt.plot(t, message_signal1, label="Message Signal 1 (50Hz)", color='blue')
plt.title("Original Message Signal 1")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)
plt.legend()

plt.subplot(8, 1, 2)
plt.plot(t, clock_signal, label="Clock Signal", color='green')
plt.title("Clock Signal")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)
plt.legend()

plt.subplot(8, 1, 3)
plt.step(t, quantized_signal1, label="Quantized Signal 1", color='red')
plt.title("Quantized Signal 1")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)
plt.legend()

plt.subplot(8, 1, 4)
plt.plot(t, message_signal2, label="Message Signal 2 (120Hz)", color='orange', alpha=0.7)
plt.title("Original Message Signal 2")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)
plt.legend()

plt.subplot(8, 1, 5)
plt.plot(t, clock_signal, label="Clock Signal", color='green')
plt.title("Clock Signal")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)
plt.legend()

plt.subplot(8, 1, 6)
plt.step(t, quantized_signal2, label="Quantized Signal 2", color='purple', alpha=0.7)
plt.title("Quantized Signal 2")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)
plt.legend()

plt.subplot(8, 1, 7)
plt.step(t, quantized_signal1, label="Quantized Signal 1", color='red')
plt.step(t, quantized_signal2, label="Quantized Signal 2", color='purple', alpha=0.7)
plt.title("Overlay of Quantized Signals")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)
plt.legend()

plt.subplot(8, 1, 8)
plt.step(t_mux, multiplexed_pcm, label="Multiplexed PCM Signal", color='black')
plt.title("Multiplexed PCM Signal (Interleaved)")
plt.xlabel("Time [s]")
plt.ylabel("PCM Value")
plt.grid(True)
plt.legend()

plt.tight_layout()
plt.show()
)
```

# OUTPUT


**PULSE CODE MODULATION**

![image](https://github.com/user-attachments/assets/f42b952f-cf82-425e-8097-b53a7b4885e5)


 
# RESULT / CONCLUSIONS
The simulation of Pulse Code Modulation (PCM) was successfully performed. The analog signal was sampled, quantized, encoded into binary format, and reconstructed from the encoded data. The reconstructed signal closely followed the original analog input, validating the working of PCM.


