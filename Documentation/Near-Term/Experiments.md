# Near-Term: Experiments

Phase 0: Immediate target is to materialize an improved version of “Fast low-noise transimpedance amplifier” ([arxiv.org/abs/2007.00615](https://arxiv.org/abs/2007.00615)). It will remove the need for dangerous high voltage electronics and use a 300 MΩ feedback resistor. The project also requires careful consideration of PCBs with ADC/DAC chips, compensation capacitors for capacitive displacement sensing, and power filter feedback loops. It will be a challenging, but important, demonstration of control over external EMI and strong coupling between analog components. Assembly will rely entirely on hand soldering, making the lab setup minimal and convenient.

> Update: split Phase 0 into two parts
> 1) Transimpedance amplifier without capacitive displacement sensing
> 2) Use capacitive displacement sensing to detect the micron-scale actuations from a ThorLabs piezo stack. It requires low voltages of 15&ndash;45 V. Although the PZT material suffers from creep, it's a more accessible stepping stone toward the end goal.

Another component of Phase 0 is finite element simulation of electromagnetic fields. Recent developments suggest the Elmer dependency of FreeCAD can be compiled, by targeting x86\_64 and running under Rosetta 2 on Apple silicon. While it is computationally intractable to model electromagnetic radiation, the tool may elucidate static electric fields from nearby high voltage conductors.

> Update: now, at least the Elmer executable is compiling on macOS. Have not yet tested whether the integration with FreeCAD works. Source: https://github.com/ElmerCSC/elmerfem/issues/503

Phases I&ndash;III have extreme barriers to entry.

| Phase      | Barrier | Explanation |
| :--------- | :------ | :---------- |
| I          | High voltage electronics | 1000 V power filter<br>1000 V linear amplifier<br>Risk to health and safety (shock hazard) |
| I          | <s>Laser interferometry</s> | Understand the speed limits of Michelson interferometry to clarify Phase IV<br>Complicated field of engineering, in general<br>Risk to health and safety (laser blinding) |
| I&ndash;II | Epoxy | Unfamiliar<br>Necessary to assemble precision nanopositioning and optical hardware<br>Possible health risk (bisphenol A fumes) |
| I&ndash;II | [Vibration isolation](https://gist.github.com/philipturner/a365d72c1ba5c4eedf1c331bb21d586d) | Solved problem, but still a pain<br>CNC machining of stiff aluminum housing (solved barrier) |
| III        | Transporting an entire UHV STM in a vehicle | Lifting heavy equipment<br>Always present risk of automobile accident |
| III        | Renting a dedicated lab | Prefer to handle everything in Philip’s garage<br>Extraordinary cleanliness/cleanroom standards for assembling UHV chambers |
| III        | <s>Organogermanium tripod synthesis</s> | Complicated, multi-step chemical process<br>High-field NMR spectroscopy is inaccessible to average people |

Accelerate progress on the experimental side. Knock down the first barrier to entry into Phase I: high voltage electronics. Therefore, a concurrent project to the transimpedance amplifier will be a sub-phase of Phase I. Custom power supply module and linear amplifier, all using equipment rated for 3000&ndash;5000 V. Measure the output of the high voltage amplifier with an oscilloscope. Establish good safety practices, such as using insulated gloves and SHV connectors. Get rigorous peer review on the safety plan from experts in HV electronics.

Piezo stack fabrication will occur in a late sub-phase of Phase I. One important barrier has been broken, the ability to [know crystallographic orientation beforehand](https://gist.github.com/philipturner/9fb9d81c1d2d1427b4287541a99e6cec). Piezo plates received from Crystal Substrates had notches and chamfers, positioned to uniquely identify the crystal lattice vectors. The process for assembling piezo stacks, with this knowledge, still has not been fleshed out in detail. It will likely be very complicated and error-prone.

Kinematic mount fabrication will occur in a late sub-phase of Phase I. It builds on epoxy, a barrier to entry for Phase I. Consequential struggles with engineering the Phase II system are [described to a high level of detail](https://github.com/philipturner/home-built-stm).

Reflow soldering will likely not be needed until Phase II, which requires the DAC81404 chip (QFN package). It is a 4-channel DAC from the highest quality product line of Texas Instruments. The barrier to entry for reflow soldering has already been broken.

## Shortcut Through Phase I

There is one idea to skip laser interferometry, and the subsequent need for vibration isolation to get nanometer-stable position readings. Directly build a piezo stack and test whether it can perform coarse actuations in response to a sawtooth voltage. The principal challenge is the number of variables that must be debugged. A single variable might be possible to bisect, like narrowing down lines of code to find a culprit. Two variables pose a continuous 2D space, borderline intractable to navigate. We have eliminated uncertainty in crystallographic orientation as a catastrophic unknown variable.

The high barrier to entry for laser interferometry motivates attempting to skip it, deferring investigation to Phase IV. There is low confidence that this will succeed. A helpful elucidation will be whether a full kinematic mount (three stacks + low-friction nanoasperity) is required. Another is the number of fabrication attempts needed. It is advantageous (although stressful) to order the required number of LiNbO3 plates from Crystal Substrates, 3 weeks in advance. The massive time delay + non-negligible costs deterred running the first test of LiNbO3 during early 2025.

Actions to solve the root causes of this issue:
- Have other tasks (e.g. 1000 V linear amplifier) queued up for the possible 3 week wait
- Rectify the basic physics involved and minimum displacement target
- Elaborate on the assembly process (e.g. epoxy) and chance of failure
- Create CAD models and/or simulations to finalize the specific plate dimensions that must be ordered
- Quantify the number of simultaneous control variables
- Obtain more confidence and experience in the relevant engineering disciplines, such as analog electronics

## Shortcut Through Phase III

Tripod synthesis is out of scope. It requires access to high-field NMR spectroscopy. I've given up on trying to perform this synthesis, and it's a distraction anyway. The biggest problem is the cost and complexity of the electrical and vacuum hardware, to even manipulate hydrogen atoms on a silicon surface.

I am interested in organotin tripods, which have never been synthesized before. Not so much the organogermanium tripods, which have already been proven many times.
