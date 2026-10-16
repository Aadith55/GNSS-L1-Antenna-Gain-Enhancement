<div align="center">
  <h1>GNSS L1 Antenna Gain Enhancement</h1>
  <p><strong>Design, simulation and experimental validation of compact printed GNSS antennas</strong></p>
  <p>Target band: <strong>GNSS L1 · 1.57542 GHz</strong><br>
  FR-4 · Ansys HFSS · CST Studio Suite · Vector Network Analyzer</p>
</div>

---

## Project at a glance

This repository documents two related but **separate** gain-enhancement studies for a printed microstrip antenna. Phase 1 changes the patch and ground-plane geometry; Phase 2 adds an SRR superstrate and scales it into arrays.

| Workstream | Enhancement approach | Best reported result | Evidence |
|---|---|---|---|
| **Phase 1** | Four symmetric patch corner slots + rectangular Defected Ground Structure (DGS) | **2.38 dB simulated peak gain**, up by 0.20 dB from its baseline | HFSS simulation, fabricated prototype and measured S11 |
| **Phase 2** | Single Split Ring Resonator (SRR) superstrate, then 2×2 and 4×4 arrays | **2.65 dB reported realized gain** for the 4×4 array, up by 0.72 dB from its baseline | CST simulation results |

> **How to read the results:** The phases have different baseline models and must not be treated as one continuous comparison. Values and units are transcribed from the source documents. Phase 1's measured result is an S11 measurement; its source paper is inconsistent about whether the 2.38 dB gain is simulated or measured, so this repository labels it as **simulated** pending clarification. Phase 2 results are simulation results, not measured prototype results.

## Contents

