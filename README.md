## README

This script performs automated image analysis for neuroprotection experiments by quantifying **neurite morphology, soma area, and cell-associated metrics** from microscopy images across multiple experimental folders.

### What it does
- Detects **neurites and soma regions** using intensity thresholding, morphology, and skeletonization.
- Calculates metrics including neurite length, neurite/soma area, cell count, neurite coverage, branches per cell, and a composite **Total Repair Score**.
- Matches images to experimental conditions using a **plate map** based on well IDs parsed from image filenames.
- Optionally applies image QC filtering and generates diagnostic overlays.
- Summarizes results at the **image, replicate/well, and condition** levels.
- Generates replicate and condition-level plots when plotting is enabled.

### Before running
Update `ROOT_DIR` and `OUTPUT_ROOT` under **MULTI-EXPERIMENT SETTINGS**. Each experiment folder should contain microscopy images and, when `USE_PER_FOLDER_PLATEMAP = True`, a `platemap.csv` or `platemap.xlsx` file containing at minimum the well and corresponding experimental condition information.

### Main outputs
Each experiment produces:
- `AllImages`, `Included`, and `Excluded` image-level results
- `PerWell_Avg` and `PerWell_Stats`
- `Condition_Summary`
- `Summary` of analysis settings
- `UNMAPPED` and `PARSE_FAIL` QC sheets
- Image overlays showing detected soma and neurite structures
- Summary plots for selected metrics

A `_MASTER_INDEX.xlsx` file is also generated to summarize all experiments processed in the batch.

**Note:** Analysis parameters controlling thresholding, soma detection, skeleton pruning, filtering, and plotting are located near the top of the script and should be kept consistent when comparing experiments.
