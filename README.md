# 4-Bit-LFSR-IC-design
This repository presents the IC design of a 4-Bit Linear Feedback Shift Register (LFSR) also known as Pseudo Random Binary Sequence Generator; on 90nm CMOS technology.
This implementation is done on Cadence Virtuoso tool and gpdk90 library. It is basically a shift register with a linear function feedback. The generally used linear feedback function in LFSR is XOR. It has got many application such as counters, data bit generators, pattern generators, Pseudo random bit sequence generators as well as in data encryption & compression technologies. The working of design is verified using Circuit Schematic and Waveforms.
## Circuit-Description
To make a 4-bit LFSR, first we need to make a 4 bit shift register. I have chosen 4 positive edge triggered D Flip-Flops with asynchronous preset inputs. This flipflop is a master-slave D latch combination. The D latch is made using CMOS Inverters, Buffers & Transmission gates for improved switching transients. Preset input is incoperated by the Latch hence by the flip flop. This asynchronous preset input is essential in order to generate the initial state of the bit pattern, which would help in better analysis of the output.

__LFSR Circuit:__

![schematic](https://user-images.githubusercontent.com/68592620/164891993-b400f0d0-ae36-46a1-8f71-74a1362a462d.png)

__D Flip Flop with Asynchronous Preset:__

![FF](https://user-images.githubusercontent.com/68592620/164892097-4229472e-7e9d-448f-a428-de0d9267f3fe.png)
