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
**But we have considered P=2.5mW**
since P=VddxIss;

**Iss = P/Vdd = 2.5m/3.3 = 0.757mA**


**Id1=Id2=Iss/2 = 0.37mA**

By Applying KVL :

**Vdd-I1Rd-Vocm1=0**
3.3 - 0.37 Rd - 1.81 = 0
**Rd = 3.93kohm**

**Rss=Vp/Iss = 0.7/0.757m**

Rss=0.924kohm

### Circuit 1
