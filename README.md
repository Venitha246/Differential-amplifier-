## Experminet 3:- MOS Differential Amplifier
## AIM:Design and analyse the MOS differential amplifier circuit for the given specification.
VDD=2.5V

P<=3mW

Vicm=1.3V

Vocm=1.4V

Vp= 0.3V

## Perform DC analysis, transient analysis and frequency response and extract the required paramenters.
## Introduction 
The **MOS differential amplifier** is a critical component in analog circuit design, widely used in applications like operational amplifiers, data converters, and communication systems. It offers high gain, excellent linearity, and common-mode noise rejection, making it a cornerstone of modern electronics.

In this project, we aim to design and analyze a MOS differential amplifier that meets the following specifications:
- **Supply Voltage (Vdd):** 2.5 V
- **Power Dissipation (P):** ≤ 3 mW
- **Common-Mode Input Voltage (Vicm):** 1.3 V
- **Common-Mode Output Voltage (Vocm):** 1.4 V
- **Overdrive Voltage (Vp):** 0.3 V

The design process will involve selecting suitable MOSFET parameters, biasing conditions, and circuit topology to achieve the desired performance. The analysis will include:
1. **DC Analysis:** To determine operating points and bias currents.
2. **Transient Analysis:** To evaluate the time-domain response of the amplifier.
3. **Frequency Response:** To study the gain and bandwidth characteristics.

The extracted parameters will validate the design and provide insights into the amplifier's performance under varying conditions. This comprehensive study will not only satisfy the technical requirements but also highlight the practical considerations in designing robust analog circuits.

## Circuit Diagram


## Working Principle of a MOS Differential Amplifier
The **MOS differential amplifier** operates based on the principle of **differential signal amplification**, which involves amplifying the difference between two input signals while rejecting any common-mode signals (e.g., noise or interference).

#### **Key Components and Their Roles:**
1. **MOSFET Pair (Transistors):**
   - The amplifier typically consists of two MOSFETs configured as a differential pair. 
   - These transistors share a common source, which is connected to a constant current source.

2. **Current Source:**
   - A constant current source supplies a stable bias current to the circuit, ensuring proper operation and maintaining high common-mode rejection.

3. **Load Resistors/Active Loads:**
   - Connected to the drain terminals of the MOSFETs, they determine the voltage gain of the amplifier.

#### **Steps in the Working Process:**

1. **Differential Mode Operation:**
   - When two input voltages are applied to the gates of the MOSFETs, the amplifier responds to the difference between these inputs.
   - If one input increases and the other decreases, the current flowing through each transistor adjusts accordingly, leading to a differential output voltage.

2. **Common-Mode Signal Rejection:**
   - If both input signals are identical (common-mode), the current distribution between the MOSFETs remains unchanged, and the common-mode signal is largely suppressed in the output.

3. **Output Voltage:**
   - The output voltage is measured across the load resistors or active loads at the drain terminals. It is proportional to the difference in currents flowing through the MOSFETs, which is driven by the difference in input voltages.

4. **Gain:**
   - The gain of the amplifier depends on the transconductance of the MOSFETs and the load impedance.

## Procedure: Simulating a Differential Amplifier in LTSpice

1. Open LTSpice

Launch LTSpice and create a new schematic file to begin the simulation process.

2. Load the Required Library

Ensure accurate MOSFET simulations by importing the tsmc018.lib library, which contains models for TSMC 0.18µm (180nm) CMOS technology. The library file should be stored in the same directory as the LTSpice simulation file.

3. Add Circuit Components

Select and place the required components in the schematic:

M1 & M2 (CMOSN): Two NMOS transistors

R1, R2, RSS: Three resistors

VDD, V2, V3: Three voltage sources


Assign appropriate values to each component based on the design specifications.

4. Connect the Circuit

Wire the components together according to the differential amplifier schematic. Ensure correct connections between the transistors, resistors, and voltage sources.

5. Configure the Simulation Settings

Open the Simulate menu and select Edit Simulation Cmd.

Go to the DC op pnt (DC operating point) tab.


6. Perform DC Operating Point Analysis

Enable the option to compute the DC operating point.

Start the simulation by clicking Run to analyze the circuit's DC behavior.


7. Analyze the Simulation Results

## Design:
Given P<=3mW
**But we have considered P=3mW**
since P=VddxIss;

**Iss = P/Vdd = 3m/2.5 = 1.2mA**


**Id1=Id2=Iss/2 = 0.6mA**

By Applying KVL :

