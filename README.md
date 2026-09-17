# APCDD1 cell surface marker benchmarking

Code, raw flow cytometry data and environment to reproduce the analyses and figures in:

> Alrik L. Schörling, Alison Salvador, Pedro Rifes, Erno Hänninen, Amalie Holm Nygaard, Gaurav Singh Rathore, Jenny Nelander, Josefine Rågård Christiansen, Simone Møller Jensen, Jonathan Christos Niclis, Emma Gustafsson, Patrick Aldrin-Kirk, Yu Zhang, Malin Parmar & Agnete Kirkeby. *APCDD1 shows high specificity for ventral midbrain dopaminergic progenitors in a cell surface marker benchmarking study.* npj Parkinson's Disease (2026). https://doi.org/10.1038/s41531-026-01467-9

## Installation

Change to the Benchmarking directory

```bash
cd Benchmarking
```

Create the conda environment from the .yml

```bash
conda env create -f py_flow_env.yml
```

Activate the env

```bash
conda activate py_flow_env
```

Install FlowCal

```bash
pip install flowcal
```

The R analysis uses the packages loaded at the top of `R/Benchmarking.Rmd` (installation commands are included there, commented out).

## Repository structure

```
Benchmarking/
├── py_flow/            # Python flow cytometry analyses (Jupyter notebooks + raw .fcs files)
├── R/                  # R Markdown for statistical analysis and figures (qRT-PCR)
├── color_palettes/     # Scientific colour maps (batlow, bilbao, devon, oslo, tokyo) used in the plots
└── py_flow_env.yml     # conda environment for the Python analyses
```

### py_flow

Each subdirectory is a self-contained project with its notebook(s), raw `.fcs` files, and `output/` and `figs/` directories for exported tables and figures. Per-sample FACS plots are written to `facs_plots/`, which is not version controlled.

| Project | Description | Notebook |
| --- | --- | --- |
| `regional_spec` | RC17 regional specificity assay: quality control, cut-offs, processing, comparison with manual gating, and FAMD | `regional_spec.ipynb` |
| `regional_spec_d11` | Day 11 vs day 16 cVM cells | `regional_spec_d11.ipynb` |
| `regional_spec_h9` | H9 regional specificity assay | `regional_spec_h9.ipynb` |
| `regional_spec_kolf` | KOLF regional specificity assay | `regional_spec_kolf.ipynb` |
| `regional_spec_stem_cells` | Marker expression in undifferentiated stem cells (APCDD1, and all markers) | `AS 230213 stem cells APCDD1/regional_spec_stemcells_apcdd1.ipynb`, `AS 240614 stem cells all markers/stem cells all markers.ipynb` |
| `clinical_panel` | FOXA2/LMX1A co-expression panel, including APCDD1 sensitivity and specificity | `clinical_panel.ipynb` |

Notebooks use paths relative to their own directory, so start Jupyter from (or set the working directory to) the notebook's folder and run the cells from top to bottom.

### R

`R/Benchmarking.Rmd` contains the statistical analysis and figure generation for the qRT-PCR data in `R/data/`. Open `R/Benchmarking.Rproj` (or knit the `.Rmd`) so that paths resolve relative to the `R` directory. The full R code and data are available upon request.

## Citation

If you use this code or data, please cite the article above.


## License

A license to use this code and data is granted under the terms of the MIT License. See the LICENSE file for details. Copyright (c) 2026 kirkebylab.