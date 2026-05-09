# Perovskite Solar Cell Degradation Study

A semester-long experimental analysis of perovskite solar cell performance and degradation conducted in Spring 2026 as part of a quantum engineering lab course. The project involved fabricating a perovskite solar cell, measuring its current-voltage and quantum efficiency characteristics weekly over eight weeks, and tracking how performance evolved over time under continuous light exposure.

**Team:** B Team — Madelyne Dusbabek, Gregory Lowman, Jay Hall
**Cell:** R22 | 8 pixels | 0.14 cm² active area per pixel

> Raw measurement data is stored on a shared team Google Drive and is not included in this repository. All notebooks reference that data via Google Colab's Drive mount. The completed PDF exports of every notebook are included here so results, plots, and analysis are fully viewable without access to the original data.

---

## Experiment Overview

Each week, the team measured:
- **J-V curves** (current density vs. voltage) for all 8 pixels using a solar simulator (P_in = 99.8 mW/cm²)
- **EQE spectra** (External Quantum Efficiency vs. wavelength, 350–750 nm) using a monochromated light source

From the J-V data, the following parameters were extracted each week per pixel:
- Short-circuit current density (J_sc)
- Maximum power point (V_pmax, J_pmax)
- Power Conversion Efficiency (PCE)
- Fill Factor (FF)

All measurements included **uncertainty propagation** using standard error of the mean, voltage step resolution, and solar simulator calibration uncertainty, producing error bars on all reported values.

---

## Notebooks

| File | Week | Description |
|------|------|-------------|
| `DataCollection1-S26.pdf` | Week 1 | Initial J-V and EQE measurements (PDF only) |
| `EQEBaselineData-V4.ipynb` | Week 2 | EQE baseline — all 8 pixels measured and compared to literature |
| `DataCollection2-S26-SE.ipynb` | Week 4 | J-V analysis with full uncertainty workflow; PCE and EQE tracked over time with error bars |
| `DataCollection3_S26.ipynb` | Weeks 5–6 | Two-week dataset (including TA-collected break week data); cumulative PCE vs. time and EQE subplots updated |
| `DataCollection4_S26.ipynb` | Week 7 | Weighted linear regression on PCE over time; chi-squared and residual analysis; two-pixel slope comparison via z-test |
| `DataCollection5-S26.ipynb` | Week 8 | Final data collection; LED spectra analysis from stressing stations; histogram and Gaussian fitting; EQE comparison across all seven time points |
| `Final_Project.ipynb` | Final | Full research analysis: series and shunt resistance over time, sigma clipping, advanced regression, and summary figures |

---

## Analysis Progression

**Weeks 1–2 (Baseline):** Established initial J-V and EQE baselines. EQE peaked near 475 nm (~0.95) and dropped sharply at 700 nm, consistent with literature values for perovskite absorbers.

**Weeks 3–6 (Degradation Tracking):** PCE and EQE were measured weekly and plotted as cumulative time series. Uncertainty was propagated from three sources: statistical (SE of repeated current measurements), instrumental (voltage step resolution), and systematic (solar simulator calibration). Pixel 6 was consistently the highest-performing pixel throughout the study.

**Week 7 (Regression Analysis):** Weighted linear regression was applied to PCE vs. time for each pixel. Reduced chi-squared (χ²/ν >> 1) and patterned residuals indicated that a linear model was not an adequate description of the degradation — suggesting a decay model would be more appropriate.

**Week 8 (Final Collection + Spectra):** LED emission spectra from all stressing stations were loaded from an HDF5 file, plotted, and analyzed with histograms and Gaussian fits at selected wavelengths. Bimodal distributions at certain wavelengths indicated non-uniform light delivery across stations.

**Final Project:** Advanced analysis extending the weekly data into full resistance characterization, outlier removal, and comparative pixel regression.

---

## Technologies

- Python 3 (Google Colab)
- `pandas`, `numpy`, `matplotlib` — data processing and plotting
- `scipy`, `sklearn` — regression and statistics
- `h5py` — HDF5 file access for LED spectra data
- Google Drive — shared team data storage

## Supporting Documents

- `Project Memo.docx` — project context and objectives
- `Summary Slide.pptx` — presentation slide summarizing key findings
