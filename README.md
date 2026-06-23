# FRAP live-cell analysis

Data analysis pipeline for FRAP kinetochore live-cell imaging experiments described in:

> Soares-de-Oliveira, Okada, Kletter et al. (2026) Low kinetochore-microtubule occupancy leaves a mitotic memory by delaying checkpoint silencing.

> bioRxiv preprint: https://doi.org/10.64898/2026.01.26.701783

## Goal

Goal of the pipeline is to quantify fluorescence recovery after total or partial photobleaching of MAD1 signal at kinetochores. 

## How to Use This Repository

### 1. Install dependencies

Download and install the relevant Python packages (e.g. using the Anaconda + conda management system for Windows, macOS, and Linux):

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

- Point-coordinates (across all frames) of the extremes of the "BLEACH" kinetochore (sum-projected). After bleaching, the extremes corresponds to the unbleached region of the kinetochore (partial bleaching) OR the leftover kinetochore signal (total bleaching).
- Point-coordinates (across all frames) of the extremes of the "NON-BLEACH" sister kinetochore (sum-projected).
- Point-coordinates (across all frames) of the extremes of the "CONTROL" unperturbed kinetochore (sum-projected).
- Point-coordinates (1st frame) of the BG (from cytoplasmic region where there will be no kinetochore throughout the movie).
- .tif of sum-projected movie.
- Frame-to-second conversion file (provided by microscope software).

### 4. Output
- Based on the coordinates, the script will define a ROI rectangle with the length equal to the distance of the coordinates in the pre-bleaching frame and a width of 0.6 microns.
- In case of the "partial" FRAP, an additional smaller ROI rectangle is defined with length equal to the distance of the coordinates of the remaining kinetochore signal. 
- The length of the bleach region rectangle will correspond to the difference of the rectangles defined above.
- The background ROIs are centered around the XY coordinates that were defined, and will have a side length of 0.86 microns. 
- MAD1 kinetochore fluorescence intensity (SKT, corrected) will be corrected for fluctuations in the cytoplasmatic fluorescent signal as described in the following equation: SKT, corrected = SKT / (a x time + b); SKT: kinetochore MAD1 raw integrated density; a, b: constants provided by a linear fit of the cytoplasmatic MAD1 raw integrated density.
- Output table contains signal recovery data (sum signal in the respective ROI) corrected to background fluctuations (Column "Background Bleach-Correction") and normalised to pre-bleach signal (Column "Ratio with control"). 


## Demo

To run the demo:

1. Download the example files from the folder `Demo`.
2. Open the `Partial_FRAP.ipynb` Jupyter notebook in Jupyter.

### `Partial_FRAP.ipynb`

**Inputs** — 
- `BKT.csv` (BLEACH kinetochore coordinates, "Slice" corresponds to timepoint)
- `SKT.csv` (NON-BLEACH kinetochore coordinates, "Slice" corresponds to timepoint)
- `CKT.csv` (CONTROL kinetochore coordinates, "Slice" corresponds to timepoint)
- `BG.csv` (BACKGROUND coordinates)
- `Movie_003_Partial.tif` (sum-projected demo movie)
- `Time.xlsx`(Real-time data for each frame in seconds, with bleach frame = 0)

Define the locations of these tables in the input cell.

**Outputs**:
- `[MOVIE NAME].xlsx`
- Overlay file (MOVIE + ROIs) that shows the ROI rectangles that were created based on the user-defined XY coordinates.


**Runtime**: The total run time of the demo on a normal computer should be less than 10 seconds.

## Note

This repository is mainly published for documentation purposes within the context of a series of custom experiments, and was not optimised for user-friendliness. Please feel encouraged to ask for help if needed.
