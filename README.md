# QuintHorizon

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/)

Open-source computational framework designed to algorithmically identify and evaluate bright stellar candidate anchors ($V_{\text{app}} \le 2.50$) across seven key Mesoamerican archaeological sites spanning nearly 3,000 years (1400 BCE to 1500 CE). The framework partitions the celestial sphere into a fivefold radial geometry ($5 \times 72^\circ$ quintants) incorporating dynamic precession corrections, atmospheric extinction models (Schaefer 1993), and horizon visibility constraints.

---

## Project Overview

This repository provides an automated archaeoastronomical pipeline built to model historical sky orientations and evaluate structural alignments against specific archaeological epochs. 

The source code is structured into major analytical components:
1. **Epoch Generator (`run_epoch`):** Handles site-specific geographic configurations (latitude, longitude, elevation, platform height, and terrain masks), transforms International Celestial Reference System (ICRS) coordinates to FK5 epoch-adjusted frames using `astropy`, and calculates atmospheric extinction and true first-emergence/horizon visibility.
2. **Geometric Grid & Candidate Selection:** Partitions the normalized horizon into sub-quadrants, evaluates magnitude limits, and isolates primary sector anchors.
3. **Inter-Quintant & Meridional Re-candidates:** Evaluates symmetrical pairing across quintant boundaries using multi-criteria scoring (brightness, symmetry, and equatorial centrality) alongside north/south meridional alignments.
4. **Statistical & Permutation Suite:** Executes rigorous analytical validation, including framework-rotation permutations ($\Delta\theta \sim U[-36^\circ, +36^\circ]$, $N=10,000$), Monte Carlo azimuth simulations, and bootstrap resampling.
5. **20-Star Integrated Selector (`run_20_selector`):** Employs linear sum assignment across multi-epoch datasets to isolate consistent multi-epoch astronomical anchors.

---

The complete computational execution log, including epoch-specific geometric grids, weight-sensitivity evaluations, and 10,000-iteration permutation test results across all seven sites, is available in outputs/QuintHorizon_Full_Compilation_Report.md.
