# COM372S Formulas

## 1. Gain Formulas

### Formula 1.1: Gain in Decibels
$$ A_{db} = 10 \log_{10} \left( \frac{P_2}{P_1} \right) $$

#### Explanation:
- $A_{db}$: Gain in decibels (dB)
- $P_2$: Output power
- $P_1$: Input power

This formula calculates the gain in terms of power, where the gain is the ratio of the output power to the input power, expressed in decibels.

### Formula 1.2: Power in Terms of Voltage
$$ P = \frac{V^2}{R} $$

#### Explanation:
- $P$: Power
- $V$: Voltage
- $R$: Resistance

This formula relates the power to voltage and resistance. It shows that power is proportional to the square of the voltage divided by the resistance.

### Formula 1.3: Gain in Decibels (Voltage)
$$ A_{db} = 10 \log_{10} \left( \frac{V_2}{V_1} \right) $$

#### Explanation:
- $A_{db}$: Gain in decibels (dB)
- $V_2$: Output voltage
- $V_1$: Input voltage

This formula calculates the gain in terms of voltage, where the gain is the ratio of the output voltage to the input voltage, expressed in decibels.

## 2. Gain with Reference Input Power

### Formula 2.1: Gain with Reference to 1W
$$ A_{dbW} = 10 \log_{10} \left( \frac{P}{1W} \right) $$

#### Explanation:
- $A_{dbW}$: Gain in decibels (dB) with reference to 1 watt
- $P$: Power

This formula calculates the gain with the reference input power of 1 watt.

### Formula 2.2: Gain with Reference to 1mW
$$ A_{dbm} = 10 \log_{10} \left( \frac{P}{1mW} \right) $$

#### Explanation:
- $A_{dbm}$: Gain in decibels (dB) with reference to 1 milliwatt
- $P$: Power

This formula calculates the gain with the reference input power of 1 milliwatt.

## 3. Decibel as a Voltage

### Formula 3.1: Decibel Formula
$$ dB = 10 \log_{10} \left( \frac{P_2}{P_1} \right) $$

#### Explanation:
- $dB$: Decibels
- $P_2$: Output power
- $P_1$: Input power

This is the standard decibel formula used to express the ratio of two power levels.

### Derivation of Decibel as a Voltage

Given:
$$ P = \frac{V^2}{R} $$

Substitute for $P_2$ and $P_1$:

$$ dB = 10 \log_{10} \left( \frac{\frac{V_2^2}{R_2}}{\frac{V_1^2}{R_1}} \right) $$

Simplify the equation:

$$ dB = 10 \log_{10} \left( \frac{V_2^2}{V_1^2} \cdot \frac{R_1}{R_2} \right) $$

Separate into two logarithms:

$$ dB = 10 \log_{10} \left( \frac{V_2^2}{V_1^2} \right) + 10 \log_{10} \left( \frac{R_1}{R_2} \right) $$

Since $\log_{10} (x^2) = 2 \log_{10} (x)$:

$$ dB = 20 \log_{10} \left( \frac{V_2}{V_1} \right) + 10 \log_{10} \left( \frac{R_1}{R_2} \right) $$

### Formula 3.2: Decibel as a Voltage
$$ dB = 20 \log_{10} \left( \frac{V_2 \sqrt{R_1}}{V_1 \sqrt{R_2}} \right) $$

#### Explanation:
- $dB$: Decibels
- $V_2$: Output voltage
- $V_1$: Input voltage
- $R_1$: Input resistance
- $R_2$: Output resistance

This formula expresses the ratio of two voltage levels in decibels, taking into account the input and output resistances.

## 4. Modulation Index

### Formula 4.1: Modulation Index
$$ m = \frac{E_i}{E_c} $$

#### Explanation:
- $m$: Modulation index or modulation factor (ranges from 0 to 1 or can be expressed as a percentage)
- $E_i$: Amplitude of the modulating signal
- $E_c$: Amplitude of the carrier signal

This formula calculates the modulation index, which represents the ratio of the amplitude of the modulating signal to the amplitude of the carrier signal.

### Formula 4.2: Modulation Index from Peak-to-Peak Values
$$ m = \frac{B - A}{B + A} $$

#### Explanation:
- $m$: Modulation index or modulation factor
- $A$: Minimum peak-to-peak value
- $B$: Maximum peak-to-peak value

This formula calculates the modulation index using the minimum and maximum peak-to-peak values of the modulated signal.

## 5. AM (Amplitude Modulation) Formula

