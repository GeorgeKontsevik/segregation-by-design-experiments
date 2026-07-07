# segregation-by-design-experiments

---

[![OSA-improved](https://img.shields.io/badge/improved%20by-OSA-yellow)](https://github.com/aimclub/OSA)

Built with:

![numpy](https://img.shields.io/badge/NumPy-013243.svg?style={0}&logo=NumPy&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458.svg?style={0}&logo=pandas&logoColor=white)
![scipy](https://img.shields.io/badge/SciPy-8CAAE6.svg?style={0}&logo=SciPy&logoColor=white)
![tqdm](https://img.shields.io/badge/tqdm-FFC107.svg?style={0}&logo=tqdm&logoColor=black)

---

## Table of Contents

- [Overview](#overview)
- [Installation](#installation)
- [Getting Started](#getting-started)
- [Architecture](#architecture)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [Citation](#citation)

---

## Overview

This repository contains a Python experiment suite for studying street-pattern structure, route geometry, and service-accessibility relationships in cities. It is intended for developers, researchers, and GIS-oriented data scientists who work with geospatial analysis and transport morphology workflows. The project is organized around script-driven experiments and batch analysis rather than a single application, with command-line entrypoints for city-level studies and related route or accessibility analyses. If you want to run one of the experiments, start with the Getting Started instructions.

---

## Installation

**Prerequisites:** requires Python >=3.11

Install segregation-by-design-experiments using one of the following methods:

**Build from source:**

1. Clone the segregation-by-design-experiments repository:
```sh
git clone https://github.com/GeorgeKontsevik/segregation-by-design-experiments
```

2. Navigate to the project directory:
```sh
cd segregation-by-design-experiments
```

3. Install the project dependencies:

```sh
pip install -r requirements.txt
```

---

## Getting Started

**Prerequisites**

- Python 3.11
- Project dependencies from `pyproject.toml`
- Prepared geospatial inputs for the script you want to run

**Quick start**

1. Install the project dependencies.

2. Run the street-pattern city workflow:

```bash
python run_street_pattern_city.py --place "Montreal, Canada"
```

3. For route-pattern analysis, provide prepared city bundles and run the experiment script:

```bash
python route_pattern_street_pattern/run_experiments.py --cities warsaw_poland berlin_germany
```

4. For route-directness analysis, run the corresponding experiment script with prepared inputs:

```bash
python route_directness_street_pattern/run_experiments.py --cities warsaw_poland berlin_germany
```

If your data is stored in different locations, use the script arguments shown in each file’s `parse_args()` definition, such as `--joint-input-root`, `--output-root`, `--service-accessibility-root`, or `--roads` where supported.

---

## Architecture

This repository is organized as a script-driven experiment suite rather than a single application. The top level groups related analyses into separate Python packages such as `route_directness_street_pattern`, `route_pattern_street_pattern`, `service_accessibility_street_pattern`, `pt_street_pattern_cross_city`, and `polyclinic_access_components`, with additional one-off scripts for generating and rendering maps, comparisons, and reference chunks.

Most workflows follow the same broad pattern: a runner script reads prepared geospatial inputs, applies analysis logic from shared modules or imported pipeline helpers, and writes structured outputs such as GeoJSON, Parquet, pickle files, figures, and summary tables. Several scripts also support CLI arguments for selecting cities, modalities, input roots, and cache behavior.

The `polyclinic_access_components` area appears to be a self-contained workflow with its own run scripts, recomputation helpers, diagnostics rendering, and dated output directories. Its contents suggest batch generation of city-level figures and component outputs, but the repository context does not show a deeper service boundary.

The street-pattern experiments depend on shared geospatial and plotting libraries, plus prepared city bundles under `aggregated_spatial_pipeline/outputs/joint_inputs` in some scripts. For example, route-pattern and route-directness analyses both resolve per-city input bundles, combine street-pattern classifications with transit route data, and then generate per-city and cross-city summaries.

Overall, the codebase is organized around offline geospatial analysis pipelines: prepare inputs, run city-level or cross-city experiments, and inspect the resulting artifacts. The provided tree does not show microservices, asynchronous workers, or a single central runtime.

---

## Documentation

A detailed segregation-by-design-experiments description is available [here](https://github.com/GeorgeKontsevik/segregation-by-design-experiments/tree/main/docs).

---

## Contributing

- **[Report Issues](https://github.com/GeorgeKontsevik/segregation-by-design-experiments/issues)**: Submit bugs found or log feature requests for the project.

- **[Submit Pull Requests](https://github.com/GeorgeKontsevik/segregation-by-design-experiments/tree/main/CONTRIBUTING.md)**: To learn more about making a contribution to segregation-by-design-experiments.

---

## Citation

If you use this software, please cite it as below.

### APA format:

    GeorgeKontsevik (2026). segregation-by-design-experiments repository [Computer software]. https://github.com/GeorgeKontsevik/segregation-by-design-experiments

### BibTeX format:

    @misc{segregation-by-design-experiments,

        author = {GeorgeKontsevik},

        title = {segregation-by-design-experiments repository},

        year = {2026},

        publisher = {github.com},

        journal = {github.com repository},

        howpublished = {\url{https://github.com/GeorgeKontsevik/segregation-by-design-experiments}},

        url = {https://github.com/GeorgeKontsevik/segregation-by-design-experiments}

    }

---