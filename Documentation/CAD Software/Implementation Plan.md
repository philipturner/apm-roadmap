# CAD Software: Implementation Plan

An ambitious software engineering project will simulate the largest possible nanomachine systems, with the highest quality visualization. It will repurpose consumer hardware, designed for AI/ML, to instead perform dense linear algebra and embarrassingly parallel molecular mechanics modeling. The entire software stack rests heavily on the FP32 data type, with FP16/BF16 serving little practical use.

CAD at the million atom scale requires both high throughput real time rendering, and design practices that scale to very large atom counts. Importantly, [automation of the bond topology setup](https://github.com/philipturner/HDL/blob/2025-cleanups/Documentation/API/Reconstruction.md) and $O(n)$ scaling simulations. Scalable design probably means <b>restriction to exclusively sp<sup>3</sup> hybridized crystal lattices, which coincides with the hardest material to build</b> in experiment. See also: [additional discussion](http://apm.bplaced.net/w/index.php?title=Software) of nanofactory design and control software.

Swift programming language: Modern programming language, inspired by Python, Rust, and Haskell. Apple recently released Swift 6, with improved focus on cross-platform support and enforcing good practices in concurrent CPU code. Achieves the claimed performance of Mojo (explicit fixed width SIMD vectors in CPU-only code) today, on all major platforms.

Molecular Renderer: Origin of the need to restrict to Apple silicon and discrete GPUs. Imposter method is not acceptable. Need visually satisfying self-shadowing. To achieve this effect correctly, one must identify the average distance from one reflecting surface to other nearby surfaces. This is accomplished through ray tracing, efficient random sampling, and real time denoising (combining samples from previous frames). A marvel of software engineering made this denoising not only tractable, but accurate enough to triple the image resolution.

HDL: Shape description language compiler from <i>Nanosystems</i>, Ch. 14.6. Exploits direct control over fixed width SIMD vectors, performing computationally intensive operations over homogeneous crystal unit cells. All with acceptably low latency. Almost a finished library.

HDL: Shape description language compiler from <i>Nanosystems,</i> Ch. 14.6. Exploits direct control over fixed width SIMD vectors, performing computationally intensive operations over homogeneous crystal unit cells. All with acceptably low latency. Almost a finished library.

xTB: Recent developments boosted confidence that the 2.0&ndash;3.0x whole program speedup target is achievable. Source: https://github.com/grimme-lab/xtb/issues/1315

MM4: Replace the OpenMM dependency with a custom backend, written from scratch in Metal (macOS) and DirectX (Windows). Intentionally excludes Linux and multi-GPU superclusters.
- Enable fluid dynamics simulation in exploratory studies of Phase V. Extend MM4Parameters to sp<sup>3</sup> hybridized feedstock molecules. Very complicated algorithms for retaining $O(n)$ scaling in nonbonded force computation.
- Impractical to offload rigid body dynamics and other rotary motor constraints to the GPU. Rotary constraints are an artifact of easily coded CPU-centric time integrators. Completely nonphysical when the actuation source is 3DOF LiNbO3 picopositioners.
- Force the user to script energy minimizations in Swift code, with a CPU&ndash;GPU data transfer at every timestep. Encourage exploitation of key-value SSD caching, which defeated a simulation bottleneck in mechanosynthetic-build-sequences. Exacerbates the barrier to entry.