### Formula 5.1: Instantaneous Value of the AM Wave
$$ e_c = E_c \sin(\omega_c t) = E_c (1 + m \sin(\omega_i t)) \sin(\omega_c t) $$

#### Explanation:
- $e_c$: Instantaneous value of the carrier signal
- $E_c$: Maximum peak value of the carrier signal when unmodulated
- $\omega_c$: Angular frequency of the carrier signal
- $t$: Time
- $m$: Modulation index or modulation factor
- $\omega_i$: Angular frequency of the modulating signal

This formula represents the amplitude modulation (AM) of a carrier signal. The term $E_c \sin(\omega_c t)$ represents the unmodulated carrier signal, while $E_c (1 + m \sin(\omega_i t)) \sin(\omega_c t)$ represents the modulated carrier signal where the amplitude varies according to the modulating signal.

### Formula 5.2: Trigonometric Identity
$$ \sin(A) \sin(B) = \frac{1}{2} [\cos(A - B) - \cos(A + B)] $$

#### Explanation:
This trigonometric identity is used to simplify the product of two sine functions into a sum of cosine functions.

### Formula 5.3: AM Wave with Sidebands
Using the trigonometric identity in the AM formula:

$$ e = E_c \sin(\omega_c t) + \frac{m E_c}{2} \cos((\omega_c - \omega_i)t) - \frac{m E_c}{2} \cos((\omega_c + \omega_i)t) $$

#### Explanation:
- $e$: Instantaneous value of the AM wave
- $E_c$: Maximum peak value of the carrier signal when unmodulated
- $\omega_c$: Angular frequency of the carrier signal
- $m$: Modulation index or modulation factor
- $\omega_i$: Angular frequency of the modulating signal

This formula represents the AM wave as a combination of the carrier signal, the upper sideband (frequency $f_c + f_i$), and the lower sideband (frequency $f_c - f_i$). The first term $E_c \sin(\omega_c t)$ is the carrier signal, the second term $\frac{m E_c}{2} \cos((\omega_c - \omega_i)t)$ is the upper sideband, and the last term $-\frac{m E_c}{2} \cos((\omega_c + \omega_i)t)$ is the lower sideband.

### Formula 5.4: Side Frequency Amplitude
$$ E_{sf} = \frac{m E_c}{2} $$

#### Explanation:
- $E_{sf}$: Amplitude of the side frequency
- $m$: Modulation index or modulation factor
- $E_c$: Maximum peak value of the carrier signal when unmodulated

This formula calculates the amplitude of the side frequencies in an amplitude modulated wave.

## 6. Variants of AM (Amplitude Modulation)

### Double Sideband Suppressed Carrier (DSB-SC)
- Equation:
 $$ e_{DSB-SC} = E_m \cos(\omega_i t) \cos(\omega_c t) $$
- Performance: Efficient in terms of power, as the carrier is suppressed.
- Bandwidth Efficiency: Uses twice the bandwidth of the modulating signal.
- Power Efficiency: Higher than standard AM as no power is wasted on the carrier.

### Single Sideband Full Carrier (SSB-FC)
- Equation:
 $$ e_{SSB-FC} = E_c \cos(\omega_c t) + \frac{m E_c}{2} \cos((\omega_c + \omega_i)t) $$
- Performance: More efficient than DSB-SC but retains the carrier.
- Bandwidth Efficiency: Uses half the bandwidth of DSB-SC.
- Power Efficiency: Better than DSB-SC and standard AM as it eliminates one sideband.

### Single Sideband Suppressed Carrier (SSB-SC)
- Equation:
 $$ e_{SSB-SC} = \frac{m E_c}{2} \cos((\omega_c + \omega_i)t) $$
- Performance: Most power-efficient variant.
- Bandwidth Efficiency: Uses half the bandwidth of DSB-SC.
- Power Efficiency: Highest among all AM variants as both one sideband and the carrier are suppressed.

### Double Sideband Full Carrier (DSB-FC)
- Equation:
 $$ e_{DSB-FC} = E_c \cos(\omega_c t) + \frac{m E_c}{2} \cos((\omega_c - \omega_i)t) - \frac{m E_c}{2} \cos((\omega_c + \omega_i)t) $$
- Performance: Standard AM, simple to implement but less power-efficient.
- Bandwidth Efficiency: Uses twice the bandwidth of the modulating signal.
- Power Efficiency: Least efficient as power is wasted on the carrier and both sidebands.
