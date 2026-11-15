# EE186 Lab 4

## ADC
(a)
The STM32L4R5 ADC supports 12-bit, 10-bit, 8-bit, and 6-bit resolution. Lower resolutions require fewer successive-approximation steps and therefore allow higher sampling rates.
| Resolution | Maximum rate—fast channels | Maximum rate—slow channels |
|---|---:|---:|
| 12 bits | 5.33 MS/s | 4.21 MS/s |
| 10 bits | 6.15 MS/s | 4.71 MS/s |
| 8 bits | 7.27 MS/s | 5.33 MS/s |
| 6 bits | 8.88 MS/s | 6.15 MS/s |


MS/s means million samples per second. These are the maximum rates under the datasheet’s specified operating conditions; longer sampling times reduce the achievable conversion rate.

This information appears in the STM32L4R5xx/STM32L4R7xx/STM32L4R9xx datasheet, DS12023 Rev 5, Table 81, “ADC characteristics,” page 214, in the sampling-rate rows for fast and slow channels.


(b)
The photoresistor changes its resistance with light intensity, whereas the ADC measures voltage. A voltage divider containing the photoresistor and a fixed 10 kΩ resistor converts the resistance change into a measurable voltage.

With the photoresistor connected between 3.3 V and the output junction, and the fixed resistor connected between the junction and ground:
\[
V_{\text{out}}=V_{\text{in}}\frac{10\,000}{R_{\text{LDR}}+10\,000}.
\]

(c)
Diagrams made in overleaf:






<img width="672" height="722" alt="image" src="https://github.com/user-attachments/assets/ddbf9bf8-88a0-4c90-af6c-63e7a729b3ab" />

(d) code in file 2d.c


https://github.com/user-attachments/assets/a92db793-c17c-471e-b073-088125484fac



## DAC

(a)
Using the ideal DAC relation Vout = (B / 2^n) Vref, B = 9 gives Vout = (9 / 4096) Vref, approximately 0.0021973 Vref. For Vref = 3.3 V, this is approximately 7.25 mV. 

(b)
code in file 3b.c for 
<img width="692" height="439" alt="image" src="https://github.com/user-attachments/assets/f4bbc300-c82a-49cb-b42d-8435dcfd90e5" />


(c)
For a fixed output frequency, increasing the DAC sample-update rate provides more samples per period. This gives a finer staircase approximation to the desired waveform and moves sampling images farther above the signal band. The update rate must exceed twice the highest frequency component we want to reproduce. Square and sawtooth waves contain many harmonics, so their sharp edges cannot be reproduced exactly at a finite sampling rate. With an N-sample table repeated once per period, the output frequency is f_out = f_update/N; increasing the update rate without changing N also increases the pitch.

At the same fundamental frequency, sine, square, and sawtooth waves have the same pitch but different timbres. A sine wave contains only the fundamental and sounds pure. An ideal symmetric square wave contains odd harmonics with amplitudes proportional to 1/n and sounds hollow or buzzy. A sawtooth wave contains both even and odd harmonics with amplitudes proportional to 1/n, producing a brighter, harsher sound.

The DAC waveform has a positive DC offset because its output cannot go below ground. A series coupling capacitor blocks that DC component while passing the changing audio signal. This prevents sustained DC current through the speaker or earphone coil. Together with the effective load resistance, the capacitor forms a high-pass filter with cutoff frequency f_c = 1/(2*pi*R*C). The capacitance should be large enough that the cutoff is below the desired audio frequencies. AC coupling does not itself provide the current gain needed to drive a low-impedance load.


(d)
Code is in file 3d.c


## Musical Instrument


https://github.com/user-attachments/assets/46822752-8c05-40f4-add7-8bad32e0f1db

code is in 4.c file

















