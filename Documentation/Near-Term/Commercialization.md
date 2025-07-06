# Near-Term: Commercialization

The economic model is heavily inspired by EUV lithography (see the DeepSeek output below). Several funding sources have been pondered&mdash;venture capital, government, academia, sympathetic investors. Funding is not a particular challenge during Phases I&ndash;II. The optimistic case for Phases III&ndash;IV (1 UHV STM) puts the R&D resources at <b>$2.8 million</b>, O(10 employees), O(3 years). The worst case (1000 UHV STMs) balloons this to <b>$7.8 billion</b>. Before refining the [ballparks for cost](https://gist.github.com/philipturner/8d1d6680932b01fae4700b6f20da5198#conclusion), we ought to clarify the reasons the worst case might happen.

> <b>$20B+</b> was spent on EUV R&D over ~30 years (public + private funding).<br>
> ASML alone invested <b>€6B+</b> in EUV between 2012&ndash;2020.
>
> <b>Early Stage:</b> U.S. government (DoE, DARPA) funded foundational research.<br>
> <b>Mid-Stage:</b> SEMATECH and EUV LLC transitioned it to industry.<br>
> <b>Commercialization:</b> ASML (with Intel/TSMC/Samsung backing) turned it into a production-ready tool.
>
> Today, ASML is the sole producer of EUV lithography machines. The effort stands as one of the most ambitious public-private R&D collaborations in tech history.

We assert that, due to fundamental limits, semiconductor lithography cannot use smaller light wavelengths in a practical manner. Resolution is ultimately limited to approximately the light wavelength. <b>Conventional approaches (photolithography, protein engineering) have zero chance of extending Moore’s Law, beyond a mediocre ~2x with high-NA.</b> Therefore, <i>massively parallel</i> or <i>kilogram scale</i> molecular manufacturing is the only viable way to miniaturize transistors at scale. However, reaching that end goal requires so many phases (each with glaring technical issues) that we have very low confidence the entire pathway will work. Even if it does, the end goal will likely be reached after decades of work. After massive mobilization of R&D resources from a growing number of groups that accept the futility in extending Moore’s Law scaling.

The design space for low atom count products has already been explored to the maximum possible depth. Source: http://www.imm.org/documents/IMM_Roadmap_Applications.pdf

Robert Wolkow’s group revealed a glaring technical issue with packaging. Silicon dangling bonds are the only chemical substrate for scalable logic fabrication today. They are air-sensitive free radical sites, instantly destroyed by a single oxygen molecule. UHV-tight vacuum seals set an incredibly high standard for porosity. To be conservative, assume all near-term products face this challenge.

<b>Single SiDB logic gates can be fabricated with Phase III technology.</b> These electronic structures are aligned to the 2D Si(100) surface lattice. As a result, Wolkow’s group made great strides toward automating the CAD and physical modeling. In contrast, 3D amorphous carbon structures are a maximally poor substrate for finely tailoring electronic properties.

It may be possible to encapsulate a single SiDB radical in a hole free, nano-sized seal fabricated with 3D mechanosynthesis. This feat would be a major step toward Phase V (perfect vacuum seals) and Phase VIII (packaging electronic chips for mass distribution). It may be economical to ship customizable SiDB logic patterns to hobbyists for an accessible price. This business model is analogous to research grade [solid phase polypeptide synthesis](https://en.wikipedia.org/wiki/Solid-phase_synthesis).

> Note the extreme barrier to entry for acquiring custom chips with EUV-enabled nodes. On the order of $10,000 per wafer, which may pale in comparison to the design and software licensing cost.
>
> We assert that physical objects aligned to the crystal lattice are orders of magnitude easier to design. Translational symmetry is the reason DNA origami designs scale to very large building block counts.

Our product will be soldered onto PCBs, serving similar functions to [TTL](https://en.wikipedia.org/wiki/Transistor%E2%80%93transistor_logic) components from the 1960's. The continued existence of the vinyl record market demonstrates profitability of "retro" technologies, with transistor counts matching the earliest digital hardware. The novelty of possessing the first "atomically precise" logic will distinguish our product from other discrete transistors.