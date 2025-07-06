# Near-Term Experiments

Philip’s next project (“Phase 0”) is to materialize an improved version of “Fast low-noise transimpedance amplifier” (Schmid et al., [arxiv.org/abs/2007.00615](https://arxiv.org/abs/2007.00615)). It will remove the need for dangerous high voltage electronics and use a 300 MΩ feedback resistor. The project also requires careful consideration of PCBs with ADC/DAC chips, compensation capacitors for capacitive displacement sensing, and power filter feedback loops. It will be a challenging, but important, demonstration of control over external EMI and strong coupling between analog components. Assembly will rely entirely on hand soldering, making the lab setup minimal and convenient.

Phases I&ndash;III have extreme barriers to entry.

| Phase | Barrier | Explanation |
| ----- | ------- | ----------- |
| I     | High voltage electronics | 1000 V power filter<br>1000 V linear amplifier<br>Risk to health and safety (shock hazard) |
| I     | Laser interferometry | Understand the speed limits of Michelson interferometry to clarify Phase IV<br>Complicated field of engineering, in general<br>Risk to health and safety (laser blinding) |
| I     | Epoxy | Unfamiliar<br>Necessary to assemble precision nanopositioning and optical hardware<br>Possible health risk (bisphenol A fumes) |
| I     | [Vibration isolation](https://gist.github.com/philipturner/a365d72c1ba5c4eedf1c331bb21d586d) | Solved problem, but still a pain |
| III   | Transporting an entire UHV STM in a vehicle |

Accelerate progress on the experimental side. Knock down the first barrier to entry into Phase I: high voltage electronics. Therefore, a concurrent project to the transimpedance amplifier will be a sub-phase of Phase I. Custom power supply module and linear amplifier, all using equipment rated for 3000&ndash;5000 V. Measure the output of the high voltage amplifier with an oscilloscope. Establish good safety practices, such as using insulated gloves and SHV connectors. Get rigorous peer review on the safety plan from experts in HV electronics.