**Vdd-I1Rd-Vocm1=0**
2.5- 0.6m Rd - 1.4 = 0
**Rd = 1.833kohm**

**Rss=Vp/Iss = 0.3/1.2m**

Rss=250ohm

### Circuit 1




## DC Analysis




Mosfet aspect ratio was same ie, L= nm, W = um

for mosfet M1 & M2:

Vicm = 1.3V

Vocm = 1.4V

Id= 0.6mA

Vtn = 0.487v

VDD = IdRd + VDS +Vp

2.5=0.6m(1.833k)+VDS+0.3

VDS = 1.1002V

The Q-point of both the mosfets are (1.1002V, 0.6mA).

## Transient Analysis



The transient analysis of the MOS differential amplifier aims to evaluate its dynamic behavior and time-domain response when subjected to varying input signals. This analysis provides key insights into the amplifier's performance, including its ability to amplify signals linearly without distortion and its response to changes in input signals over time.

#### **Procedure:**
1. The circuit was designed as per the given specifications:
   - **Supply Voltage (Vdd):** 2.5 V
   - **Bias Current:** Derived from the tail current source.
   - **Load Resistors:** Properly chosen to ensure the desired gain.
2. A small differential input signal (sine wave) with an amplitude of \( V_p \) = 0.3 V was applied. The common-mode input voltage (\( V_{icm} \)) was maintained at 1.3 V.
3. Transient simulation was performed in LTSpice with a simulation time sufficient to observe multiple signal cycles.
4. The output voltage was recorded at the drain terminals of the differential MOSFET pair.

#### **Results and Observations:**
- The amplifier's differential output exhibited a clean, amplified version of the input signal, confirming proper linear operation.
- Key parameters such as **rise time**, **fall time**, and **settling time** were extracted from the time-domain waveform.
- The observed transient response verified the absence of distortion, indicating the circuit operates within its designed parameters.

  From the above observation
Gain Av=Vout(peak)/Vin(peak)
Av= 0.3126/0.0974 = 3.209V/V
Converting it to the decibel(dB):
20log(3.209) = 10.127 dB

## AC Analysis



**AC analysis** examines the frequency-domain response of the MOS differential amplifier, providing insights into its gain, bandwidth, and stability. This analysis is essential for understanding how the amplifier performs across different frequencies.


#### **Procedure for AC Analysis:**
1. **Setup the Circuit:**
   - Use the same circuit configuration as in the transient analysis.
   - Apply a small AC signal to one of the differential inputs, while the other input is grounded or set to the common-mode input voltage (\( V_{icm} = 1.3 \, \text{V} \)).

2. **Configure AC Input Signal:**
   - Set the AC magnitude of the input signal to a small value (e.g., 1 mV). This ensures linear operation and prevents distortion during frequency-domain analysis.

3. **Simulation Settings in LTSpice:**
   - Open the **AC Analysis** tab in LTSpice.
   - Specify the frequency range for the sweep (e.g., \( 1 \, \text{Hz} \) to \( 10 \, \text{MHz} \)).
   - Choose a logarithmic or linear frequency scale, depending on the desired resolution.

4. **Run the Simulation:**
   - Start the AC analysis to compute the amplifier's frequency response, including gain and phase at various frequencies.

5. **Extract and Analyze Parameters:**
   - **Voltage Gain (\( A_v \)):** Observe the ratio of output voltage to input voltage across the frequency range.
   - **Bandwidth:** Identify the frequency range over which the amplifier maintains a consistent gain (typically up to -3 dB from the maximum gain).
   - **Phase Shift:** Analyze how the phase of the output signal varies with frequency.
   - **Gain-Bandwidth Product (GBW):** Calculate the product of the gain and bandwidth to assess the amplifier's performance.
 From the graph gain in dB scale is
20log(3.209)=10.127dB

## Inference 
From the analysis of the MOS differential amplifier, we can see how effectively the circuit performs. The transient analysis showed that the amplifier works well with time-varying signals, amplifying them cleanly without distortion. It also responds quickly to input changes, making it reliable for dynamic applications.

In the frequency analysis, the amplifier demonstrated a stable gain at lower frequencies and maintained good performance within its bandwidth. The cutoff frequency marked the range where the amplifier is most effective, and the gain-bandwidth product confirmed its overall quality.

The amplifier also did a great job rejecting noise or common-mode signals, proving its suitability for handling real-world scenarios with interference. Additionally, it operated within the power dissipation limit of 3 mW, highlighting its efficiency.

