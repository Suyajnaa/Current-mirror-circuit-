# Current-mirror-circuit-
- Working of current mirror circuit  using MOSFETs 

## Aim:
 Design and Analyze Current mirror circuit as active load in amplifier circuit.

### Performing :
- DC Ananlysis
- Transient Analysis
- AC Analysis
- Extract required parameters

### Components Required:
- MOSFET(NMOS,PMOS)
- Resistors
- Current source
- Voltage supply
- Connecting wires

## Theory

A MOSFET current mirror is a fundamental analog circuit used to copy a reference current from one branch of a circuit into another, maintaining a stable and predictable output current. This circuit plays a critical role in analog integrated circuits such as operational amplifiers, differential amplifiers, and active loads. The core idea behind a current mirror is that if two MOSFETs are matched and operated under the same conditions, they will conduct equal currents when their gate-source voltages are equal.

The basic MOSFET current mirror consists of two identical n-channel MOSFETs. The first MOSFET, often called the reference transistor, has its gate and drain connected together, forming a diode-connected configuration. This ensures the transistor operates in the saturation region, where the drain current is primarily controlled by the gate-source voltage. A reference current is forced through this transistor, creating a fixed gate voltage that is then applied to the gate of the second transistor.

The second MOSFET, known as the output transistor, has its gate and source connected to those of the reference transistor. Assuming it is also operating in saturation and the MOSFETs are well matched, the output transistor will mirror the current flowing in the reference transistor. If both transistors have the same width-to-length ratio (W/L), then the output current will ideally be equal to the reference current. If different W/L ratios are used, the output current can be scaled proportionally.

While the MOSFET current mirror is simple and effective, it has limitations. The accuracy of current mirroring depends on how closely the transistors are matched in terms of threshold voltage, mobility, and physical dimensions. In addition, channel length modulation can introduce errors, causing the output current to vary with changes in the output voltage. Furthermore, there is a minimum output voltage, known as the compliance voltage, below which the output transistor can no longer remain in saturation and accurate mirroring fails.

Despite these limitations, the MOSFET current mirror remains a versatile and widely used circuit element. Its ability to generate precise and scalable bias currents makes it invaluable in analog circuit design. More advanced versions, such as Wilson and cascode current mirrors, improve performance by increasing output resistance and reducing the effect of voltage variations at the output node.