- [Phase 1: DGS and patch slotting](#phase-1-dgs-and-patch-slotting)
- [Phase 2: SRR superstrate arrays](#phase-2-srr-superstrate-arrays)
- [Key design parameters](#key-design-parameters)
- [Repository guide](#repository-guide)
- [Reproducibility and interpretation notes](#reproducibility-and-interpretation-notes)
- [Source documents](#source-documents)

---

<a id="phase-1"></a>
## Phase 1: DGS and patch slotting

### Design approach

A rectangular microstrip patch was designed for GNSS L1 on FR-4. The proposed configuration adds four symmetric 5 × 5 mm corner slots to the radiating patch and two rectangular 15 × 5 mm slots in the ground plane. The source paper describes the design and simulation in Ansys HFSS.

<table>
  <tr>
    <td align="center" width="50%">
      <strong>Radiating patch</strong><br><br>
      <img src="results/phase-1-dgs-slots/Patch%20-%20Top%20View.png" alt="Top view of the patch with symmetric corner slots and inset feed" width="420">
    </td>
    <td align="center" width="50%">
      <strong>Defected ground structure</strong><br><br>
      <img src="results/phase-1-dgs-slots/Ground%20Plane%20View.png" alt="Ground-plane view showing rectangular DGS slots" width="420">
    </td>
  </tr>
</table>

### Simulated performance

| Metric | Baseline patch | DGS + patch corner slots |
|---|---:|---:|
| Reported S11 | −19.71 dB | −20.82 dB |
| Simulated peak gain | 2.18 dB | 2.38 dB |
| Reported −10 dB bandwidth interval | 1.524–1.560 GHz | 1.540–1.577 GHz |

The reported simulated peak gain increases by **0.20 dB** versus the Phase 1 baseline.

<table>
  <tr>
    <td align="center" width="50%">
      <strong>S11 comparison</strong><br><br>
      <img src="results/phase-1-dgs-slots/S11%20patch%20vs%20w%20slots%2CDGS.png" alt="S11 comparison of the basic patch and proposed DGS plus slots design" width="440">
    </td>
    <td align="center" width="50%">
      <strong>Radiation patterns</strong><br><br>
      <img src="results/phase-1-dgs-slots/E%20and%20H%20Plane%20Graph.png" alt="E-plane and H-plane radiation pattern plots" width="440">
    </td>
  </tr>
</table>

### Prototype and measurement

The proposed design was fabricated on double-sided copper-clad FR-4. The paper reports measurement of the reflection coefficient using a Rohde & Schwarz ZVL vector network analyzer.

| Measured quantity | Reported value |
|---|---:|
| S11 at measured resonance | −22.186 dB |
| Measured resonant frequency | 1.632 GHz |
| Centre frequency used in the design | 1.575 GHz |
| GNSS L1 range quoted by the paper | 1.559–1.610 GHz |

**Frequency-offset caveat:** the measured resonance at 1.632 GHz is approximately 57 MHz above the 1.575 GHz design centre and about 22 MHz above the upper edge of the 1.559–1.610 GHz range quoted in the paper. Do not describe this measurement as a resonance centered in the cited GNSS L1 range.

<table>
  <tr>
    <td align="center" width="50%">
      <strong>Simulated vs measured S11</strong><br><br>
      <img src="results/phase-1-dgs-slots/S11%20simulated%20vs%20measured.png" alt="Comparison of simulated and measured S11" width="440">
    </td>
    <td align="center" width="50%">
      <strong>VNA result</strong><br><br>
      <img src="results/phase-1-dgs-slots/VNA%20Measurements.jpg" alt="Vector network analyzer measurement" width="440">
    </td>
  </tr>
  <tr>
    <td align="center">
      <strong>Fabricated patch</strong><br><br>
      <img src="results/phase-1-dgs-slots/Fabricated%20Top%20View.jpg" alt="Fabricated antenna patch top view" width="360">
    </td>
    <td align="center">
      <strong>Fabricated ground plane</strong><br><br>
      <img src="results/phase-1-dgs-slots/Fabricated%20Ground%20Plane.jpg" alt="Fabricated antenna ground plane" width="360">
    </td>
  </tr>
</table>

---

<a id="phase-2"></a>
## Phase 2: SRR superstrate arrays

### Design approach

The Phase 2 report uses CST Studio Suite to investigate a split ring resonator (SRR) above the patch as a parasitic superstrate. The study progresses from a single SRR to 2×2 and 4×4 arrays. The source report describes the superstrate as an electromagnetic lens intended to shape the near-field distribution and increase realized gain.

### Reported simulation comparison

| Configuration | S11 at 1.575 GHz | Reported peak realized gain | Change vs. Phase 2 baseline |
|---|---:|---:|---:|
| Baseline patch | −22.414 dB | 1.93 dB | — |
| Single SRR superstrate | −21.80 dB | 2.26 dB | +0.33 dB |
| 2×2 SRR array | −19.96 dB | 2.45 dB | +0.52 dB |
| 4×4 SRR array | −20.05 dB | 2.65 dB | +0.72 dB |

The **4×4 SRR configuration** has the highest reported gain in the Phase 2 comparison. All values in this table are from simulation; no physical measurement of the SRR-array gain is included in this repository.

### Single SRR superstrate

<table>
  <tr>
    <td align="center" width="50%">
      <strong>Geometry</strong><br><br>
      <img src="results/phase-2-srr-metasurface/Single%20SRR%20superstrate.png" alt="Single SRR superstrate geometry" width="420">
    </td>
    <td align="center" width="50%">
      <strong>S11</strong><br><br>
      <img src="results/phase-2-srr-metasurface/S11%20Single%20SRR%20superstrate.png" alt="S11 result for the single SRR superstrate" width="420">
    </td>
  </tr>
</table>

<p align="center">
  <strong>Reported gain</strong><br><br>
  <img src="results/phase-2-srr-metasurface/Gain%20Single%20SRR%20superstrate.png" alt="Gain result for the single SRR superstrate" width="560">
</p>

### 2×2 SRR array

<table>
  <tr>
    <td align="center" width="50%">
      <strong>Geometry</strong><br><br>
      <img src="results/phase-2-srr-metasurface/2x2%20SRR%20superstrate%20design.png" alt="2 by 2 SRR superstrate array geometry" width="420">
    </td>
    <td align="center" width="50%">
      <strong>S11</strong><br><br>
      <img src="results/phase-2-srr-metasurface/S11%202x2%20SRR%20superstrate%20design.png" alt="S11 result for the 2 by 2 SRR array" width="420">
    </td>
  </tr>
</table>

<p align="center">
  <strong>Reported realized gain: 2.45 dB</strong><br><br>
  <img src="results/phase-2-srr-metasurface/Gain%202x2%20SRR%20superstrate%20design.png" alt="Gain result for the 2 by 2 SRR array" width="560">
</p>

### 4×4 SRR array

<table>
  <tr>
    <td align="center" width="50%">
      <strong>Geometry</strong><br><br>
      <img src="results/phase-2-srr-metasurface/4x4%20SRR%20superstrate%20design.png" alt="4 by 4 SRR superstrate array geometry" width="420">
    </td>
    <td align="center" width="50%">
      <strong>S11</strong><br><br>
      <img src="results/phase-2-srr-metasurface/S11%204x4%20SRR%20superstrate%20design.png" alt="S11 result for the 4 by 4 SRR array" width="420">
    </td>
  </tr>
</table>

<p align="center">
  <strong>Reported realized gain: 2.65 dB</strong><br><br>
  <img src="results/phase-2-srr-metasurface/Gain%204x4%20SRR%20superstrate%20design.png" alt="Gain result for the 4 by 4 SRR array" width="560">
</p>

### Electromagnetic field distributions

<table>
  <tr>
    <th align="center">2×2 array</th>
    <th align="center">4×4 array</th>
  </tr>
  <tr>
    <td align="center">
      <strong>E-field</strong><br><br>
      <img src="results/phase-2-srr-metasurface/E-Field%202x2%20SRR%20superstrate%20design.png" alt="E-field distribution for the 2 by 2 SRR array" width="400">
    </td>
    <td align="center">
      <strong>E-field</strong><br><br>
      <img src="results/phase-2-srr-metasurface/E-Field%204x4%20SRR%20superstrate%20design.png" alt="E-field distribution for the 4 by 4 SRR array" width="400">
    </td>
  </tr>
  <tr>
    <td align="center">
      <strong>H-field</strong><br><br>
      <img src="results/phase-2-srr-metasurface/H-Field%202x2%20SRR%20superstrate%20design.png" alt="H-field distribution for the 2 by 2 SRR array" width="400">
    </td>
    <td align="center">
      <strong>H-field</strong><br><br>
      <img src="results/phase-2-srr-metasurface/H-Field%204x4%20SRR%20superstrate%20design.png" alt="H-field distribution for the 4 by 4 SRR array" width="400">
    </td>
  </tr>
</table>

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
| Rectangular DGS slots | Two slots, 15 × 5 mm each |
| Feed-line width | 3 mm |
| Inset notch | 8.6 × 1.555 mm |
| Simulation sweep stated in paper | 1–2 GHz, 301 points |
| Reported loss tangent | 0.02 |

### Phase 2: SRR superstrate

| Parameter | Reported value |
|---|---:|
| Target frequency | 1.575 GHz |
| Substrate / superstrate | FR-4 |
| Relative permittivity | 4.4 |
| Layer thickness | 1.6 mm |
| SRR trace width | 2 mm |
| 2×2 superstrate height | 11 mm in the array-optimization section |
| 4×4 superstrate height | 40 mm in the array-optimization section |

**Geometry note:** the Phase 2 report's parameter table also lists a 12 mm layer separation. Verify the intended height for each final configuration against the CST model before treating the listed dimensions as definitive.

---

## Repository guide

~~~text
.
├── README.md
├── .gitignore
├── docs/
│   ├── project-notes.md
│   ├── results-summary.md
│   └── reports/
│       ├── phase-1-wams-paper.pdf
│       └── phase-2-end-semester-report.pdf
├── models/
│   ├── GNSS FINAL.aedt
│   └── 4x4.cst
└── results/
    ├── phase-1-dgs-slots/
    └── phase-2-srr-metasurface/
~~~

| Location | Contents |
|---|---|
| [Phase 1 results](results/phase-1-dgs-slots/) | Geometry, S11 plots, radiation patterns, prototype photos and VNA measurement |
| [Phase 2 results](results/phase-2-srr-metasurface/) | Single-SRR, 2×2 and 4×4 geometries, S11/gain plots and field distributions |
| [Simulation models](models/) | Ansys Electronics Desktop project and CST Studio Suite project |
| [Supporting reports](docs/reports/) | Source paper and end-semester project report |
| [Results summary](docs/results-summary.md) | Compact phase-wise numerical comparison |
| [Project notes](docs/project-notes.md) | Data interpretation, model inventory and limitations |

## Reproducibility and interpretation notes

- **Phase-specific baselines:** Phase 1's baseline gain is 2.18 dB; Phase 2's baseline gain is 1.93 dB. These are separate studies, not a single progression.
- **Gain measurement ambiguity:** the Phase 1 paper's results table lists 2.38 dB as simulated peak gain, while the conclusion calls it measured gain. The experimental-validation section reports S11 measurement but does not document a gain-measurement method. This README therefore labels 2.38 dB as simulated pending clarification.
- **Frequency offset:** the Phase 1 measured resonance is reported at 1.632 GHz, above the GNSS L1 range quoted in the paper. This is an important limitation when describing the experimental validation.
- **Phase 2 evidence:** gain and S11 values are simulation results in the report; the repository does not include measured SRR-array results.
- **Model availability:** native project files can depend on software version, solver settings, linked files and cached results. Their presence in GitHub does not guarantee that results will reproduce without additional setup.

## Source documents

- [Phase 1 — WAMS conference paper](docs/reports/phase-1-wams-paper.pdf)
- [Phase 2 — End-semester project report](docs/reports/phase-2-end-semester-report.pdf)

