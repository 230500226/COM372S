# Amplifiers and Oscillators Class 04
19-01-2025

## Amplifiers in communication systems
- Amplifiers are used in communication systems to increase the strength of the signal.
- For long distance signal transmission
- The transmit power (RF power) determines the range of the signal
- Amplifiers need to be linear and constant (no drift) - (gain remains constant at all timees all inputs) linearity performance
- Amplifiers must be power efficient - power efficiency performance
- Important factor is to balance linearity and power efficiency
- cutoff mode - not producing any output - input is not being processed by amplifire

## Classes of Amplifiers
- The cutoff mode differs between Class A, B, C and more
- The class depends on the best for the signal
- crossover point is when the amplifier switches from cutoff to active mode - only with non-linear
- crossover distortion is the distortion that occurs at the crossover point
- Classes seen on slide 7
- Class A: 360 degrees of the input signal is amplified
    - Linear region (exact copy)
    - Not power efficient
    - no crossover point
- Class B: 180 degrees of the input signal is amplified
    - non linear region
    - More power efficient
    - has one crossover
- Class C: Less than 180 degrees of the input signal is amplified
    - two crossover points
- Class AB: Between Class A and B - Conductin angle is between 180 - 200 degrees
There are many other classes to achieve the most efficient amplification
- Applications of amplifiers - audio amplifiers, RF amplifiers, etc.

## Oscillators
- Oscillators are resonance circuits used to generate a signal
    - The carrier signal is mixed with a modulating signal to generate the modulated signal
    - LC Oscillators
        - utilises LC tank or Parallel LC circuit
        - easy to build
        - widely used in RF applications, recievers and audio oscillators
        - The feedback increases or sustains the self generated output.
            - This is done using positive feedback mechanism

    - Hartley Oscillators
         - Utilises a tapped inductor
         - The biggest advantage is that it can be easily tuned to the desired frequency compared to LC oscillators
         - the tapped inductor is used to provide feedback
            - it works by providing a phase shift of 180 degrees 
            - But can be tuned to provide 360 degrees of phase shift (tunes how much feedback is provided by limiting the amount of windings used)

    - Clapp Oscilator
        - Utilises a varactor diode
        - The varactor diode is used to tune the oscillator
        - The varactor diode is a voltage controlled capacitor

    - crystal Oscilator
        - Utilises a crystal to generate the signal
        - The crystal is used to provide feedback
        - Optimum performance is obtained when coupled with an external capacitance
