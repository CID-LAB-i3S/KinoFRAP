# FRAP live-cell analysis

Data analysis pipeline for FRAP kinetochore live-cell imaging experiments described in:

> Soares-de-Oliveira, Okada, Kletter et al. (2026) Low kinetochore-microtubule occupancy leaves a mitotic memory by delaying checkpoint silencing.

> bioRxiv preprint: https://doi.org/10.64898/2026.01.26.701783

## Goal

Goal of the pipeline is to quantify fluorescence recovery after total or partial photobleaching of MAD1 signal at kinetochores. 

## How to Use This Repository

### 1. Install dependencies

Download and install the relevant Python packages (e.g. using the Anaconda + conda management system):

| Package | Version |
|---|---|
| python | 3.12.7 |
| jupyter | 4.2.5 |
| pandas | 2.2.2 |
| numpy | 1.26.4 |
| matplotlib| 3.11.0 |
| skimage | 0.26.0 |
| scipy | 1.18.0 | 
| aicsimageio| 4.14.0 |


### 2. Repository structure

The code is divided into:
- **Notebooks** — Jupyter notebooks for analysis of partially bleached kinetochores OR totally bleacked kinetochores

### 3. Expected input



### 4. Output



## Demo

To run the demo:

1. Download the example files from the folder `Demo`.
2. Open the `Partial_FRAP.ipynb` Jupyter notebook in Jupyter.

### `Partial_FRAP.ipynb`

**Inputs** — 
- `.csv`
- `.csv`
- `.csv`
- `.csv`

Define the locations of these tables in the input cell.

**Outputs**:
- `....csv` — contains ...
- `...csv` — contains ...



**Runtime**: The total run time of the demo on a normal computer should be less than ... seconds.

## Note

This repository is mainly published for documentation purposes within the context of a series of custom experiments, and was not optimised for user-friendliness. Please feel encouraged to ask for help if needed.
