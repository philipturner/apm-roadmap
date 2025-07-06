# Principal Issue

The margin of uncertainty is too large, hindering the ability to specify a bill of materials.<br>
Original margin: [300 (March 2025)](https://gist.github.com/philipturner/8d1d6680932b01fae4700b6f20da5198#next-steps)<br>
Updated margin: >1000 (upper estimate / lower estimate)

| Phase | Parallelism   | Frequency          | Atom Count    | Temperature | Pressure    |
| :---- | ------------: | -----------------: | ------------: | ----------: | ----------: |
| I     | 1             | n/a                | n/a           | 300 K       | 760 torr    |
| II    | 1             | n/a                | n/a           | 300 K       | 760 torr    |
| III   | 1             | 0.001&ndash;10 Hz  | n/a           | 300 K       | ~1e-10 torr |
| IV    | 1&ndash;1000  | 0.001&ndash;0.1 Hz | n/a           | ~150 K      | ~1e-10 torr |
| V     | 1             | 0.1&ndash;100 Hz   | 1e4&ndash;1e7 | ~150 K      | ~1e-10 torr |
| VI    | O(1 trillion) | 100 Hz             | 1e6&ndash;1e9 | ~150 K      | ~1e-10 torr |
| VII   | O(1 trillion) | 1e3&ndash;1e6 Hz   | O(1e23)       | ~150 K      | ~1e-10 torr |
| VIII  | n/a           | n/a                | O(1e23)       | 300 K       | 760 torr    |

Phase III frequency bottlenecked by inverted mode tip registration<br>
Phase IV frequency bottlenecked by Michelson interferometer<br>
Phase IV parallelism mandated by Phase IV frequency + Phase V atom count<br>
Phase V&ndash;VI frequency improves with larger feedstock tanks, given constant UHV bakeout latency

qPlus AFM was eliminated from all phases, avoiding a catastrophic frequency bottleneck. We’ll have to initiate a crystal lattice (2D aromatic or 3D silicon carbide) from a sticky amorphous build plate, or an otherwise mismatched lattice constant. We are effectively performing heteroepitaxy, but with picometer control of the trajectories of sputtered atoms.

Conservative estimate, based on simulation results, is that at least 2 tripod species must exist on physically separate silicon wafers. There are multiple factors that might mandate this. Therefore, we cannot ignore a catastrophic frequency bottleneck from millimeter scale repeatable coarse movements. In the worst case, a coarse tip approach in a 4 K STM setup (no optical access allowed) can take several hours. The repeatability is O(100 nm), after which a fresh inverted mode tip registration restores the positional certainty to ~10 pm.

For simplicity, modeled tank capacity (in feedstock molecule count) as equal to tank atom count. And bakeout latency is 1 day. This model underestimates both of the contributing factors, but the errors cancel, leading to a very accurate number for frequency. One could envision sub-phases of Phase V that grow tank size, exploiting the speed of the previous iteration.