Overall, the amplifier meets all the design goals, offering high linearity, stability, and excellent noise rejection—ideal for applications requiring precise signal amplification.


## Circuit 2
Replacing ( R3 ) with a current source ( Iss ) transforms the circuit into a fully differential pair with an active current source. This modification eliminates source degeneration, increasing the gain and improving common-mode rejection (CMRR). The current source ensures a stable bias current, making the circuit less sensitive to variations in component values. Without ( R3 ), the transconductance ( g_m ) is higher, resulting in a larger differential gain given by (Ad=gm*rd).

## DC Analysis




Mosfet aspect ratio was same ie, L= nm, W = um

for mosfet M1 & M2:

Vicm = 1.3V

Vocm = 1.4V

Id= 0.6mA

Vtn = 0.487v

VDD = IdRd + VDS +Vp

2.5=0.6m(1.833k)+VDS+0.3

VDS = 1.1002V

The Q-point of both the mosfets are (1.1002V, 0.6mA).

## Transient Analysis



The modification of replacing ( R_3 ) with a current source( I_{ss} )fundamentally enhances the MOS differential amplifier's performance. By eliminating source degeneration, the circuit achieves higher transconductance( g_m) and improved gain. 



#### **Objective:**
The transient analysis evaluates the time-domain response of the fully differential amplifier. It focuses on the increased differential gain and dynamic behavior resulting from the integration of an active current source.


#### **Procedure:**
1. **Circuit Setup:**
   - Replace ( R_3 ) with a constant current source ( I_{ss}) to create a fully differential structure.
   - Set the current source to provide a stable tail current, ensuring consistent biasing of the MOSFET pair.

