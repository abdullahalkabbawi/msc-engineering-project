# MSc THz Coplanar-Waveguide Resonator Simulation

> **Current status:** the baseline gap-coupled resonator has been analysed, a merged interdigital-capacitor (IDC) coupled geometry has been developed, and IDC cavity-length and mesh-convergence sweeps are in progress.

The detailed, results-focused project page is available in [index.md](index.md).

## Project Title

Simulation of a High-Q Terahertz Coplanar-Waveguide Resonator with Capacitive and Interdigital Coupling for Quantum Engineering and 6G Applications

## Project Overview

This MSc project investigates a terahertz-frequency coplanar-waveguide resonator with two capacitive couplers. It compares simple gap coupling with interdigital-capacitor coupling for a target frequency near 0.8 THz. The broader research context includes high-frequency resonator readout and possible excitation through picosecond-scale current pulses.

The project uses Ansys Lumerical FDTD to simulate the electromagnetic behaviour and analyse how cavity length, coupling geometry, local mesh resolution, and material properties affect resonance frequency, field confinement, transmission, bandwidth, and quality factor.

## Latest Results

The simple-gap sweep confirms the expected coupling trend:

| Coupling gap | Resonance (THz) | FWHM (GHz) | Loaded \(Q_L\) |
| ---: | ---: | ---: | ---: |
| 5 µm | 0.6675 | 49.25 | 13.55 |
| 3 µm | 0.6670 | 58.78 | 11.35 |
| 1 µm | 0.6454 | 92.09 | 7.01 |
| 0.8 µm | 0.6399 | 101.03 | 6.33 |

Reducing the gap strengthens coupling, broadens the resonance, and lowers loaded \(Q\). A cavity-length fit gives an effective index of approximately 2.68 and an end correction of approximately 12.38 µm.

The latest IDC geometry uses two couplers integrated into one merged signal-conductor polygon:

```text
Port 1 -> left IDC -> central CPW cavity -> right IDC -> Port 2
```

The current IDC design uses 12 µm coupling length, 0.6 µm finger width, 0.45 µm finger spacing, 0.5 µm tip spacing, and four fingers per side. Its resonance is below the 0.8 THz target, so the central cavity is being swept from 30 to 70.75 µm.

## Main Objectives

1. Review THz waveguide resonators, capacitive couplers, IDC couplers, and trap-assisted current generation.
2. Build a Lumerical FDTD model of a THz CPW resonator with simple-gap and IDC couplers.
3. Extract resonance frequency, transmission/reflection response, electric-field confinement, and Q-factor.
4. Investigate the effect of gap size, IDC geometry, cavity length, mesh resolution, and material parameters on resonator performance.
5. Analyse whether picosecond current pulses contain suitable THz-frequency components to excite the resonator.
6. Discuss relevance to quantum engineering and future 6G THz communication technologies.

## Software

- Ansys Lumerical FDTD
- Ansys Lumerical CHARGE / DEVICE, if required
- Python, NumPy, Pandas, Matplotlib, and SciPy
- MATLAB, optional
- Overleaf / LaTeX
- GitHub for version control and project organisation

## Repository Structure

```text
docs/              Project planning, meeting notes, literature notes
lumerical/         FDTD/CHARGE models, Lumerical scripts and exported data
data/              Raw and processed datasets
python_analysis/   Python scripts and notebooks for analysis
results/           Final plots, field maps and spectra
report/            Report drafts, figures and final PDF
poster/            Poster figures and final PDF
references/        Papers and BibTeX files
```

## Key Outputs

- THz resonance and reference-normalised transmission spectra
- Electric-field maps at resonance
- Lorentzian fits and Q-factor extraction
- Gap-size, IDC-geometry, cavity-length, and mesh-convergence sweeps
- FFT analysis of picosecond current pulses
- Comparison of simple-gap and IDC coupling
- Final MSc report and A1 poster

## Project Guidelines

The preliminary report must include:

- Introduction
- Aims and objectives
- Resources required
- Gantt chart
- Risk assessment

The preliminary report should be no more than 4 pages.

Final report figures should have captions, numbered labels, readable text, axes, scales, and units. The `results/` folder should contain polished figures rather than messy screenshots.

The final MSc report is expected to be around 40-50 pages, roughly 10,000-15,000 words, with appendices separate.

The poster must be A1 portrait using the school poster template. The template indicates 58 pt Arial bold title, 32 pt Arial bold subheadings, and 24 pt Arial paragraph text.

## Large File Guidance

Lumerical files can become very large. For very large `.fsp` files or exported datasets, use Git LFS or keep them in OneDrive/University storage and upload scripts, figures, and smaller processed data.

## Author

Abdullah Alkabbawi  
MSc Electrical and Electronic Engineering  
James Watt School of Engineering  
University of Glasgow  
Academic Year: 2025-2026
