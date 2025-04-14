# EXP.NO.9-Simulation-of-Pulse-Code-Modulation
9.Simulation of PCM

## AIM
The aim of Pulse Code Modulation (PCM) is to convert an analog signal into a digital form by sampling, quantizing, and encoding it into binary format. This process ensures accurate transmission and storage of signals in digital systems. PCM enhances signal quality and error detection, making it crucial in audio, telecommunications, and multimedia applications.


## SOFTWARE REQUIRED
google colab or matplotlib python compiler

## ALGORITHMS

🔹 1. Sampling Algorithm
Purpose: Convert a continuous-time signal into discrete-time samples.
Choose a sampling frequency 

🔹 2. Quantization Algorithm
Purpose: Approximate sampled values to the nearest value within a finite set of levels.
Define the number of quantization levels 
Compute the quantization step size 
Find the nearest quantization level.
Replace the original value with the quantized value.

🔹 3. Encoding Algorithm
Purpose: Convert quantized levels into binary code.
Assign a unique binary code to each quantization level (usually using natural binary coding).
Determine its corresponding binary index.


## PROGRAM
```
import matplotlib.pyplot as plt
import numpy as np

# Parameters
sampling_rate = 5000  # Sampling rate (samples per second)
frequency = 50  # Frequency of the message signal (analog signal)
duration = 0.1  # Duration of the signal in seconds
quantization_levels = 16  # Number of quantization levels (PCM resolution)

# Generate time vector
t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

# Generate message signal (analog signal)
message_signal = np.sin(2 * np.pi * frequency * t)

# Generate clock signal (sampling clock) with higher frequency
clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))  # 200 Hz clock

# Quantize the message signal
quantization_step = (max(message_signal) - min(message_signal)) / quantization_levels
quantized_signal = np.round(message_signal / quantization_step) * quantization_step

# Simulate the PCM modulated signal (as quantized levels)
pcm_signal = (quantized_signal - min(quantized_signal)) / quantization_step
pcm_signal = pcm_signal.astype(int)

# Plotting the results
plt.figure(figsize=(12, 10))

# Plot message signal
plt.subplot(4, 1, 1)
plt.plot(t, message_signal, label="Message Signal (Analog)", color='blue')
plt.title("Message Signal (Analog)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

# Plot clock signal (higher frequency)
plt.subplot(4, 1, 2)
plt.plot(t, clock_signal, label="Clock Signal (Increased Frequency)", color='green')
plt.title("Clock Signal (Increased Frequency)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

# Plot PCM modulated signal (quantized)
plt.subplot(4, 1, 3)
plt.step(t, quantized_signal, where='mid', label="PCM Modulated Signal", color='red')
plt.title("PCM Modulated Signal (Quantized)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

# Plot 'PCM Demodulation' (just plotting the quantized signal again)
plt.subplot(4, 1, 4)
plt.plot(t, quantized_signal, label="Signal Demodulation", color='purple', linestyle='--')
plt.title("Signal Without Demodulation")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

plt.tight_layout()
plt.show()

```


## OUTPUT
 ![download](https://github.com/user-attachments/assets/86577064-0f94-4b14-b6c1-eab16530eaba)

## RESULT / CONCLUSIONS

Pulse Code Modulation (PCM) converts analog signals into digital form by sampling and quantizing the signal. The result is a series of pulses that represent the digitized version of the original signal, widely used in audio and telecommunications.
