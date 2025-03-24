# Filters Class 05
05-03-2025

### Filters
- Usually required by an ampllifier for a desired clear output signal
- Amplitude of a ceratin desired frequency is increased and the rest are attenuated (decreased)

### Types of Filters
- Low Pass Filter (main)
    - Allows low frequencies to pass through
- High Pass Filter (main)
    - Allows high frequencies to pass through
- Band Pass Filter (main)
    - Allows a certain band of frequencies to pass through
- Band Stop Filter - TV (colors)
    - notch filter

### Passive Filters vs Active Filters - (applies for all tupes of filters)
- Passive filters 
    - no power source, or amplification
- Active filters
    - require power source, or amplification

### Cut off Frequency - Fc
- Indicated in ther filter data sheet
- Low pass filter
    - Frequencies below Fc are passed through
- High pass filter
    - Frequencies above Fc are passed through
- Band pass filter
    - Frequencies between Fc1 (lower fc) and Fc2 (upper fc) are passed through

### Frequency Response
- Graph of the filter's output amplitude vs frequency
- behaviour of the filter at different frequencies

### Filtes components
- Resistors
- Capacitors
- Inductors

- Inductance, resistance, and capacitance are the main components of filters that can be changed to change the filter's behaviour
    - can be dynamic or fixed

### Tune circuit 
- Change the values of the components to change the filter's behaviour
- Frequency slective circuit
- Use Q factor
    - Q = Fc / BW
    - Energy stored vs energy dissipated in the circuit or component
    - Ideal Q = infinity

    - Factors that decrease Q factor
        - (also from large soldering joints)
        - Radiation
        - Absorption
        - inductance
        - Mounting capacitance

### Circuit analysis, formulas
- Inductive
    - when the inductance is high, the capacitive reactance is low
- Capacitive
    - when the capacitance is high, the inductive reactance is low
- Resonant frequency
    - when the inductive reactance is equal to the capacitive reactance
    - Fc = 1 / 2 * pi * sqrt(L * C)
- Voltage divider
    - formula 
        - Vout = Vin * (Z2 / (Z1 + Z2))
- Impedance
    - Z = sqrt(R^2 + (Xl - Xc)^2)
    - Xl = 2 * pi * F * L
    - Xc = 1 / (2 * pi * F * C)
- Bandwidth
    - BW = Fc2 - Fc1
- Filters peak output
    - Q =  Fr/ BW

### Passband
- Frequencies that are passed through the filter
- High pass filter
    - Frequencies above the cut off frequency
- Low pass filter
    - Frequencies below the cut off frequency
- Band pass filter
    - Frequencies between the lower and upper cut off frequencies

### Stockband
- Frequencies that are blocked by the filter
- High pass filter
    - Frequencies below the cut off frequency
- Low pass filter
    - Frequencies above the cut off frequency
- Band pass filter
    - Frequencies outside the lower and upper cut off frequencies

### Transistion and filter roll off
- Transition
    - The range of frequencies between the passband and the stockband
    - Ideal transition is immediate
- Roll off
    - The rate at which the filter attenuates the frequencies outside the passband
    - Ideal roll off is infinite
- Ideal is not possible due to switching time of capactiors

### Filter type examples
- Butterworth
    - Maximally flat response
    - No ripples in the passband
    - Slow roll off
    - roll off is -20 dB/decade
- Chebyshev
    - Ripple in the passband
    - Fast roll off
    - rapid roll off rate exceeding -20 dB/decade
- Bessel
    - Linear phase response
    - Slow roll off

### Crystal filters
- High Q factor
- Store more energy, low energy waste

## Notes
- Wide bandwidth
    - high noise
- Narrow bandwidth
    - low noise


    - Filters block or attenduate undesired frequencies
    - Draw the band pass filter - frequent question (in FIsa not test)