![image](https://github.com/user-attachments/assets/69376a23-4454-4970-aeb9-fdd021a31424)

 
## Part A

**1> Design question** 
- Power Supply (V<sub>DD</sub>) = 1.8V.
- Power Consumption (P) <= 1mW. 
- Gain (A<sub>v</sub>) > -10V/V.

### Circuit

![image](https://github.com/user-attachments/assets/b8be8323-46fd-4a70-8524-3a151b055e79)

 <pre>
   I total = P / Vdd
   I total = I ref + I x
 </pre>

 **Design for the current mirror ratio 1:1 and 1:2**

## DC Analysis

### Steps to Perform DC Analysis 
1. Build the circuit as per the diagram shown above and set the values of the voltage sources,resistors as per the calculated values.
2. Next go to **SPICE Directive** and type **.lib filename.lib or .lib filepath.lib** to import the Library file.
3. Click **OK**, and place the generated command on the schematic.
4. After importing the library file name the two mosfet as CMOSN.
5. Set the channel length value of M<sub>1</sub> as 180nm and  we have to vary the value of the width to get a desired value of I<sub>D</sub> and V<sub>out</sub>
6. Repeat the same steps with M<sub>2</sub> mosfet.
7. Now go to **Edit simulation command** and select **DC op pnt**.
8. Click **OK**, and place the generated command on the schematic.
9. Next click on run button, you will get a pop up window which gives us information about operating point.It includes the values of V<sub>out</sub> and I<sub>D</sub>.
 
## Transient Analysis

### Steps to Perform Transient Analysis 
1. After setting the operating point, we will give sine wave as the input for both the gate terminals of the mosfet.
2. Next set the **Amplitude** as 50mV and **Frequency** as 1kHz for both V<sub>2</sub> and V<sub>3</sub>.
3. You should specify the AC amplitude for each voltage source separately. You have two voltage sources, you can set their AC amplitudes as follows:
 - First Voltage Source(V<sub>2</sub>): **AC amplitude** = 1
 - Second Voltage Source(V<sub>3</sub>): **AC amplitude** = -1
4. Next set **phi[deg]** for V<sub>3</sub> as 180.
5. Now go to **Edit Simulation cmd** and select **Transient**.
6. Give **stop time** as per your convenience, here it is 5m.
7. Click **OK**, and place the generated command on the schematic.
8. Verify the response and note the phase shift and signal gain.

## AC Analysis

### Steps to Perform AC Analysis :

1. Go to Simulate > Edit Simulation Cmd.
2. In the AC Analysis tab, choose Decade as the sweep type.
3. Specify the number of points per decade and set the frequency range from 0.1Hz to 1THz.
4. Click OK and place the generated command on the schematic.
5. Ensure that the input voltage source has an AC amplitude of 1V.
6. Click the Run button to start the analysis.
7. Examine the gain and phase plots.
8. Determine key characteristics such as bandwidth and gain margin.
 
 ## Case 1
 <pre>
   I total = P/ Vdd
           = 1m / 1.8 
           = 0.555m A
  </pre>
  
 if ratio is 1:1
   
 <pre>
   I ref = I x
  
   I total = I ref + I x
    0.555m = 2 * I ref
     I ref = 0.277m A = I x
  </pre>


 **Circuit**
 
![image](https://github.com/user-attachments/assets/b381318e-8962-4289-8b5a-6cf2f07d0c01)

**DC Analysis** 

![image](https://github.com/user-attachments/assets/e1784b0c-bbcd-4ddc-a3e8-9074cde45961)

![image](https://github.com/user-attachments/assets/56646cfb-7297-4f02-b5bd-887b1c486d93)

![image](https://github.com/user-attachments/assets/0db5ba11-42f3-430a-a52c-268e3ff80c6a)


**Transient Analysis**

![image](https://github.com/user-attachments/assets/9d583e4f-43b6-4a40-800d-08b5c503d41e)


INPUT:

![Image](https://github.com/user-attachments/assets/c62f9169-72ab-4ef2-843d-e601be447097)

OUTPUT:

![Image](https://github.com/user-attachments/assets/6041cebc-b8d6-4d4c-9611-35583355ceef)

**AC Analysis**

![Image](https://github.com/user-attachments/assets/34f2279c-0fd6-4b1c-90f6-f3d95a0443d6)

The Expected gain in db of the circuit is 20db.But the obtained gain from the AC analysis(frequency response) is 22.117db.

|Parameter      |Theory value  | Practical value |
|---------------|--------------|-----------------|
|Av(in dB)      | 20dB         | 22.117dB         |
|Av(in V/V)     | 10           | 10.12            |

**3db Bandwidth:**

The obatined 3db B.W=2.253GHz.

![Image](https://github.com/user-attachments/assets/4c9f54bb-8fcd-49f3-8c97-8d90e143613e)


 ## Case 2
 <pre>
   I total = P/ Vdd
           = 1m / 1.8 
           = 0.555m A
  </pre>
 
 if ratio is 1:2
   
 <pre>
   I ref = 2 * I x
  
   I total = I ref + I x 
    0.555m = 3 * I ref
     I ref = 0.185m A
     I x   = 0.37m A
  </pre>



**Circuit**

![Image](https://github.com/user-attachments/assets/f5bd39e0-d8e9-46bd-954a-145ff21f8ad8)



**DC Analysis**

![Image](https://github.com/user-attachments/assets/792237e5-ca5c-4a18-938d-8cf86e65bf7f)

OUTPUT:

![Image](https://github.com/user-attachments/assets/d6b1ba32-0f98-43f5-b57a-8624733312e1)

**Transient Analysis**

![Image](https://github.com/user-attachments/assets/73700227-f1c9-4959-9f7b-451a2113ce76)

INPUT:

![Image](https://github.com/user-attachments/assets/482b6bc0-1a1a-4115-959f-76b6a4cb1d22)

OUTPUT:

![Image](https://github.com/user-attachments/assets/a13ee9d1-08a3-441e-9a23-c97182fb14e6)

The Expected gain of the circuit is -10V/V.But the obtained gain from the transient analysis is -11.36V/V.


**AC Analysis**

![Image](https://github.com/user-attachments/assets/9cd5cb62-1b5b-4c7b-858b-704d2a5a957e)

 

The Expected gain in db of the circuit is 21.34db.But the obtained gain from the AC analysis(frequency response) is 24.55db.

|Parameter      |Theory value  | Practical value |
|---------------|--------------|-----------------|
|Av(in dB)      | 21.34dB      | 24.55dB         |
|Av(in V/V)     | 10           | 11.36          |

**3db Bandwidth:**

The obatined 3db B.W=1.186GHz.

![Image](https://github.com/user-attachments/assets/60a9df80-3b1b-41b5-b14f-8215f75df050)

### **Comparison Table:**
| **Parameter**  | **Mirror Ratio 1:1** (Theory) | **Mirror Ratio 1:1** (Practical) | **Mirror Ratio 1:2** (Theory) | **Mirror Ratio 1:2** (Practical) |
|---------------|-----------------------------|-----------------------------|-----------------------------|-----------------------------|
| Av (in dB)    | 20 dB                        | 22.117 dB                     | 21.34 dB                     | 24.55 dB                     |
| Av (in V/V)   | 10                           | 10.12                          | 10                           | 11.36                         |
| 3 dB Bandwidth | -                            | 2.253 GHz                     | -                            | 1.186 GHz                     |  


## Inference:

- The implemented current mirror circuit accurately replicates the reference current with minimal deviation, demonstrating effective current mirroring across different W/L ratios.

- When the W/L ratio is varied while maintaining the same proportionality, the drain current (Id) remains nearly constant, confirming the reliability of the mirror circuit.

- The measured amplifier gain is slightly higher than the theoretical prediction for both mirror ratios, likely due to minor mismatches in transistor parameters or simulation-related variations.

- An increase in the mirror ratio from 1:1 to 1:2 results in a higher gain, as anticipated. However, this also leads to a reduction in bandwidth—from 2.253 GHz to 1.186 GHz.

- Overall, the simulation results align closely with theoretical expectations, validating both the circuit design and the simulation methodology.



## Part B

## Aim:
Design the differential amplifier using the same design specification as Experiment-3. Perform DC analysis,trasient and AC analysis.

## DC Analysis

- Repeat the same steps as mentioned in the above section.

![Image](https://github.com/user-attachments/assets/8ef76f51-e4b2-469e-b4ed-2fa01ff3582b)

Here’s a well-structured explanation of the DC Analysis for your circuit while ensuring that all MOSFETs operate in the saturation region and match the experimental results.

1. Circuit Overview

The circuit comprises six MOSFETs (labeled M1 through M6), each with specified (W/L) ratios. It is essential to ensure that all transistors operate in the saturation region throughout the analysis for accurate performance. The given width-to-length ratios for the transistors are as follows:

- M1: 108 μm / 180 nm
- M2: 108 μm / 180 nm
- M4: 108 μm / 180 nm
- M3: 49.1 μm / 180 nm
- M5: 57.33 μm / 180 nm
- M6: 57.33 μm / 180 nm

To preserve consistency with Experiment 3, the circuit must maintain the same DC operating point, which includes both the current levels and node voltages. Accordingly, the biasing conditions are selected to match those of the previous experiment.

![Image](https://github.com/user-attachments/assets/2cceda88-b45c-4953-82ef-5f89d74089e1)


## Transient Analysis

- Repeat the same steps as mentioned in the above section.

Circuit Diagram:

![Image](https://github.com/user-attachments/assets/d9721172-90ac-4507-80cb-f209b5f9fdb8)


INPUT:

![Image](https://github.com/user-attachments/assets/d29de8c7-91f6-471f-8afc-b95161aa0ed0)

OUTPUT:

![Image](https://github.com/user-attachments/assets/fcf711dc-4d72-4097-9948-bab749e0348f)

The Expected gain of the circuit is -8.6V/V.But the obtained gain from the transient analysis is -13.979V/V.

## AC Analysis

- Repeat the same steps as mentioned in the above section.

Circuit Diagram:

![Image](https://github.com/user-attachments/assets/1bfcd546-2f16-4a24-a6f2-53143182cb63)


The Expected gain in db of the circuit is 22.72db.But the obtained gain from the AC analysis(frequency response) is 23.46db.

|Parameter      |Theory value  | Practical value |
|---------------|--------------|-----------------|
|Av(in dB)      | 21.34dB      | 23.46dB          |
|Av(in V/V)     | 8.6          | 13.979           |

![Image](https://github.com/user-attachments/assets/f399a75e-d2e7-4f46-930b-c552aec7adb2)



**3db Bandwidth:**

The obatined 3db B.W=400.0834MHz.

 ![Image](https://github.com/user-attachments/assets/e4acc891-9d80-4cc1-9dfb-543e7616c284)


## Inference

- The observed gain, which exceeds expected values, may be attributed to additional gain contributions arising from parasitic effects or mismatches between devices.

- The measured high bandwidth of 406.16 MHz indicates that the amplifier is well-suited for high-frequency applications.

- Moreover, the deviation in gain could also result from an underestimation of the drain resistance or variations in transconductance across the devices.


