# GNSS L1 Antenna Gain Enhancement

A two-phase antenna design project exploring gain enhancement for a compact printed antenna targeting the **GNSS L1 band (1.57542 GHz)**. The work studies two different enhancement approaches on FR-4:

1. **Phase 1:** a rectangular Defected Ground Structure (DGS) in the ground plane, combined with four symmetric corner slots in the patch. The design was simulated in Ansys HFSS and a prototype was fabricated and measured.
2. **Phase 2:** a single Split Ring Resonator (SRR) superstrate, progressively scaled to 2×2 and 4×4 SRR arrays. The project report evaluates this approach through electromagnetic simulation.

> **Important:** These are separate design phases with their own baseline antennas and results. Do not treat the Phase 1 and Phase 2 gain values as one continuous comparison. The gain values below are simulation results; the Phase 1 VNA result is a measured S11 value.

## Contents

- [Phase 1 — DGS and symmetric patch slots](#phase-1--dgs-and-symmetric-patch-slots)
- [Phase 2 — SRR superstrate and metasurface arrays](#phase-2--srr-superstrate-and-metasurface-arrays)
- [Key design parameters](#key-design-parameters)
- [Repository layout](#repository-layout)
- [Tools and reproducibility](#tools-and-reproducibility)

---

## Phase 1 — DGS and symmetric patch slots

### Design approach

The baseline is a rectangular microstrip patch designed for GNSS L1. The proposed geometry introduces four symmetric 5 × 5 mm corner slots in the radiating patch and rectangular slots in the ground plane to modify current distribution and reduce unwanted substrate/ground-plane effects.

**Patch geometry**

![Top view of the proposed patch with symmetric corner slots and inset feed](results/phase-1-dgs-slots/Patch%20-%20Top%20View.png)

**Ground-plane geometry**

![Ground-plane view showing the rectangular DGS slots](results/phase-1-dgs-slots/Ground%20Plane%20View.png)

### Simulated performance

| Metric | Baseline patch | Patch with DGS + corner slots |
|---|---:|---:|
| S11 | −19.71 dB | −20.82 dB |
| Peak gain | 2.18 dB | 2.38 dB |
| Reported −10 dB bandwidth | 1.524–1.560 GHz | 1.540–1.577 GHz |

The paper reports a simulated gain increase of **0.20 dB** relative to the Phase 1 baseline.

![S11 comparison: basic patch versus patch with slots and DGS](results/phase-1-dgs-slots/S11%20patch%20vs%20w%20slots,DGS.png)

![E-plane and H-plane radiation pattern results](results/phase-1-dgs-slots/E%20and%20H%20Plane%20Graph.png)

### Fabrication and measurement

A physical prototype was fabricated on double-sided copper-clad FR-4. The reflection coefficient was measured with a Rohde & Schwarz ZVL vector network analyzer.

- **Measured S11:** −22.186 dB
- **Measured resonant frequency:** 1.632 GHz
- The paper notes that the measured resonance is shifted upward from the 1.575 GHz simulated target. The reported measured value should not be confused with the simulated gain result.

![Measured versus simulated S11](results/phase-1-dgs-slots/S11%20simulated%20vs%20measured.png)

| Fabricated patch | Fabricated ground plane |
|---|---|
| ![Fabricated top view](results/phase-1-dgs-slots/Fabricated%20Top%20View.jpg) | ![Fabricated ground plane](results/phase-1-dgs-slots/Fabricated%20Ground%20Plane.jpg) |

**VNA measurement setup/result**

![VNA measurement](results/phase-1-dgs-slots/VNA%20Measurements.jpg)

---

## Phase 2 — SRR superstrate and metasurface arrays

### Design approach

The second phase investigates placing a split ring resonator (SRR) on a dielectric superstrate above the patch. The SRR layer is intended to act as a parasitic director and reshape the near-field phase distribution. The design was then scaled from one SRR to 2×2 and 4×4 arrays.

The Phase 2 report describes these configurations as simulation studies. No physical measurement of the SRR-array gain is claimed here.

### Results comparison

| Configuration | Reported S11 | Peak gain | Gain change vs. Phase 2 baseline |
|---|---:|---:|---:|
| Baseline patch | −22.414 dB | 1.93 dB | — |
| Single SRR superstrate | −21.8 dB | 2.26 dB | +0.33 dB |
| 2×2 SRR array | −19.96 dB | 2.45 dB | +0.52 dB |
| 4×4 SRR array | −20.05 dB | 2.65 dB | +0.72 dB |

The report's best result is the **4×4 SRR array at 2.65 dB peak gain**, which is a reported improvement of **0.72 dB** over that phase's baseline.

### Single SRR

| Geometry | S11 |
|---|---|
| ![Single SRR superstrate geometry](results/phase-2-srr-metasurface/Single%20SRR%20superstrate.png) | ![S11 for the single SRR superstrate](results/phase-2-srr-metasurface/S11%20Single%20SRR%20superstrate.png) |

![Gain for the single SRR superstrate](results/phase-2-srr-metasurface/Gain%20Single%20SRR%20superstrate.png)

### 2×2 SRR array

| Geometry | S11 |
|---|---|
| ![2x2 SRR superstrate geometry](results/phase-2-srr-metasurface/2x2%20SRR%20superstrate%20design.png) | ![S11 for the 2x2 SRR array](results/phase-2-srr-metasurface/S11%202x2%20SRR%20superstrate%20design.png) |

![Gain for the 2x2 SRR array](results/phase-2-srr-metasurface/Gain%202x2%20SRR%20superstrate%20design.png)

### 4×4 SRR array

| Geometry | S11 |
|---|---|
| ![4x4 SRR superstrate geometry](results/phase-2-srr-metasurface/4x4%20SRR%20superstrate%20design.png) | ![S11 for the 4x4 SRR array](results/phase-2-srr-metasurface/S11%204x4%20SRR%20superstrate%20design.png) |

![Gain for the 4x4 SRR array](results/phase-2-srr-metasurface/Gain%204x4%20SRR%20superstrate%20design.png)

**Field distributions**

| 2×2 SRR array | 4×4 SRR array |
|---|---|
| ![E-field for the 2x2 array](results/phase-2-srr-metasurface/E-Field%202x2%20SRR%20superstrate%20design.png) | ![E-field for the 4x4 array](results/phase-2-srr-metasurface/E-Field%204x4%20SRR%20superstrate%20design.png) |
| ![H-field for the 2x2 array](results/phase-2-srr-metasurface/H-Field%202x2%20SRR%20superstrate%20design.png) | ![H-field for the 4x4 array](results/phase-2-srr-metasurface/H-Field%204x4%20SRR%20superstrate%20design.png) |

### Phase 2 geometry notes

The report specifies FR-4 for the patch substrate and superstrate, with relative permittivity 4.4, thickness 1.6 mm and SRR trace width 2 mm. The report's parameter table lists a 12 mm layer separation, while its later array-optimization section describes 11 mm for the 2×2 configuration and 40 mm for the 4×4 configuration. These values need to be checked against the final native models before being treated as definitive design settings.

---

## Key design parameters

### Phase 1: DGS + patch slots

| Parameter | Reported value |
|---|---:|
| Target frequency | 1.575 GHz |
| Substrate | FR-4 |
| Relative permittivity | 4.4 |
| Substrate thickness | 1.6 mm |
| Patch dimensions | 58.5 × 44.2 mm |
| Substrate footprint | 95 × 82 mm |
| Patch corner slots | Four slots, 5 × 5 mm each |
| Rectangular DGS slots | 15 × 5 mm |
| Feed-line width | 3 mm |
| Inset notch | 8.6 × 1.555 mm |
| Simulation sweep in paper | 1–2 GHz, 301 points |
| Reported loss tangent | 0.02 |

### Phase 2: SRR superstrate

| Parameter | Reported value |
|---|---:|
| Target frequency | 1.575 GHz |
| Substrate / superstrate | FR-4 |
| Relative permittivity | 4.4 |
| Layer thickness | 1.6 mm |
| SRR trace width | 2 mm |
| 2×2 superstrate height | 11 mm in array-optimization section |
| 4×4 superstrate height | 40 mm in array-optimization section |

See [the detailed results summary](docs/results-summary.md) and [project notes](docs/project-notes.md) for the phase-wise data and documentation notes.

## Repository layout

```text
.
├── README.md
├── .gitignore
├── docs/
│   ├── project-notes.md
│   └── results-summary.md
├── models/
│   ├── GNSS FINAL.aedt
│   └── 4x4.cst
└── results/
    ├── phase-1-dgs-slots/
    └── phase-2-srr-metasurface/
```

## Tools and reproducibility

- **Ansys HFSS / Electronics Desktop** — antenna modeling and full-wave simulation used in the Phase 1 work; an AEDT model is included in this repository.
- **CST Studio Suite** — used in the Phase 2 report for the SRR-superstrate and array simulation work; the 4×4 CST model is included.
- **Measurement** — Phase 1 S11 measured on a Rohde & Schwarz ZVL VNA.

Native simulation projects can depend on software version, local settings, linked files, and cached result data. Open each project in the relevant software and verify that the expected designs and results are available before attempting to reproduce the reported values.

## Source documents

The descriptions and numerical values in this README are based on the project's WAMS Phase 1 paper and the Phase 2 end-semester report. The complete reports are not included here.
