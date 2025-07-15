# CAD Software: Implementation Plan

An ambitious software engineering project will simulate the largest possible nanomachine systems, with the highest quality visualization. It will repurpose consumer hardware, designed for AI/ML, to instead perform dense linear algebra and embarrassingly parallel molecular mechanics modeling. The entire software stack rests heavily on the FP32 data type, with FP16/BF16 serving little practical use.

CAD at the million atom scale requires both high throughput real time rendering, and design practices that scale to very large atom counts. Importantly, [automation of the bond topology setup](https://github.com/philipturner/HDL/blob/2025-cleanups/Documentation/API/Reconstruction.md) and $O(n)$ scaling simulations. Scalable design probably means <b>restriction to exclusively sp<sup>3</sup> hybridized crystal lattices, which coincides with the hardest material to build</b> in experiment. See also: [additional discussion](http://apm.bplaced.net/w/index.php?title=Software) of nanofactory design and control software.

[Swift programming language:](https://www.swift.org) Modern programming language inspired by Python, Rust, and Haskell. Apple recently released Swift 6, with improved focus on cross-platform support and enforcing good practices in concurrent CPU code. Achieves the claimed performance of Mojo (explicit fixed width SIMD vectors in CPU-only code) [today](https://web.archive.org/web/20250704141833/https://docs.modular.com/mojo/faq/#will-mojo-be-open-sourced), on all major platforms.

[Molecular Renderer:](https://github.com/philipturner/molecular-renderer) Origin of the need to restrict to Apple silicon and discrete GPUs. Imposter method is not acceptable. Need visually satisfying self-shadowing. To achieve this effect correctly, one must identify the average distance from one reflecting surface to other nearby surfaces. This is accomplished through ray tracing, efficient random sampling, and real time denoising (combining samples from previous frames). A [marvel of software engineering](https://github.com/GPUOpen-LibrariesAndSDKs/FidelityFX-SDK) made this denoising not only tractable, but accurate enough to triple the image resolution.
- Breaking the 0.5&ndash;1.5 million atom barrier requires new approaches. The ray tracing acceleration structure must be constructed gradually, over several frames. This is similar to Minecraft's chunk loader, which loads chunks in order from nearest to farthest from the viewer.
- Preliminary investigation proved it is possible to construct a CPU-side API, perhaps using `subscript(index:)` and `_modify`, that allows in-place modification of an atom array without scanning the entire array each frame. The maximum array capacity must be specified at program startup and allocated proactively. To counteract fragmentation, this allocation may be treated as an "address space".
- Practical limits are likely in the tens of millions, not the 200 million previously desired because of the KSRM replicator atom count. This is due to the very large number of bytes per atom (~100), from the acceleration structure and auxiliary CPU-side arrays. A tradeoff for making it practical to code Swift programs as easily as in previous projects.
- Target is nanofactory / 3D printer / rod logic scenes, where most atoms reside in static housing. A small fraction (perhaps 10%) can move each frame. This percentage is the second contributor to the practical limit for atom count.

[HDL:](https://github.com/philipturner/HDL/tree/2025-cleanups) Shape description language compiler from <i>Nanosystems,</i> Ch. 14.6.4. Exploits direct control over fixed width SIMD vectors, performing computationally intensive operations over homogeneous crystal unit cells. All with acceptably low latency. Almost a finished library.
- Considered adding dedicated support for 2D lattices (graphene) that are more likely to be buildable IRL. Concluded that this is out of scope, and conflicts with the purpose of the library. Instead, retain the short tutorial that models graphene with the 3D `Hexagonal` basis and a simple transformation.

[xTB:](https://github.com/grimme-lab/xtb) Modern replacement for Gaussian 16 and GAMESS (US). Especially with the g-xTB method that performs on par with B3LYP.
- Recent developments boosted confidence that the 2.0&ndash;3.0x whole program speedup target is achievable. Source: https://github.com/grimme-lab/xtb/issues/1315
- React to the recent news of g-xTB, and its complications for open-shell simulations.

[MM4:](https://github.com/philipturner/mm4) Replace the OpenMM dependency with a custom backend, written from scratch in Metal (macOS) and DirectX (Windows). Intentionally excludes Linux and multi-GPU superclusters.
- Enable fluid dynamics simulation in exploratory studies of Phase V. Extend [MM4Parameters](https://philipturner.github.io/MM4/documentation/mm4/mm4parameters) to sp<sup>3</sup> hybridized feedstock molecules. Very complicated algorithms for retaining $O(n)$ scaling in nonbonded force computation.
- Impractical to offload [rigid body dynamics](https://philipturner.github.io/MM4/documentation/mm4/mm4rigidbody) and other rotary motor constraints to the GPU. Rotary constraints are an artifact of easily coded CPU-centric time integrators. Completely nonphysical when the actuation source is 3DOF LiNbO3 picopositioners.
- Force the user to script energy minimizations in Swift code, with a CPU&ndash;GPU data transfer at every timestep. Encourage exploitation of key-value SSD caching, which defeated a simulation bottleneck in [mechanosynthetic-build-sequences](https://github.com/philipturner/mechanosynthetic-build-sequences). Exacerbates the barrier to entry.

## Shortcut Through Implementation Plan

The xTB C API doesn't work on Windows. This event reminded me of a conclusion reached in ~August 2024, that we just need a correct foundation for nanotech CAD that compiles/runs on all platforms. Written from the ground up, entirely in Swift. The mindset behind the motivation to replace OpenMM with a custom Swift code base. The MSEP project was motivated by a similar goal: get the basics right.

Don't bake simulators into the core CAD workflow, when they might not even compile, or pre-compiled dylibs must be hosted on GitHub. Instead, create an environment where users can easily link custom dylibs to the `Workspace` executable. The main interface will be a `run.sh` and/or `run.bat` script. It serves two purposes:
- Force the Swift compiler to use the `-Xswiftc -Ounchecked` mode.
- Facilitate linking of dylibs (currently just FidelityFX and DXCompiler on Windows)

Three Swift packages serve as the "core" of nanotech CAD:
- Molecular Renderer
- HDL
- A fork of `swift-numerics` that supports quaternions. It grew outdated since 2022, but it's not worth the hassle to fuse recent commits from `main` into the branch.