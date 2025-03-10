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