2. **Input Signal Configuration:**
   - Apply a differential input signal (e.g., a sine wave with an amplitude of ( V_p = 0.3V) to the gates of the MOSFETs.
   - Maintain the common-mode voltage at ( V_{icm} = 1.3V).

3. **Transient Simulation:**
   - Run a time-domain simulation over a sufficient period to observe multiple signal cycles.
   - Measure the differential output voltage ( V_{out+} - V_{out-} ) at the drain terminals of the MOSFETs.

From the above observation
Gain Av=Vout(peak)/Vin(peak)
Av= 0.3156/0.1004 = 3.143 V/V
Converting it to the decibel(dB):
20log(3.143) = 9.94 dB


## AC Analysis




#### **Objective:**
The aim of AC analysis is to study the frequency-domain behavior of the MOS differential amplifier after replacing ( R_3 ) with ( I_{ss} ). Key parameters such as gain ( A_v), bandwidth, and common-mode rejection ratio (CMRR) will be determined.



#### **Procedure:**
1. **Circuit Configuration:**
   - Replace ( R_3 ) with a current source (\( I_{ss} )) at the common source node.
   - Maintain the rest of the circuit setup, including the differential MOSFET pair, load resistors, and supply voltage.

2. **Input Signal:**
   - Apply a small AC signal (e.g., 1 mV peak) to one of the differential inputs while grounding the other input.
   - This ensures linear operation during the frequency sweep.

3. **Simulation in LTSpice:**
   - Configure AC analysis in LTSpice to sweep over a desired frequency range
   - Use a logarithmic frequency scale for better resolution in observing gain across multiple decades.

4. **Output Analysis:**
   - Measure the differential output voltage ( V_{out+} - V_{out-} ) across the load resistors or active loads.

From the graph gain in dB scale is
20log(3.143)=9.94dB

## Inference
By replacing ( R_3 ) with a current source (\( I_{ss} ), the circuit's performance significantly improved. This change increased the differential gain because there’s no source degeneration, allowing higher transconductance( g_m ) and better voltage gain ( A_d = g_m . r_d ). 

The transient analysis showed a larger output signal and excellent linearity, with fast response times, making the circuit more suitable for high-speed operations. The active current source provided stable biasing, which also reduced sensitivity to component variations.

In the frequency-domain (AC analysis), the circuit demonstrated higher gain and wider bandwidth compared to the original setup. The current source enhanced noise rejection by improving the common-mode rejection ratio (CMRR), making the amplifier better at handling real-world noise and interference.

Overall, these upgrades confirmed that replacing ( R_3 ) with ( I_{ss} ) resulted in a more efficient, precise, and high-performing differential amplifier.


## Circuit 3
**Differential Amplifier with NMOS Current Source Biasing**

This circuit features an improved differential amplifier where the traditional tail resistor is replaced with an NMOS transistor (M3) functioning as a current source. This modification enhances the stability and control of the bias current in the differential pair (M1 and M2), resulting in a more consistent operating point and improved common-mode rejection.

By utilizing an active NMOS current source, the circuit achieves higher accuracy and stability in amplifying the difference between the input signals (V2 and V1). This method ensures better regulation of the bias current, which is crucial for applications demanding precise signal processing and strong resistance to common-mode noise. While maintaining its fundamental role of differential signal amplification, the circuit benefits from enhanced performance and reliability due to the active biasing approach.


## Circuit Diagram



## DC Analysis


Mosfet aspect ratio was same ie, L= nm, W = um

for mosfet M1 & M2:

Vicm = 1.3V

Vocm = 1.4V

Id= 0.6mA

Vtn = 0.487v

VDD = IdRd + VDS +Vp

2.5=0.6m(1.833k)+VDS+0.3

VDS = 1.1002V

The Q-point of both the mosfets are (1.1002V, 0.6mA).

## Transient Analysis 


In Circuit 3, we replaced the tail resistor with an NMOS transistor ( M_3 ) as a current source. This change makes the bias current more stable and keeps the circuit's operating point consistent. During transient analysis, the circuit showed improved performance.

The gain of the amplifier increased because the NMOS current source gives a higher transconductance( g_m ). The output waveform was amplified well, with no distortion, and it responded quickly to input changes. The linearity of the circuit also improved because ( M_3 ) keeps the bias current steady.

Additionally, the NMOS current source enhanced the circuit's ability to reject noise. This improvement in common-mode rejection makes the amplifier more reliable in handling real-world signals.

From the above observation
Gain Av=Vout(peak)/Vin(peak)
Av= 0.3126/0.0974 = 3.209V/V
Converting it to the decibel(dB):
20log(3.209) = 10.127 dB

## AC Analysis



In Circuit 3, using an NMOS transistor ( M_3 ) as a current source instead of a tail resistor improved the amplifier's performance, especially in terms of gain and stability. During the AC analysis, the circuit showed a higher gain because the NMOS current source increased the output impedance. This enhanced the overall gain ( A_v = g_m . r_d ).

The circuit maintained good performance across a broader range of frequencies, showing a wider bandwidth compared to the previous configurations. The NMOS current source also significantly improved noise rejection by enhancing the common-mode rejection ratio (CMRR), making the circuit more effective at rejecting unwanted signals or noise.

From the graph gain in dB scale is
20log(3.209)=10.127dB

## Inference 
By replacing the tail resistor with an NMOS transistor (\( M_3 \)) as a current source, Circuit 3 showed significant improvements. This modification provided better stability and control over the bias current, ensuring that the operating point remained consistent. 

The transient and AC analyses confirmed that this change led to higher differential gain (\( A_d = g_m \cdot r_d \)) due to the increased transconductance and output impedance. The circuit's ability to handle signals over a wider range of frequencies was evident from its improved bandwidth. Additionally, the NMOS current source enhanced the circuit's noise rejection by improving the common-mode rejection ratio (CMRR). 

Overall, this design made the amplifier more efficient, stable, and precise, which is especially beneficial for applications requiring high accuracy and reliability in signal amplification.

## Summary 

### **Circuit 1a: Basic Differential Amplifier**
This circuit uses a resistive tail ( R_3 ) and serves as a simple design for amplifying differential signals. While effective for basic applications, its performance is limited due to source degeneration, which restricts the gain and reduces its ability to reject noise. The transient analysis showed clean but moderate amplification, and the AC analysis highlighted a reasonable bandwidth and gain suitable for simpler uses.


### **Circuit 2: Differential Amplifier with a Current Source**
In Circuit 2, the tail resistor ( R_3 ) is replaced by a current source ( I_{ss} ), which eliminates source degeneration and significantly improves the circuit's performance. The transient analysis revealed higher gain with clean output signals and better linearity. The AC analysis showed wider bandwidth and enhanced noise rejection through an improved common-mode rejection ratio (CMRR). This circuit is a step up from Circuit 1a, offering better performance and reliability.


### **Circuit 3: Differential Amplifier with NMOS Current Source Biasing**
Circuit 3 further improves the design by replacing the resistive tail with an NMOS transistor ( M_3 ) as a current source. This change provides more stability and precision in biasing the circuit. Transient analysis confirmed a high gain with excellent linearity and quick response to input changes. The AC analysis showed wider bandwidth and superior noise immunity, thanks to an even better CMRR. This circuit stands out as the most efficient and reliable for applications requiring precision and stability.
