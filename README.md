# GNSS L1 Antenna Gain Enhancement

**Two design investigations for a compact printed GNSS L1 antenna:** rectangular Defected Ground Structure (DGS) with symmetric patch slotting, followed by an SRR-superstrate / metasurface approach.

The target band is GNSS L1 around **1.575 GHz**. This work studies gain enhancement on a low-cost FR-4 substrate while retaining acceptable input matching.

> **Important:** This repository separates the two phases and their baselines. The DGS/slot results in the WAMS paper and the SRR-superstrate results in the project report come from different design iterations; their baseline numbers should not be treated as one direct comparison.

## Phase 1 — Rectangular DGS and symmetric patch slotting

The first design uses a rectangular microstrip patch on FR-4, four symmetric corner slots in the radiating patch, and two rectangular defects in the ground plane. The design was simulated in Ansys HFSS and a physical prototype was fabricated and measured with a Rohde & Schwarz ZVL vector network analyzer.

| Configuration | Simulated S11 | Simulated peak gain |
|---|---:|---:|
| Basic L1 patch | -19.71 dB | 2.18 dB |
| Proposed patch with DGS and corner slots | -20.82 dB | 2.38 dB |

The paper reports a simulated -10 dB bandwidth of **1.540–1.577 GHz (37 MHz)** for the proposed design. The fabricated prototype's measured S11 was **-22.186 dB at 1.632 GHz**. Simulation and measurement values are listed separately because the measured resonance is shifted from the simulated target.

**Reported geometry:** FR-4, relative permittivity 4.4, substrate thickness 1.6 mm; patch 58.5 × 44.2 mm; substrate 95 × 82 mm; four 5 × 5 mm patch slots; 15 × 5 mm DGS slots; inset feed.

## Phase 2 — SRR superstrate and metasurface scaling

The second phase investigates a split-ring resonator (SRR) superstrate placed above the patch. It starts with one SRR, then scales to 2×2 and 4×4 periodic arrays. The report describes the SRR layer as a parasitic director / electromagnetic lens intended to shape the near-field and focus radiation toward broadside.

| Configuration | Reported S11 | Reported peak gain |
|---|---:|---:|
| Baseline patch | -22.414 dB | 1.93 dB |
| Single SRR superstrate | -21.8 dB | 2.26 dB |
| 2×2 SRR array | -19.96 dB | 2.45 dB |
| 4×4 SRR array | -20.05 dB | 2.65 dB |

Relative to the Phase 2 baseline, the 4×4 configuration improves reported peak gain by **0.72 dB**, while its reported S11 remains below -10 dB. The report gives a superstrate height of **11 mm** for the 2×2 design and **40 mm** for the 4×4 design, with SRR trace width 2 mm and FR-4 thickness 1.6 mm.

These are simulation results from the project report; they are not presented as measured gain results.

## Repository structure

```text
.
├── README.md
├── docs/
│   ├── project-notes.md
│   └── results-summary.md
├── models/
│   ├── hfss/
│   └── cst/
└── results/
    ├── phase-1-dgs-slots/
    └── phase-2-srr-metasurface/
```

The `results/` folders are for exported simulation plots, antenna geometry screenshots, field plots, radiation patterns and (for Phase 1) prototype/VNA photographs. Add original exports where available; avoid screenshots with unreadable axes or cropped legends.

## Simulation files

Native HFSS/CST project files should be placed under `models/` once uploaded. Open them with the compatible version of Ansys Electronics Desktop / HFSS or CST Studio Suite. Some solvers store cached results or dependencies separately; verify that the model opens and results are available before relying on exported values.

## Reproducibility and interpretation

- Keep simulation and measurement results explicitly labeled.
- Include frequency sweep, boundary conditions, material properties and solver settings alongside plots when available.
- Gain units are reproduced as stated in the source documents; do not silently relabel them as dBi unless the simulation report confirms that convention.
- The values in this README are source-reported and should be checked against exported plots before final publication.

## Source documents

The technical summary is based on the WAMS final CRC paper for Phase 1 and the end-semester project report for Phase 2. The full source documents are not included here; add them only after deciding what to make public and confirming publication/personal-information considerations.
