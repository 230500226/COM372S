# Receivers Lab: Superheterodyne Receiver MATLAB Analysis & Explanations

---

## 1. Effect of Increase in Signal Input Power on Output Power, Noise Figure, and Intermodulation Product

### MATLAB Code

```matlab
% Define receiver elements as in the main section
elements(1) = rfelement('Name', 'TRSwitch', 'Gain', -1.3, 'NF', 2.3, 'OIP3', 37);
Fcenter = 5.8e9;
Bwpass = 20e6;
Z = 132.986;
elements(2) = rffilter('ResponseType', 'Bandpass', 'FilterType', 'Butterworth', 'FilterOrder', 6, ...
    'PassbandAttenuation', 10*log10(2), 'Implementation', 'Transfer function', ...
    'PassbandFrequency', [Fcenter-Bwpass/2 Fcenter+Bwpass/2], 'Zout', 50, 'Name', 'RF_Filter');
elements(3) = amplifier('Name', 'LNA', 'Gain', 15, 'NF', 1.5, 'OIP3', 26, 'Zin', Z);
elements(4) = amplifier('Name', 'Gain', 'Gain', 10.5, 'NF', 3.5, 'OIP3', 23);
elements(5) = modulator('Name', 'Demod', 'Gain', -7, 'NF', 7, 'OIP3', 15, 'LO',5.4e9, 'ConverterType', 'Down');
FcenterIF = 400e6;
BwpassIF = 5e6;
elements(6) = rffilter('ResponseType', 'Bandpass', 'FilterType', 'Butterworth', 'FilterOrder', 4, ...
    'PassbandAttenuation', 10*log10(2), 'Implementation', 'Transfer function', ...
    'PassbandFrequency', [FcenterIF-BwpassIF/2 FcenterIF+BwpassIF/2], 'Zout',50, 'Name', 'IF_Filter');
elements(7) = amplifier('Name', 'IFAmp', 'Gain', 40, 'NF', 2.5, 'Zin',Z);
elements(8) = amplifier('Name', 'AGC', 'Gain', 17.5, 'NF', 4.3, 'OIP3', 36);

% Vary input power
input_powers = [-66, -56, -46]; % dBm, example values for low, medium, high input power

% Store results
results = struct();

for i = 1:length(input_powers)
    superhet = rfbudget('Elements', elements, ...
        'InputFrequency', 5.8e9, ...
        'AvailableInputPower', input_powers(i), ...
        'SignalBandwidth', 20e6);

    % Collect Output Power, Noise Figure, OIP3 at output
    results(i).InputPower = input_powers(i);
    results(i).OutputPower = superhet.OutputPower(end); % dBm
    results(i).NoiseFigure = superhet.NoiseFigure(end); % dB
    results(i).OIP3 = superhet.OIP3(end); % dBm
end

% Display results
disp(struct2table(results))
```

### Explanation

- **Increasing Input Power:** As you increase the signal input power (`AvailableInputPower`), the output power of the receiver chain also increases linearly up to the linear region of the amplifiers. However, if the input power is high enough to drive the receiver near or beyond the 1dB compression point or OIP3 of any stage, nonlinearity and distortion increase.
    - **Output Power (dBm):** Increases with input power until saturation/compression is reached.
    - **Noise Figure (dB):** Remains largely unchanged, as NF is a property of the receiver chain, not the input signal level.
    - **Output Intermodulation Product (OIP3):** The OIP3 value itself (in dBm) remains the same (it's a device property), but the actual observed intermodulation products at the output increase with higher input power, as they are proportional to input power and device nonlinearity.
- **MATLAB Workflow:** The code loops over several input power levels, runs `rfbudget`, and records output power, noise figure, and OIP3 at the output. Observing the table shows the trends above.

---

## 2. Influence of Filter Order on Output Power and Noise Figure

### MATLAB Code

```matlab
filter_orders = [2, 4, 6, 8]; % Example filter orders to test
results_order = struct();

for i = 1:length(filter_orders)
    % Only change the order of the RF filter (element 2)
    elements(2) = rffilter('ResponseType', 'Bandpass', 'FilterType', 'Butterworth', ...
        'FilterOrder', filter_orders(i), 'PassbandAttenuation', 10*log10(2), ...
        'Implementation', 'Transfer function', ...
        'PassbandFrequency', [Fcenter-Bwpass/2 Fcenter+Bwpass/2], 'Zout', 50, 'Name', 'RF_Filter');

    superhet = rfbudget('Elements', elements, ...
        'InputFrequency', 5.8e9, ...
        'AvailableInputPower', -66, ...
        'SignalBandwidth', 20e6);

    results_order(i).FilterOrder = filter_orders(i);
    results_order(i).OutputPower = superhet.OutputPower(end);
    results_order(i).NoiseFigure = superhet.NoiseFigure(end);
end

disp(struct2table(results_order))
```

### Explanation

- **Changing Filter Order:**
    - **Higher Filter Order:** Increases selectivity (sharper roll-off), but also increases insertion loss and can degrade the noise figure (since loss before amplification counts directly against NF).
    - **Output Power:** May decrease with higher order, due to greater insertion loss.
    - **Noise Figure:** Increases with higher order for the same reason.
- **Filter Location Matters:** 
    - **Early in Chain:** Losses before the first amplifier (LNA) have the greatest negative impact on overall system noise figure (Friis formula).
    - **Later in Chain:** Losses after amplification have less effect on NF but still reduce output power.
- **MATLAB Workflow:** The code varies the order of the RF filter (element 2) and displays the effect on output power and noise figure.

---

## 3. Performance Parameters for Low OIP3 Values

### Explanation

- **OIP3 (Output Third-Order Intercept Point):** Lower OIP3 values mean the device is more nonlinear (worse linearity).
- **To Achieve Low OIP3 (i.e., more distortion, NOT desirable for most receivers):**
    - **Low Power Handling:** Use devices rated for low output power.
    - **High Gain per Stage:** Sometimes, very high gain stages have lower OIP3.
    - **Poor Device Linearity:** Choose components (amplifiers, mixers) with poor linearity specs.
    - **Operating Close to Compression:** Run devices near their saturation/compression point (not recommended for normal operation).
    - **Filter Placement:** Placing lossy or nonlinear components before/after critical stages can also degrade OIP3.
- **Performance Parameter Set:**
    - Low OIP3 values in the `OIP3` field of amplifiers, switches, and modulators (e.g., 10–20 dBm).
    - High gain but poor linearity settings.
    - High insertion loss filters (not recommended in practice).
- **In MATLAB:**
    - Set `'OIP3'` arguments lower for amplifiers, switches, mixers:
    ```matlab
    elements(3) = amplifier('Name', 'LNA', 'Gain', 15, 'NF', 1.5, 'OIP3', 10, 'Zin', Z); % OIP3 lowered
    ```

---

## References

- [cite: 1]–[cite: 457]: As provided in the ReceiversLabInstructions document.
