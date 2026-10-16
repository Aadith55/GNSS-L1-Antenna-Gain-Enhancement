# Project notes

## Scope

This repository documents two related but distinct gain-enhancement studies for a printed GNSS L1 antenna.

- **Phase 1:** A rectangular Defected Ground Structure (DGS) in the ground plane plus four symmetric patch corner slots. The source paper describes Ansys HFSS simulation, prototype fabrication and VNA measurement.
- **Phase 2:** An SRR superstrate study progressing from a single split ring to 2×2 and 4×4 arrays. The project report describes CST Studio Suite simulation.

## Source files and models

- [Phase 1 source paper](reports/phase-1-wams-paper.pdf)
- [Phase 2 project report](reports/phase-2-end-semester-report.pdf)
- **models/GNSS FINAL.aedt** is an Ansys Electronics Desktop project.
- **models/4x4.cst** is a CST Studio Suite project.
- The report describes CST for Phase 2. Confirm the design name and solver setup in the native files before attributing each plotted result to a specific model.

## Keep the datasets separate

The Phase 1 paper's baseline gain is 2.18 dB, while the Phase 2 report's baseline gain is 1.93 dB. These are phase-specific models and must not be merged into one gain progression. Compare configurations within each phase unless the geometry, substrate, solver setup, and reference plane have been verified as equivalent.

## Results organization

- **results/phase-1-dgs-slots/** contains patch and ground-plane geometry, S11 comparisons, radiation patterns, fabrication photos and VNA imagery.
- **results/phase-2-srr-metasurface/** contains single-SRR, 2×2 and 4×4 geometry images, S11 and gain plots, and E-field / H-field distributions.
- **docs/results-summary.md** contains phase-wise numerical comparisons.
- The root **README.md** is the project overview and embeds the main figures.

## Interpretation and validation notes

- **Gain ambiguity in Phase 1 source:** the results table lists 2.38 dB as simulated peak gain, while the conclusion calls it measured gain. The experimental-validation section describes S11 measurement but does not document a gain-measurement method. The README and results summary therefore label 2.38 dB as simulated pending clarification.
- **Measured frequency offset:** the paper reports measured S11 of −22.186 dB at 1.632 GHz. The same paper cites 1.559–1.610 GHz as the GNSS L1 range, so the reported resonance is above that range and should not be described as centered in-band.
- Treat Phase 2 gain and S11 values as simulation results unless measurement data is explicitly provided.
- The Phase 2 report gives different layer-separation values in different sections: 12 mm in a parameter table versus 11 mm for the 2×2 configuration and 40 mm for the 4×4 configuration. Verify the intended settings against the native model.
- Native project files may depend on software version, linked files, solver settings or cached results. Their presence in the repository does not by itself guarantee reproducibility.
