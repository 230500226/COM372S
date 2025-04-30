# Lab 3: Frequency Modulation (FM) Analysis and Visualization

## Objective
The aim of this lab is to analyze frequency modulation (FM) and demodulation with MATLAB and visualize the signals at various stages (modulated, noise corrupted, and demodulated) in a single plot with labeled lines.

---

## MATLAB Code

```matlab
% Lab 3: Frequency Modulation Analysis

% Clear workspace and command window
clear all;
close all;
clc;

% Parameters
fs = 100; % Sampling frequency in Hz
t = 0:1/fs:1; % Time vector (1 second duration)
Carrier_frequency = 10; % Carrier frequency in Hz
frequency_deviation = 40; % Frequency deviation
initial_phase = 20; % Initial phase in degrees

% Message Signal
Message_signal = sin(2*pi*t); % Sine wave as the message signal

% FM Modulation
FM_signal = fmmod(Message_signal, Carrier_frequency, fs, frequency_deviation, initial_phase);

% Add Noise to FM Signal
SNR = 12; % Signal-to-Noise Ratio in dB
noise_signal_FM = awgn(FM_signal, SNR, 'measured');

% FM Demodulation
FM_demodulated_signal = fmdemod(noise_signal_FM, Carrier_frequency, fs, frequency_deviation, initial_phase);

% Plot Results
figure;
plot(t, Message_signal, 'b', 'LineWidth', 1.5); hold on;
plot(t, FM_signal, 'r', 'LineWidth', 1.5);
plot(t, noise_signal_FM, 'g', 'LineWidth', 1.5);
plot(t, FM_demodulated_signal, 'k', 'LineWidth', 1.5);
hold off;

% Add Labels and Legend
xlabel('Time (s)');
ylabel('Amplitude');
title('Frequency Modulation Analysis');
legend('Message Signal', 'FM Signal', 'Noise Corrupted FM Signal', 'Demodulated Signal');
grid on;
```

---

## Explanation of Code

1. **Initialization**:
   - Clear workspace variables and set up parameters for sampling frequency, carrier frequency, and frequency deviation.
   - Create the time vector and define the message signal as a sine wave.

2. **FM Modulation**:
   - Use the `fmmod` function to modulate the message signal.

3. **Add Noise**:
   - Add white Gaussian noise to the FM signal using the `awgn` function, simulating a real-world noisy channel.

4. **FM Demodulation**:
   - Use the `fmdemod` function to recover the message signal from the noisy FM signal.

5. **Visualization**:
   - Plot all signals (message, FM modulated, noise corrupted, and demodulated) in a single figure with labels and a legend for clear interpretation.

---

## Results
The plot produced by the script will display:
- The original message signal (blue line).
- The FM modulated signal (red line).
- The noise corrupted FM signal (green line).
- The demodulated signal (black line).

This visualization allows for a direct comparison of the signals at different stages of communication.

![image](https://github.com/user-attachments/assets/9df554b5-b455-4d92-96cb-f041cb50aacb)
