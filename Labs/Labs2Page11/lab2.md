# Lab 2: Frequency Modulation and Demodulation Analysis

Question: (critical Reasoning
Compare the results of the modulation and demodulation operation here with the
outputs gotten when you query MATLAB prompt with the command help modulator. What can you infer
from the response and how does this influence your design ?

---

## MATLAB Code

The MATLAB code below performs the following tasks:
1. Generates a message signal.
2. Modulates the message signal using `fmmod`.
3. Adds noise to the FM signal.
4. Demodulates the noisy FM signal using `fmdemod`.
5. Displays the help documentation for the `modulator` functions.
6. Compares the results with inference to the design influence

### MATLAB Script

```matlab
clear all
close all
clc

% Display the help documentation
help modulator

fs = 100; % Sampling frequency
t = 0:1/fs:1; % Time vector (1 second duration)
Carrier_frequency = 10; % Carrier frequency in Hz
frequency_deviation = 40; % Frequency deviation for FM
initial_phase = 20; % Initial phase of the carrier signal

% Generate the message signal
Message_signal = sin(2 * pi * t);

% Perform FM modulation
FM_signal = fmmod(Message_signal, Carrier_frequency, fs, frequency_deviation, initial_phase);

% add noise to the FM signal
SNR = 12; % Signal-to-Noise Ratio in dB
noise_signal_FM = awgn(FM_signal, SNR, 'measured');

% Perform FM demodulation
FM_demodulated_signal = fmdemod(noise_signal_FM, Carrier_frequency, fs, frequency_deviation, initial_phase);

%  Plot the results
figure;

subplot(3, 1, 1);
plot(t, Message_signal);
title('Original Message Signal');
xlabel('Time (s)');
ylabel('Amplitude');

subplot(3, 1, 2);
plot(t, FM_signal);
title('FM Modulated Signal');
xlabel('Time (s)');
ylabel('Amplitude');

subplot(3, 1, 3);
plot(t, FM_demodulated_signal);
title('Demodulated Signal');
xlabel('Time (s)');
ylabel('Amplitude');

```

---

## Results

### Graphs

1. **Original Message Signal**:

   ![msg](https://github.com/230500226/COM372S/blob/main/Labs/Labs2Page11/FMmsgSig.jpg?raw=true)
3. **FM Modulated Signal**:

   ![mod](https://github.com/230500226/COM372S/blob/main/Labs/Labs2Page11/FMmodSig.jpg?raw=true)
5. **Demodulated Signal**:

   ![demod](https://github.com/230500226/COM372S/blob/main/Labs/Labs2Page11/FMdemodSig.jpg?raw=true)
   
### Inference and design influence
 
  The effect of noise to the FM signal via the `awgn` introduces random distortions which affect the demodulated signal, this meant that the message signal and the demodulated signal was not exactly the same however it helped negate the affect of the noise had it not been modulated fiirstly.
  The higher the noise level (low snd) the more degradation to signal quality. When comparing the help modulator MATLABs command. This shows the built in modulation techniques (help documentation). From this I can infer that
  FM modulation is robust to noise, that make it suitable for broadcasting information where noise is expected but dealt with. When considering the design, the choice of modulation parameters like the carrier fre, frq deviation and others impact the sstems performance and bandwidth efficiency. Overall FM is a generally better than AM in key factors such as bandwidth efficiency and noise negation. 

---
