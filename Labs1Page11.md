# Labs 1 Page 11

## Q0.1.1
- Critical Aspect and Reasoning 1
- Bandwidth Determination

### MATLAB code
```matlab
% Define the signal parameters
fs = 1000; % Sampling frequency
t = 0:1/fs:1-1/fs; % Time vector
f = 50; % Signal frequency
signal = sin(2*pi*f*t); % Original signal

% Modulate the signal using DSB and SSB
carrier_freq = 200; % Carrier frequency
dsb_modulated_signal = signal .* cos(2*pi*carrier_freq*t); % DSB modulation
ssb_modulated_signal = real(hilbert(signal) .* exp(1i*2*pi*carrier_freq*t)); % SSB modulation

% Calculate the bandwidth of the message signal prior to modulation
message_bandwidth = f - (-f);

% Calculate the bandwidth of the modulated signals
dsb_bandwidth = 2 * f;
ssb_bandwidth = f;

% Print the bandwidth results
fprintf('Message Signal Bandwidth: %d Hz\n', message_bandwidth);
fprintf('DSB Modulated Signal Bandwidth: %d Hz\n', dsb_bandwidth);
fprintf('SSB Modulated Signal Bandwidth: %d Hz\n', ssb_bandwidth);

% Plot the results
figure;
subplot(3,1,1);
plot(t, signal);
title('Original Message Signal');

subplot(3,1,2);
plot(t, dsb_modulated_signal);
title('DSB Modulated Signal');

subplot(3,1,3);
plot(t, ssb_modulated_signal);
title('SSB Modulated Signal');
```

From the signals presented in Figure 5 and Figure 6, we can determine the bandwidths as follows:

### Message Signal Bandwidth

Formula: 

$$
\beta = f_{\text{max}} - f_{\text{min}}
$$

Calculation: For a signal with frequency $f = 50$ Hz, the bandwidth is: 

$$
\beta_{\text{message}} = 50 - (-50) = 100 \text{ Hz}
$$

### Double Sideband (DSB) Modulated Signal Bandwidth

Calculation: DSB modulation transmits both upper and lower sidebands, so the bandwidth is: 

$$
\beta_{\text{DSB}} = 2 \times 50 = 100 \text{ Hz}
$$

### Single Sideband (SSB) Modulated Signal Bandwidth

Calculation: SSB modulation transmits only one sideband, so the bandwidth is: 

$$
\beta_{\text{SSB}} = 50 \text{ Hz}
$$

## Q0.1.1
- Critical Reasoning:
- Opinion on Power and Bandwidth Content

### MATLAB code
```matlab

% Opinion on Power and Bandwidth Content
opinion = """
The modulation process has a significant impact on both power and bandwidth content associated with the message signal.

For Double Sideband (DSB) modulation:
- The bandwidth of the DSB modulated signal is twice the bandwidth of the original message signal. This is because DSB modulation transmits both the upper and lower sidebands.
- The power consumption is higher in DSB modulation because both sidebands are transmitted, which requires more power.

For Single Sideband (SSB) modulation:
- The bandwidth of the SSB modulated signal is equal to the bandwidth of the original message signal. This is because SSB modulation transmits only one sideband (either upper or lower), effectively halving the bandwidth compared to DSB.
- The power consumption is lower in SSB modulation because only one sideband is transmitted, which requires less power.

In summary, SSB modulation is more efficient in terms of both power and bandwidth compared to DSB modulation. It reduces the required bandwidth by half and consumes less power by transmitting only one sideband.
""";

disp(opinion);
```

The modulation process has a significant impact on both power and bandwidth content associated with the message signal.

### Double Sideband (DSB) Modulation

**Bandwidth:** The bandwidth of the DSB modulated signal is twice the bandwidth of the original message signal because DSB modulation transmits both the upper and lower sidebands.

**Power Consumption:** Higher in DSB modulation because both sidebands are transmitted, requiring more power.

### Single Sideband (SSB) Modulation

**Bandwidth:** The bandwidth of the SSB modulated signal is equal to the bandwidth of the original message signal because SSB modulation transmits only one sideband, effectively halving the bandwidth compared to DSB.

**Power Consumption:** Lower in SSB modulation because only one sideband is transmitted, requiring less power.
