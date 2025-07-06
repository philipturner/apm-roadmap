# Principal Issue

The margin of uncertainty is too large, hindering the ability to specify a bill of materials.<br>
Original margin: [300 (March 2025)](https://gist.github.com/philipturner/8d1d6680932b01fae4700b6f20da5198#next-steps)<br>
Updated margin: >1000 (upper estimate / lower estimate)

| Phase | Parallelism   | Frequency          | Atom Count    | Temperature | Pressure    |
| ----- | ------------: | -----------------: | ------------: | ----------: | ----------: |
| I     | 1             | n/a                | n/a           | 300 K       | 760 torr    |
| II    | 1             | n/a                | n/a           | 300 K       | 760 torr    |
| III   | 1             | 0.001&ndash;10 Hz  | n/a           | 300 K       | ~1e-10 torr |
| IV    | 1&ndash;1000  | 0.001&ndash;0.1 Hz | n/a           | ~150 K      | ~1e-10 torr |
| V     | 1             | 0.1&ndash;100 Hz   | 1e4&ndash;1e7 | ~150 K      | ~1e-10 torr |
| VI    | O(1 trillion) | 100 Hz             | 1e6&ndash;1e9 | ~150 K      | ~1e-10 torr |
| VII   | O(1 trillion) | 1e3&ndash;1e6 Hz   | O(1e23)       | ~150 K      | ~1e-10 torr |
| VIII  | n/a           | n/a                | O(1e23)       | 300 K       | 760 torr    |
