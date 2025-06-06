# AM Modulation and Spectrum Analysis

This document provides a step-by-step guide to perform AM modulation and analyze the spectrum using MATLAB.

## Steps

1. Set the sampling frequency and time vector:
    
    ```matlab
    fs = 100;
    t = 0:1/fs:100;
    t = sin(2*pi*t);
    ```

2. Define the carrier frequency and message signal:

    ```matlab
    Car_frq = 10;
    Msg_sig = sin(2*pi*t);
    ```

3. Perform AM modulation and single sideband modulation:

    ```matlab
    AM_sing = ammod(Msg_sig, Car_frq, fs);
    AM_doub = ssbmod(Msg_sig, Car_frq, fs);
    ```

4. Create and configure the Spectrum Analyzer:

    ```matlab
    Spectrum_Analyzer = spectrumAnalyzer(SampleRate=fs, PlotAsTwoSidedSpectrum=true, YLimits= [-50, 50]);
    ```

    The properties of `Spectrum_Analyzer` are as follows:
    ```
    Spectrum_Analyzer = 

      spectrumAnalyzer handle with properties:

                   InputDomain: 'time'
                  SpectrumType: 'power'
                      ViewType: 'spectrum'
                    SampleRate: 100
                        Method: 'filter-bank'
        PlotAsTwoSidedSpectrum: 1
                FrequencyScale: 'linear'
                      PlotType: 'line'
                   AxesScaling: 'manual'

      Show all properties
    ```

5. Plot the message signal on the Spectrum Analyzer:

    ```
    Spectrum_Analyzer(AM_sing);
    Error using dsp.webscopes.internal.BaseWebScope/validateInputs
    Too many input channels. The maximum number of channels allowed is
    100.

    Error in dsp.webscopes.internal.BaseWebScope/setup

    Error in dsp.webscopes.internal.BaseWebScope/step

    Error in ()
    ```

6. Transpose the message signal to correct the input dimensions and plot again:

    ```matlab
    Spectrum_Analyzer(AM_sing');
    ```

The output:

![The AM ssb](https://github.com/230500226/COM372S/blob/main/AmSing.png?raw=true)
