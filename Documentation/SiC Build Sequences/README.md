# Silicon Carbide Build Sequences

Author: Philip Turner

Date: May 31, 2025

Related document: [SiliconCarbide.md](https://gist.github.com/philipturner/d9b02836d65e63c0bd875c6fbbc4cc7f)

Reverses the conclusion of the previous document, which stated that a build sequence compiler cannot be designed. However, the scope of geometries buildable with the new primitives is too small to be of practical use. Ideas for removing this limitation are omitted for clarity.

## How to Access

There are many technical issues with exporting this research from OneNote to a portable format.
- On iPadOS, exporting converts it to a giant, long PDF file.
- On macOS, exporting makes a PDF split into 98 pages, each chopped inconveniently in the middle of important sections. In addition, the file size explodes to 4 GB.
- Both exporting mechanisms invert the colors, changing from dark mode to light mode. This makes yellows difficult to distinguish.

Two options for improvement:
- Find a way to isolate the OneNote page into a publicly shareable notebook.
- Painstakingly screenshot each section of the document and re-assemble into an organized PDF or GitHub repo.

How to view now:
- Download the file in this repo: [PDF (40 MB)](https://raw.github.com/philipturner/apm-roadmap/main/Documentation/SiC%20Build%20Sequences/SiC_Final_Cell_Issue.pdf)
- Open in a compatible PDF viewer, such as Apple Preview. It may appear blurry until it fully loads.

## Summary of Technical Discoveries

A set of four primitives for unit cell creation and extension
- Conscious of unknown pathologies that will only be known reliably in IRL experiment
- Different primitives describe the different combinations of assumptions/pathologies relevant to them

Reaction "trees" that explore multiple plausible pathways to the end goal. If one branch is false in experiment, the alternative branch is true. All branches arrive at the end goal of making synthesis feasible.

Discovered and solved all major issues with extending to multiple SiC unit cells on a SiC(111) surface with "silicons on top".
- Pathological situation with crowded steric issues and chance of 5-ring formation. This situation never appears when applying the primitives one-by-one on a hexagonal drawing board. Except when intentionally extending cells in the wrong order, closing a ring around a hole of unbuilt cells.
- Combinatorial possibilities of H-tunneling pathologies reveal no major theoretical arguments against feasibility. Overcame that fact that we cannot know, with confidence, which specific H-tunneling pathologies will happen IRL.

Organotins are needed energetically in two situations, based on GFN2-xTB energies:
- Depositing SiH<sub>3</sub> onto a Si<sub>3</sub>C· site
- Abstracting the second hydrogen from a Si moiety to generate a diradical, without taking the silicon atom with it
  - Exploits an equilibrium process, where the H has non-negligible probability of remaining on the Si moiety or the Sn tooltip
  - Requires a subsequent step that transports the grabbed hydrogen to a more energetically downhill radical, such as Ge or Si

Discovered new fundamental issues the lattice extension:
- Inevitable creep of the SiC(111) surface with "carbons on top", shrinking the edges of the atomic layer every 3 iterations. All attempts to fill a cuboidal volume with unit cells resulted in a convex pyramid.
- No detailed simulation research on whether SiC(111) with "carbons on top" can be extended. A brief attempt at proposing a layer initiation sequence (by hand / mental math) ended in mixed results.
- Most likely need control over angle of C<sub>3</sub>C-CC· tool, when abstracting H from a methyl group to form a Si-C bond. This means the IRL nanopositioning device needs quasi-5DOF, or control of the static orientation prior to tip approach.

Other fundamental issues that simulations cannot answer:
- Whether SiC can be built on a Si(111) surface. Beyond an extremely tiny product, which must be tiny to avoid popping off from lattice constant mismatch.
- Whether SiC can be built on a Si(100) surface.
- Whether SiC can be built on a more practical (higher conductivity) W surface. Or the thin amorphous Si layer covering a W tip.
- Whether the necessary NC<sub>3</sub>Sn· tool can be synthesized or charged.

## Actions to Take

We have concerningly low confidence that both the build surface and tooltip can be fabricated. Even if they can, reaction frequency may be so slow as to be entirely impractical. These three concerns deserve detailed clarification and formalization.

An equally deserved task is revisiting the concluded discoveries with:
- More accurate models (g-xTB)
- More extensive outsider peer review
- More pessimistic (finite temperature) reaction paths

Testing these discoveries with IRL hardware will be dangerous and extremely complicated. Much less practical than inverted mode mechanosynthesis of amorphous C with a randomly positioned set of Ge tooltips.

<b>We must be absolutely sure that crystal structure is a mandatory prerequisite for massively parallel molecular manufacturing.</b> The most straightforward conclusion of my research: while crystals can be built in a simulation (e.g. MinToolset paper), this is unlikely to happen in the real world.