# 4 Bit LFSR IC Design & Analysis
This repository presents the design of LFSR implemented using Cadence virtuoso tool on 90nm CMOS Technology.
## Abstract
This repository presents the IC design of a 4-Bit Linear Feedback Shift Register (LFSR) also known as Pseudo Random Binary Sequence Generator; on 90nm CMOS technology.
This implementation is done on Cadence Virtuoso tool and gpdk90 library. It is basically a shift register with a linear function feedback. The generally used linear feedback function in LFSR is XOR. It has got many application such as counters, data bit generators, pattern generators, Pseudo random bit sequence generators as well as in data encryption & compression technologies. The working of design is verified using Circuit Schematic and Waveforms.
## Circuit-Description
To make a 4-bit LFSR, first we need to make a 4 bit shift register. I have chosen 4 positive edge triggered D Flip-Flops with asynchronous preset inputs. This flipflop is a master-slave D latch combination. The D latch is made using CMOS Inverters, Buffers & Transmission gates for improved switching transients. Preset input is incoperated by the Latch hence by the flip flop. This asynchronous preset input is essential in order to generate the initial state of the bit pattern, which would help in better analysis of the output.  
__Reference Circuit:__  
![ckt](https://user-images.githubusercontent.com/68592620/164976460-98618807-8360-49f0-b083-14322adb19d1.png)  
## Circuit-Schematic
The schematics of LFSR & respective circuits are shown below:

__LFSR Circuit:__

![schematic](https://user-images.githubusercontent.com/68592620/164975269-05ff7bd1-abdc-463d-b86c-6dc10ce21063.png)

__D Flip Flop with Asynchronous Preset:__

![FF](https://user-images.githubusercontent.com/68592620/164892097-4229472e-7e9d-448f-a428-de0d9267f3fe.png)

__D Latch with Asynchronous Preset:__

![latch](https://user-images.githubusercontent.com/68592620/164892172-cd4a91ba-1f76-4c44-93c5-7e5bf09662e6.png)

## Waveforms
▫️ The following waveforms were obtained in transient analysis of the given design.  
▫️ Simulation ran for 900ns.  
▫️ Clock has period of 50ns & Pulse width is 25ns.  
▫️ Preset signal is high initially to set the intial state of flip flops.  
▫️ Analysis should be done after preset signal goes low.  

![wfm](https://user-images.githubusercontent.com/68592620/164970576-d4f0dc3c-4ad4-4008-a8ff-12c2d780bafd.png)

## Observation

![observation](https://user-images.githubusercontent.com/68592620/164972618-c7a2287c-42f2-4a80-b3ab-e4e80bb2c227.png)
