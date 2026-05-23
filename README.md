# MSc THz Waveguide Resonator Simulation using Ansys Lumerical

## Project Title

Simulation of a High-Q Terahertz Waveguide Resonator Based on Nanometre-Scale Capacitors for Quantum Engineering and 6G Applications

## Project Overview

This MSc project investigates a terahertz-frequency waveguide resonator formed using two nanometre-scale capacitive gaps. The resonator is designed to operate at THz frequencies with high quality factor (Q-factor), with possible excitation through trap-assisted carrier generation producing picosecond-scale current pulses.

The project uses Ansys Lumerical to simulate the electromagnetic behaviour of the resonator and analyse the effect of geometry, material properties, and current pulse characteristics on resonance frequency, field confinement, transmission response, and Q-factor.

## Main Objectives

1. Review THz waveguide resonators, nanogap capacitors, and trap-assisted current generation.
2. Build a Lumerical FDTD model of a THz waveguide resonator with two nanometre-scale capacitors.
3. Extract resonance frequency, transmission/reflection response, electric field confinement, and Q-factor.
4. Investigate the effect of capacitor gap size, material parameters, and geometry on resonator performance.
5. Analyse whether picosecond current pulses contain suitable THz-frequency components to excite the resonator.
6. Discuss relevance to quantum engineering and future 6G THz communication technologies.

## Software

- Ansys Lumerical FDTD
- Ansys Lumerical CHARGE / DEVICE, if required
- Python
- MATLAB, optional
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

- THz resonance spectrum
- Electric field maps at resonance
- Q-factor extraction
- Parameter sweeps for nanogap size and material properties
- FFT analysis of picosecond current pulse
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

## Lumerical File Naming Examples

```text
lumerical/fdtd_models/resonator_v01_basic_geometry.fsp
lumerical/fdtd_models/resonator_v02_gap_sweep.fsp
lumerical/scripts/run_gap_sweep.lsf
lumerical/exported_data/s21_gap_5nm.csv
```

## Python Analysis Scripts

Suggested analysis scripts:

- `q_factor_analysis.py`
- `fft_current_pulse.py`
- `plot_transmission_spectrum.py`
- `plot_field_enhancement.py`

## Example Results

```text
results/spectra/transmission_resonance_1THz.png
results/q_factor/q_vs_gap_size.png
results/field_maps/e_field_nanogap_resonance.png
```

## Large File Guidance

Lumerical files can become very large. For very large `.fsp` or exported data files, use Git LFS or keep them in OneDrive/University storage and only upload scripts, figures, and smaller processed data.

## Commit Practice

Make one commit after each meaningful step:

```bash
git add .
git commit -m "Add initial literature notes on THz resonators"
git commit -m "Add first Lumerical FDTD resonator geometry"
git commit -m "Add gap size sweep results"
git commit -m "Add Q-factor extraction script"
git commit -m "Add preliminary report draft"
```

This gives a clear record of progress, which helps with project conduct and planning.

## Author

Abdullah Alkabbawi  
MSc Electrical and Electronic Engineering  
James Watt School of Engineering  
University of Glasgow  
Academic Year: 2025-2026
