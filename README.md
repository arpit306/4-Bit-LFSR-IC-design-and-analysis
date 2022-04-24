# 4 Bit LFSR IC Design & Analysis
This repository presents the design of LFSR implemented using Cadence virtuoso tool on 90nm CMOS Technology.
## Abstract
This repository presents the IC design of a 4-Bit Linear Feedback Shift Register (LFSR) also known as Pseudo Random Binary Sequence Generator; on 90nm CMOS technology.
This implementation is done on Cadence Virtuoso tool and gpdk90 library. It is basically a shift register with a linear function feedback. The generally used linear feedback function in LFSR is XOR. It has got many application such as counters, data bit generators, pattern generators, Pseudo random bit sequence generators as well as in data encryption & compression technologies. The working of design is verified using Circuit Schematic and Waveforms.  
## Tool used  
The Cadence® Virtuoso® System Design Platform is a holistic, system-based solution that provides the functionality to drive simulation and LVS-clean layout of ICs and packages from a single schematic.

![Picture1](https://user-images.githubusercontent.com/68592620/164977590-b3e1cb46-d1ee-4a0d-b034-904aa818d44f.png)

## Circuit-Description
To make a 4-bit LFSR, first we need to make a 4 bit shift register. I have chosen 4 positive edge triggered D Flip-Flops with asynchronous preset inputs. This flipflop is a master-slave D latch combination. The D latch is made using CMOS Inverters, Buffers & Transmission gates for improved switching transients. Preset input is incoperated by the Latch hence by the flip flop. This asynchronous preset input is essential in order to generate the initial state of the bit pattern, which would help in better analysis of the output.  
__Reference Circuit:__  
![ckt](https://user-images.githubusercontent.com/68592620/164976460-98618807-8360-49f0-b083-14322adb19d1.png)  
## Circuit-Schematic
The schematics of LFSR & respective circuits are shown below:

__LFSR Circuit:__

![schematic](https://user-images.githubusercontent.com/68592620/164975269-05ff7bd1-abdc-463d-b86c-6dc10ce21063.png)

## Waveforms
▫️ The following waveforms were obtained in transient analysis of the given design.  
▫️ Simulation ran for 900ns.  
▫️ Clock has period of 50ns & Pulse width is 25ns.  
▫️ Preset signal is high initially to set the intial state of flip flops.  
▫️ Analysis should be done after preset signal goes low.  

![wfm](https://user-images.githubusercontent.com/68592620/164976303-a5719d4f-a76a-468e-aa25-3a2f54bbf888.png)  

## Observation

![observation](https://user-images.githubusercontent.com/68592620/164976295-226e19d2-f77b-4186-8d32-d2a1101108ef.png)

## Spice Netlist
```// Generated for: spectre
// Generated on: Apr 22 17:05:30 2022
// Design library name: arpit_designs
// Design cell name: LFSR
// Design view name: schematic
simulator lang=spectre
global 0
include "/home/cadence/gpdk090_v4.6/libs.oa22/gpdk090/../../models/spectre/gpdk090.scs" section=NN

// Library name: arpit_designs
// Cell name: CMOS_NOT
// View name: schematic
subckt CMOS_NOT Gnd Vdd Vin Vout
    NM0 (Vout Vin Gnd Gnd) gpdk090_nmos1v w=(120n) l=100n as=69.6f \
        ad=69.6f ps=1.16u pd=1.16u m=(1)*(1) simM=(1)*(1)
    PM0 (Vout Vin Vdd Vdd) gpdk090_pmos1v w=(120n) l=100n as=69.6f \
        ad=69.6f ps=1.16u pd=1.16u m=(1)*(1) simM=(1)*(1)
ends CMOS_NOT
// End of subcircuit definition.

// Library name: arpit_designs
// Cell name: CMOS_Buffer
// View name: schematic
subckt CMOS_Buffer Vin Vout gnd vdd
    I1 (gnd vdd net09 Vout) CMOS_NOT
    I0 (gnd vdd Vin net09) CMOS_NOT
ends CMOS_Buffer
// End of subcircuit definition.

// Library name: arpit_designs
// Cell name: CMOS_NOR
// View name: schematic
subckt CMOS_NOR Vdc Vin1 Vin2 Vout gnd
    NM1 (Vout Vin2 gnd gnd) gpdk090_nmos1v w=(120n) l=100n as=69.6f \
        ad=69.6f ps=1.16u pd=1.16u m=(1)*(1) simM=(1)*(1)
    NM0 (Vout Vin1 gnd gnd) gpdk090_nmos1v w=(120n) l=100n as=69.6f \
        ad=69.6f ps=1.16u pd=1.16u m=(1)*(1) simM=(1)*(1)
    PM1 (Vout Vin2 net19 Vdc) gpdk090_pmos1v w=(120n) l=100n as=69.6f \
        ad=69.6f ps=1.16u pd=1.16u m=(1)*(1) simM=(1)*(1)
    PM0 (net19 Vin1 Vdc Vdc) gpdk090_pmos1v w=(120n) l=100n as=69.6f \
        ad=69.6f ps=1.16u pd=1.16u m=(1)*(1) simM=(1)*(1)
ends CMOS_NOR
// End of subcircuit definition.

// Library name: arpit_designs
// Cell name: Transmission_gate
// View name: schematic
subckt Transmission_gate Control Control_bar V1 V2
    NM0 (V1 Control V2 0) gpdk090_nmos1v w=(120n) l=100n as=69.6f ad=69.6f \
        ps=1.16u pd=1.16u m=(1)*(1) simM=(1)*(1)
    PM0 (V1 Control_bar V2 net8) gpdk090_pmos1v w=(120n) l=100n as=69.6f \
        ad=69.6f ps=1.16u pd=1.16u m=(1)*(1) simM=(1)*(1)
    V0 (net8 0) vsource dc=1.8 type=dc
ends Transmission_gate
// End of subcircuit definition.

// Library name: arpit_designs
// Cell name: D_Latch_asyncSET
// View name: schematic
subckt D_Latch_asyncSET Clk D_in Preset Q Q_bar Vdd gnd
    I13 (net014 Q gnd Vdd) CMOS_Buffer
    I7 (Vdd Preset net19 Q_bar gnd) CMOS_NOR
    I12 (gnd Vdd Clk net8) CMOS_NOT
    I8 (gnd Vdd Q_bar net014) CMOS_NOT
    I11 (net8 Clk net19 net014) Transmission_gate
    I10 (Clk net8 D_in net19) Transmission_gate
ends D_Latch_asyncSET
// End of subcircuit definition.

// Library name: arpit_designs
// Cell name: D_FF_asyncSET_PosE
// View name: schematic
subckt D_FF_asyncSET_PosE Clk D_in Preset Q Q_bar Vdd gnd
    I1 (Clk net20 Preset Q Q_bar Vdd gnd) D_Latch_asyncSET
    I0 (net21 D_in Preset net20 net22 Vdd gnd) D_Latch_asyncSET
    I2 (gnd Vdd Clk net21) CMOS_NOT
ends D_FF_asyncSET_PosE
// End of subcircuit definition.

// Library name: arpit_designs
// Cell name: CMOS_NAND
// View name: schematic
subckt CMOS_NAND Gnd Vdd Vin1 Vin2 Vout
    NM1 (net20 Vin1 Gnd Gnd) gpdk090_nmos1v w=(120n) l=100n as=69.6f \
        ad=69.6f ps=1.16u pd=1.16u m=(1)*(1) simM=(1)*(1)
    NM0 (Vout Vin2 net20 Gnd) gpdk090_nmos1v w=(120n) l=100n as=69.6f \
        ad=69.6f ps=1.16u pd=1.16u m=(1)*(1) simM=(1)*(1)
    PM1 (Vout Vin2 Vdd Vdd) gpdk090_pmos1v w=(120n) l=100n as=69.6f \
        ad=69.6f ps=1.16u pd=1.16u m=(1)*(1) simM=(1)*(1)
    PM0 (Vout Vin1 Vdd Vdd) gpdk090_pmos1v w=(120n) l=100n as=69.6f \
        ad=69.6f ps=1.16u pd=1.16u m=(1)*(1) simM=(1)*(1)
ends CMOS_NAND
// End of subcircuit definition.

// Library name: arpit_designs
// Cell name: CMOS_AND
// View name: schematic
subckt CMOS_AND Vdd Vin1 Vin2 Vout gnd
    I0 (gnd Vdd Vin1 Vin2 net13) CMOS_NAND
    I1 (gnd Vdd net13 Vout) CMOS_NOT
ends CMOS_AND
// End of subcircuit definition.

// Library name: arpit_designs
// Cell name: CMOS_XOR
// View name: schematic
subckt CMOS_XOR Vin1 Vin2 Vout gnd vdc
    I8 (vdc net20 net14 Vout gnd) CMOS_NOR
    I10 (vdc net11 net12 net14 gnd) CMOS_AND
    I9 (vdc Vin1 Vin2 net20 gnd) CMOS_AND
    I7 (gnd vdc Vin2 net12) CMOS_NOT
    I6 (gnd vdc Vin1 net11) CMOS_NOT
ends CMOS_XOR
// End of subcircuit definition.

// Library name: arpit_designs
// Cell name: LFSR
// View name: schematic
I3 (net013 net011 net5 Q net14 net6 0) D_FF_asyncSET_PosE
I2 (net013 net09 net5 net9 net15 net6 0) D_FF_asyncSET_PosE
I1 (net013 net014 net5 net010 net16 net6 0) D_FF_asyncSET_PosE
I0 (net013 net016 net5 net13 net17 net6 0) D_FF_asyncSET_PosE
I4 (net014 Q net11 0 net6) CMOS_XOR
V1 (net013 0) vsource type=pulse val0=0 val1=1 period=50n width=25n
V0 (net5 0) vsource type=pulse val0=0 val1=1 period=10u width=50n
V2 (net6 0) vsource dc=1 type=dc
I12 (net11 net016 0 net6) CMOS_Buffer
I13 (net13 net014 0 net6) CMOS_Buffer
I14 (net010 net09 0 net6) CMOS_Buffer
I15 (net9 net011 0 net6) CMOS_Buffer
simulatorOptions options reltol=1e-3 vabstol=1e-6 iabstol=1e-12 temp=27 \
    tnom=27 scalem=1.0 scale=1.0 gmin=1e-12 rforce=1 maxnotes=5 maxwarns=5 \
    digits=5 cols=80 pivrel=1e-3 sensfile="../psf/sens.output" \
    checklimitdest=psf 
tran tran stop=900n write="spectre.ic" writefinal="spectre.fc" \
    annotate=status maxiters=5 
finalTimeOP info what=oppoint where=rawfile
modelParameter info what=models where=rawfile
element info what=inst where=rawfile
outputParameter info what=output where=rawfile
designParamVals info what=parameters where=rawfile
primitives info what=primitives where=rawfile
subckts info what=subckts  where=rawfile
saveOptions options save=allpub
```
