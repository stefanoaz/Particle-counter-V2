# Particle-counter-V2
PIN Diode-based beta, gamma radiation particle counter with differential sensing, Version 2

This is a beta/gamma particle detector designed with differential sensing of the PIN diode signal, to establish some rejection of common-mode EMI. Transimpedance amplifiers with high gain are very similar to an oscilloscope probe amplifier: high impedance and very sensitive to external interference. By sensing symmetrically across both sides of the diodes, common-mode rejection of 40dB can be achieved. In batches of 1% resistor and 5% capacitor tolerances, matching can be achieved of 0.1% for R and 1% for C. This will yield 40dB CMRR.

This design is intended for remote sensing for balloon flights or similar weight-sensitive applications: PCB weight (0.4mm material) is 0.75g. As such, the added weight (and difficulty) of shielding is avoided, or reduced, by incorporating common-mode rejection.

Specific changes from Version 1:
Board size reduced by 0.2" in X and Y dimensions. Added board clearance margin to make application of diode light blocking material (such as black electrical tape) easier. Extended backside ground plane underneath the sensor diodes, significantly improving CMRR and EMI rejection. Added backside pads for additional sensor diodes (see notes). Event detection threshold now referred to a bandgap voltage reference. Front-end U1 opamp now MAX4489 (higher GBW, low noise). U2,3 now OPA2325 (10 MHz GBW, low offset). Threshold voltage reduced to detect lower energy events.

Notes: The V1 board accommodated 6 PIN sensor diodes. V2 now adds the capacity to add up to six more on the back side of the board. But there is a tradeoff: Photodiode transimpedance amplifiers exhibit voltage noise peaking proportional to (C_diode / C_integrator). With the V2 improved CMRR and the lower noise of U1, I was able to lower the comparator event threshold from 350mV to 200mV (increased sensitivity), while maintaining margin over noise, with 6 diodes. As the number of diodes increases, the TIA amp noise peaking increases, so that the threshold would need to be increased (sensitivity reduced) so that the detector doesn't trigger on noise. The component settings for the comparator (200mV) are good for 6 diodes. 225-250mV should be good for up to 8-9 diodes. I do not recommend going past 9 diodes - there would be no benefit due to reduced sensitivity.

Do not exceed 5.5V Vcc.
