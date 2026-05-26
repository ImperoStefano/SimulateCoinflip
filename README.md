Coin Flip Simulator 🪙

A single-file web application that simulates up to 100,000 coin flips and visualizes the results in real time.

Features ⚡

3D Animation: Physics-mimicking requestAnimationFrame loop that lands precisely on the generated outcome.
Outcome Distribution: Bar chart showing absolute counts of Heads vs. Tails.
Convergence Chart: Line chart tracing the relative frequency of heads toward the 50% theoretical threshold.
Live Dashboard: Instant tracking of counts and percentage distributions.
Dark Mode: Native system preference matching via CSS custom properties.

Quick Start 🚀

No installations, no package managers, no build steps.

git clone https://github.com/ImperoStefano/SimulateCoinflip.git
cd SimulateCoinflip

Open directly in your browser:
open coin-flip-simulator.html       (macOS)
xdg-open coin-flip-simulator.html   (Linux)
start coin-flip-simulator.html      (Windows)

Under the Hood 🛠️

The computational core executes synchronously before the animation begins, guaranteeing instant results even when processing 100,000 flips (O(n)):

const results = new Array(n);
let heads = 0;
for (let i = 0; i < n; i++) {
results[i] = Math.random() < 0.5;
if (results[i]) heads++;
}

To maintain rendering performance, the chart dataset is automatically downsampled to a maximum of 300 evenly spaced data points.

Mathematical Foundation 📊

The convergence chart calculates and maps the relative frequency (p_k) of the "Heads" outcome after each sampled interval k:

p_k = (sum of X_i from i=1 to k) / k

Where X_i ~ Bernoulli(0.5). According to the Law of Large Numbers (Strong Law), the sample average converges almost surely to the theoretical expected value:

p_k -> 0.5 as k -> infinity

Customization ⚙️

Core parameters can be tweaked directly inside coin-flip-simulator.html:

Max Flips: max="100000" attribute on the HTML input.
Colors: --amber-* and --blue-* inside the :root CSS block.
Animation Speed: speed = 26 and friction 0.91 inside animateCoin().
Chart Resolution: The 300 step factor constant in the convergence loop.

File Structure 📂

.
├── coin-flip-simulator.html
└── README.md

External dependency: Chart.js v4.4.1 (via CDN).

Author 🧔

Stefano Kolta - ImperoStefano (https://github.com/ImperoStefano)

License 📝

MIT License
