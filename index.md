---
title: Terahertz CPW Resonator Project
description: MSc project on THz coplanar-waveguide resonators, capacitive coupling, and interdigital-capacitor coupling using Ansys Lumerical FDTD.
---

# Design and Simulation of Terahertz Coplanar-Waveguide Resonators

## Project overview

This MSc project investigates terahertz coplanar-waveguide (CPW) resonators in Ansys Lumerical FDTD. The aim is to understand how cavity and coupler geometry control resonance frequency, transmission, bandwidth, field confinement, and loaded quality factor.

The present design targets approximately **0.8 THz** and compares:

1. simple capacitive-gap coupling; and
2. interdigital-capacitor (IDC) coupling.

The work combines electromagnetic simulation, scripted geometry generation, S-parameter processing, Lorentzian fitting, and quality-factor analysis.

## Baseline CPW design

The initial cavity length is estimated using the half-wave relation

$$
L_{\mathrm{cav}}=\frac{c}{2n_{\mathrm{eff}}f_0}.
$$

For \(f_0=0.8~\mathrm{THz}\) and \(n_{\mathrm{eff}}=2.65\),

$$
L_{\mathrm{cav}}\approx70.75~\mu\mathrm{m}.
$$

| Parameter | Symbol | Current value |
| --- | ---: | ---: |
| Centre-conductor width | \(s\) | \(10~\mu\mathrm{m}\) |
| CPW slot gap | \(w\) | \(6.6\)-\(7.5~\mu\mathrm{m}\) |
| Target frequency | \(f_0\) | \(0.8~\mathrm{THz}\) |
| Initial effective index | \(n_{\mathrm{eff}}\) | 2.65 |
| Initial cavity length | \(L_{\mathrm{cav}}\) | \(70.75~\mu\mathrm{m}\) |

## Gap-coupled resonator

The baseline two-port geometry is:

```text
Input feedline | gap | CPW cavity | gap | output feedline
```

Reducing the gap increases coupling capacitance and therefore broadens the resonance:

$$
\text{smaller gap}\Rightarrow\text{stronger coupling}
\Rightarrow\text{larger bandwidth}\Rightarrow\text{lower }Q_L.
$$

The loaded quality factor is extracted from the fitted resonance using

$$
Q_L=\frac{f_0}{\Delta f},
$$

where \(\Delta f\) is the full width at half maximum.

### Gap-sweep results

The first reference-normalised resonance produced the following fitted values:

| Coupling gap | \(f_0\) (THz) | \(\Delta f\) (GHz) | \(Q_L\) |
| ---: | ---: | ---: | ---: |
| \(5~\mu\mathrm{m}\) | 0.6675 | 49.25 | 13.55 |
| \(3~\mu\mathrm{m}\) | 0.6670 | 58.78 | 11.35 |
| \(1~\mu\mathrm{m}\) | 0.6454 | 92.09 | 7.01 |
| \(0.8~\mu\mathrm{m}\) | 0.6399 | 101.03 | 6.33 |

The results follow the expected trend: stronger capacitive coupling increases bandwidth and reduces loaded \(Q\).

## Effective index and end correction

The simulated resonance is not fully described by the simple half-wave model because capacitive loading and fringing fields increase the effective electrical length. A corrected model is

$$
f_0=\frac{c}{2n_{\mathrm{eff}}\left(L_{\mathrm{cav}}+\Delta L\right)}.
$$

Fitting the cavity-length sweep gave approximately:

$$
n_{\mathrm{eff}}\approx2.68,
\qquad
\Delta L\approx12.38~\mu\mathrm{m}.
$$

The resonator therefore behaves as though it is longer than its drawn metal length.

## Interdigital-capacitor coupling

The current design replaces each simple gap with an IDC:

```text
Port 1 -> left IDC -> central CPW cavity -> right IDC -> Port 2
```

Two IDCs are used for the two-port \(S_{21}\) resonator. The latest geometry uses one merged signal-conductor polygon so that the IDC fingers are integral parts of the conductor rather than disconnected metal objects.

| IDC parameter | Symbol | Current value |
| --- | ---: | ---: |
| IDC length | \(L_{\mathrm{IDC}}\) | \(12~\mu\mathrm{m}\) |
| Finger width | \(w_f\) | \(0.6~\mu\mathrm{m}\) |
| Finger gap | \(g_f\) | \(0.45~\mu\mathrm{m}\) |
| Tip gap | \(g_{\mathrm{tip}}\) | \(0.5~\mu\mathrm{m}\) |
| Fingers per side | \(N\) | 4 |
| Total fingers | \(2N\) | 8 |

IDC coupling increases with finger count and overlap length, and decreases with finger spacing:

