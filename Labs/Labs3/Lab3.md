# Lab 3: Frequency Modulation (FM) Analysis with Spectrum Analyzer

## Objective
The objective of this lab is to analyze the process of frequency modulation (FM), noise corruption, and demodulation using MATLAB. The Spectrum Analyzer tool is used to visualize the signals at different stages in the frequency domain.

---

## MATLAB Code

```matlab
% Lab 3: Frequency Modulation Analysis with Spectrum Analyzer

% Clear workspace and command window
clear all;
close all;
clc;

% Parameters
fs = 100; % Sampling frequency in Hz
t = 0:1/fs:100; % Time vector (1 second duration)
t = sin(2*pi*t);
Carrier_frequency = 10; % Carrier frequency in Hz
frequency_deviation = 40; % Frequency deviation
initial_phase = 20; % Initial phase in degrees

% Message Signal
Message_signal = sin(2*pi*1*t)'; % Sine wave as the message signal (transpose to ensure column vector)

% FM Modulation
FM_signal = fmmod(Message_signal, Carrier_frequency, fs, frequency_deviation, initial_phase);

% Add Noise to FM Signal
SNR = 12; % Signal-to-Noise Ratio in dB
noise_signal_FM = awgn(FM_signal, SNR, 'measured');

% FM Demodulation
FM_demodulated_signal = fmdemod(noise_signal_FM, Carrier_frequency, fs, frequency_deviation, initial_phase);

% Spectrum Analyzer Instances
spectrum_Message = spectrumAnalyzer('SampleRate', fs, 'PlotAsTwoSidedSpectrum', false, 'YLimits', [-60, 50]);
spectrum_FM = spectrumAnalyzer('SampleRate', fs, 'PlotAsTwoSidedSpectrum', false, 'YLimits', [-60, 50]);
spectrum_Noise = spectrumAnalyzer('SampleRate', fs, 'PlotAsTwoSidedSpectrum', false, 'YLimits', [-60, 50]);
spectrum_Demodulated = spectrumAnalyzer('SampleRate', fs, 'PlotAsTwoSidedSpectrum', false, 'YLimits', [-60, 50]);

% Display Message Signal Spectrum
disp('Displaying Message Signal Spectrum...');
spectrum_Message(Message_signal);

% Display FM Modulated Signal Spectrum
disp('Displaying FM Modulated Signal Spectrum...');
spectrum_FM(FM_signal);

% Display Noise Corrupted FM Signal Spectrum
disp('Displaying Noise Corrupted FM Signal Spectrum...');
spectrum_Noise(noise_signal_FM);

% Display Demodulated Signal Spectrum
disp('Displaying Demodulated Signal Spectrum...');
spectrum_Demodulated(FM_demodulated_signal);
```

---

## Explanation of Code

### Parameters
1. **Sampling Frequency (`fs`)**:
   - The sampling frequency is set to 100 Hz to ensure accurate signal representation.
2. **Time Vector (`t`)**:
   - A sinusoidal time vector is created to represent the signal over 100 seconds.
3. **Carrier Frequency, Frequency Deviation, and Initial Phase**:
   - These parameters define the FM carrier characteristics.

### Signal Processing
1. **Message Signal**:
   - A sine wave is created as the baseband message signal.
2. **FM Modulation**:
   - The `fmmod` function modulates the message signal using frequency modulation.
3. **Noise Addition**:
   - White Gaussian noise is added to the FM signal to simulate real-world channel corruption.
4. **FM Demodulation**:
   - The `fmdemod` function retrieves the original message signal from the noisy FM signal.

### Visualization
1. **Spectrum Analyzer**:
   - MATLAB's `spectrumAnalyzer` tool is used to visualize the frequency domain representation of each signal.
   - Four separate Spectrum Analyzer instances are created to display:
     - The original message signal.
     - The FM modulated signal.
     - The noise corrupted FM signal.
     - The demodulated signal.

---

## Results

The script generates four Spectrum Analyzer windows:
1. **Message Signal**:
   - Displays the frequency-domain representation of the original message signal.
2. **FM Modulated Signal**:
   - Shows the frequency-domain spectrum of the modulated FM signal.
3. **Noise Corrupted FM Signal**:
   - Visualizes the FM signal after being corrupted by noise.
4. **Demodulated Signal**:
   - Displays the recovered message signal after demodulation.
  
![lab3](https://github.com/user-attachments/assets/1488222b-8032-4452-9227-f48f94a0d7fb)


---

## Conclusion

This lab demonstrates the complete process of frequency modulation, noise corruption, and demodulation. The Spectrum Analyzer tool effectively highlights the spectral characteristics of the signals at different stages.
