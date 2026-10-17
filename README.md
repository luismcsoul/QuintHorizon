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
CONFIGURATION TOGGLES & USAGE

You can customize the pipeline behavior using the configuration variables defined at the top of the script:

PRINT_DETAILED_EPOCH: Toggle between epochs ('a' through 'g') to inspect detailed console tables and charts.

EXECUTE_20_SELECTOR: Set to True to run all 7 epochs and the 20-star selection suite, or False to run a single detailed epoch.

PRINT_GEOMETRIC_GRID: Output full candidate pools per sector.

PRINT_STATISTICAL_SUITE: Run epoch-specific statistical validation suites.

PRINT_GRAPH_GENERATOR: Render dynamic site portrait graphs using matplotlib.

---
DATA SOURCES & ROBUST FALLBACK MECHANISM

To guarantee reproducibility and prevent pipeline interruptions caused by external server dropouts, the framework includes a multi-tier fallback architecture within fetch_star_catalog():

Attempt 1: Queries TAPVizieR (Strasbourg) via pyvo.

Attempt 2: Queries Astroquery via the Harvard/NAOJ mirror.

Attempt 3: Fetches directly via the CDS ASU-TSV data stream.

Attempt 4 (Ultimate Fallback): Automatically defaults to a version-controlled static backup dataset (hip_main_safe.csv) stored directly inside the repository.

---
CODERESULTS
The complete computational execution log, including epoch-specific geometric grids, weight-sensitivity evaluations, and 10,000-iteration permutation test results across all seven sites, is available in https://github.com/luismcsoul/QuintHorizon/blob/main/CodeResults.

---
LICENSE
This project is distributed under the MIT License. See the LICENSE file for details.

---
CITATION
If you use this code or framework in your research, please cite it accordingly:

QuintHorizon: Computational Framework for Mesoamerican Archaeoastronomy. Original Concept by Luis Alberto Mejia Clavijo. Submitted to the Journal of Computer Applications in Archaeology (JCAA).
