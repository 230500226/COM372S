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