$$
N\uparrow,\quad L_{\mathrm{IDC}}\uparrow,\quad g_f\downarrow
\quad\Rightarrow\quad C_c\uparrow.
$$

The geometry now forms the intended input-IDC-cavity-IDC-output topology. Its strongest simulated feature remains below \(0.8~\mathrm{THz}\), indicating that IDC loading has increased the cavity's effective electrical length.

## Current cavity-length sweep

The next sweep will test central cavity lengths of:

| Trial | \(L_{\mathrm{cav}}\) |
| ---: | ---: |
| 1 | \(30~\mu\mathrm{m}\) |
| 2 | \(40~\mu\mathrm{m}\) |
| 3 | \(50~\mu\mathrm{m}\) |
| 4 | \(60~\mu\mathrm{m}\) |
| 5 | \(70.75~\mu\mathrm{m}\) |

The physical cavity mode will be identified as the spectral feature that shifts consistently with \(L_{\mathrm{cav}}\). If the resonance is below the target frequency, the cavity must be shortened; if it is above the target, it must be lengthened.

## Mesh strategy

The smallest IDC dimensions require local mesh overrides around the two couplers. The rest of the CPW can remain more coarsely meshed to control runtime.

| Region | Recommended mesh |
| --- | ---: |
| IDC local \(dx\) | \(0.05\)-\(0.10~\mu\mathrm{m}\) |
| IDC local \(dy\) | \(0.05\)-\(0.10~\mu\mathrm{m}\) |
| IDC local \(dz\) | \(0.2\)-\(0.5~\mu\mathrm{m}\) |
| General CPW region | Coarser global mesh |

Mesh-convergence testing is required before final \(Q\)-factor values are reported.

## Data processing

The exported transmission data is \(\lvert S_{21}\rvert^2\), so its dB conversion is

$$
S_{21,\mathrm{dB}}=10\log_{10}\left(\lvert S_{21}\rvert^2\right).
$$

For a straight-CPW reference simulation,

$$
S_{21,\mathrm{norm,dB}}
=10\log_{10}\left(
\frac{\lvert S_{21}\rvert^2}
{\lvert S_{21,\mathrm{ref}}\rvert^2}
\right).
$$

Lorentzian fitting is used to obtain \(f_0\), \(\Delta f\), and \(Q_L\). The relationship between internal, coupling, and loaded quality factors is

$$
\frac{1}{Q_L}=\frac{1}{Q_i}+\frac{1}{Q_c}.
$$

## Scaled microwave validation

A direct PCB implementation at \(0.8~\mathrm{THz}\) is impractical because the critical features are micrometre and sub-micrometre scale. A scaled **10 GHz** CPW resonator on a low-loss RF substrate, such as Rogers RO4003C, could validate the underlying resonator and coupling physics using a vector network analyser.

A first-order 10 GHz cavity length is approximately \(10~\mathrm{mm}\). Such a prototype could validate \(S_{11}\), \(S_{21}\), resonance behaviour, capacitive and IDC coupling, and loaded-\(Q\) extraction, although it would not directly demonstrate THz performance.

## Main findings so far

- The half-wave equation provides a useful initial cavity length.
- Fringing fields and capacitive loading increase the effective electrical length.
- Smaller coupling gaps strengthen coupling, broaden the resonance, and lower \(Q_L\).
- IDC coupling introduces stronger and more complex loading than a simple gap.
- The IDC-loaded cavity must be retuned through a central-length sweep.
- Local mesh refinement is essential around sub-micrometre IDC features.

## Current status and next steps

**Status:** simulation and optimisation in progress.

The baseline gap-coupled resonator has been analysed and the merged IDC-coupled geometry has been developed. The immediate tasks are:

1. run the \(30\)-\(70.75~\mu\mathrm{m}\) IDC cavity-length sweep;
2. identify the physical cavity mode;
3. perform IDC mesh-convergence tests;
4. compare gap and IDC coupling using bandwidth and \(Q_L\);
5. prepare final report and poster figures; and
6. develop the optional scaled 10 GHz PCB validation design.

## Tools

- Ansys Lumerical FDTD
- Python, NumPy, Pandas, Matplotlib, and SciPy
- Overleaf / LaTeX
- Git and GitHub Pages

## Repository map

```text
docs/              Project planning, model notes, and technical decisions
lumerical/         Lumerical scripts and exported simulation data
data/              Raw and processed datasets
python_analysis/   S-parameter, spectrum, field, FFT, and Q analysis
results/           Final spectra, field maps, fits, and sweep plots
report/            MSc report sources and figures
poster/            Poster sources and figures
references/        Papers, books, project guidance, and BibTeX files
```
