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




















