# Near-Term: Experiments

Phase 0: Immediate target is to materialize an improved version of “Fast low-noise transimpedance amplifier” ([arxiv.org/abs/2007.00615](https://arxiv.org/abs/2007.00615)). It will remove the need for dangerous high voltage electronics and use a 300 MΩ feedback resistor. The project also requires careful consideration of PCBs with ADC/DAC chips, compensation capacitors for capacitive displacement sensing, and power filter feedback loops. It will be a challenging, but important, demonstration of control over external EMI and strong coupling between analog components. Assembly will rely entirely on hand soldering, making the lab setup minimal and convenient.

Another component of Phase 0 is finite element simulation of electromagnetic fields. Recent developments suggest the Elmer dependency of FreeCAD can be compiled, by targeting x86\_64 and running under Rosetta 2 on Apple silicon. While it is computationally intractable to model electromagnetic radiation, the tool may elucidate static electric fields from nearby high voltage conductors.

Phases I&ndash;III have extreme barriers to entry.

| Phase      | Barrier | Explanation |
| :--------- | :------ | :---------- |
| I          | High voltage electronics | 1000 V power filter<br>1000 V linear amplifier<br>Risk to health and safety (shock hazard) |
| I          | Laser interferometry | Understand the speed limits of Michelson interferometry to clarify Phase IV<br>Complicated field of engineering, in general<br>Risk to health and safety (laser blinding) |
| I&ndash;II | Epoxy | Unfamiliar<br>Necessary to assemble precision nanopositioning and optical hardware<br>Possible health risk (bisphenol A fumes) |
| I&ndash;II | [Vibration isolation](https://gist.github.com/philipturner/a365d72c1ba5c4eedf1c331bb21d586d) | Solved problem, but still a pain<br>CNC machining of stiff aluminum housing (solved barrier) |
| III        | Transporting an entire UHV STM in a vehicle | Lifting heavy equipment<br>Always present risk of automobile accident |
| III        | Renting a dedicated lab | Prefer to handle everything in Philip’s garage<br>Extraordinary cleanliness/cleanroom standards for assembling UHV chambers |
| III        | Organogermanium tripod synthesis | Complicated, multi-step chemical process<br>High-field NMR spectroscopy is inaccessible to average people |

Accelerate progress on the experimental side. Knock down the first barrier to entry into Phase I: high voltage electronics. Therefore, a concurrent project to the transimpedance amplifier will be a sub-phase of Phase I. Custom power supply module and linear amplifier, all using equipment rated for 3000&ndash;5000 V. Measure the output of the high voltage amplifier with an oscilloscope. Establish good safety practices, such as using insulated gloves and SHV connectors. Get rigorous peer review on the safety plan from experts in HV electronics.

Piezo stack fabrication will occur in a late sub-phase of Phase I. One important barrier has been broken, the ability to [know crystallographic orientation beforehand](https://gist.github.com/philipturner/9fb9d81c1d2d1427b4287541a99e6cec). Piezo plates received from Crystal Substrates had notches and chamfers, positioned to uniquely identify the crystal lattice vectors. The process for assembling piezo stacks, with this knowledge, still has not been fleshed out in detail. It will likely be very complicated and error-prone.

Kinematic mount fabrication will occur in a late sub-phase of Phase I. It builds on epoxy, a barrier to entry for Phase I. Consequential struggles with engineering the Phase II system are [described to a high level of detail](https://github.com/philipturner/home-built-stm).

Reflow soldering will likely not be needed until Phase II, which requires the DAC81404 chip (QFN package). It is a 4-channel DAC from the highest quality product line of Texas Instruments. The barrier to entry for reflow soldering has already been broken.
