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
```python
import matplotlib.pyplot as plt

import numpy as np

sampling_rate = 5000

frequency = 50

duration = 0.1

quantization_levels = 16

t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

message_signal = np.sin(2 * np.pi * frequency * t)

clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))

quantization_step = (max(message_signal) - min(message_signal)) / quantization_levels

quantized_signal = np.round(message_signal / quantization_step) * quantization_step

pcm_signal = (quantized_signal - min(quantized_signal)) / quantization_step

pcm_signal = pcm_signal.astype(int)

plt.figure(figsize=(12, 10))

plt.subplot(4, 1, 1)

plt.plot(t, message_signal, label="Message Signal (Analog)", color='blue')

plt.title("Message Signal (Analog)")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 2)

plt.plot(t, clock_signal, label="Clock Signal (Increased Frequency)", color='green')

plt.title("Clock Signal (Increased Frequency)")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 3)

plt.step(t, quantized_signal, label="PCM Modulated Signal", color='red')

plt.title("PCM Modulated Signal (Quantized)")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 4)

plt.plot(t, quantized_signal, label="Signal Demodulation", color='purple', linestyle='--')

plt.title("Signal Without Demodulation")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.tight_layout()

plt.show()
```

# OUTPUT


**PULSE CODE MODULATION**

![image](https://github.com/user-attachments/assets/f4c3c1db-7b07-4e72-ba15-888669e41022)

 
# RESULT / CONCLUSIONS
The simulation of Pulse Code Modulation (PCM) was successfully performed. The analog signal was sampled, quantized, encoded into binary format, and reconstructed from the encoded data. The reconstructed signal closely followed the original analog input, validating the working of PCM.


