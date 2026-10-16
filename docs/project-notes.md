# Project notes

## Scope

This repository documents two related but distinct gain-enhancement investigations for a printed GNSS L1 antenna.

- **Phase 1:** Rectangular Defected Ground Structure (DGS) in the ground plane plus four symmetric corner slots in the patch. The design was simulated in Ansys HFSS, fabricated, and measured with a VNA.
- **Phase 2:** An SRR superstrate study progressing from a single split ring to 2×2 and 4×4 arrays. The project report describes this as a metasurface / electromagnetic-lens approach.

## Keep the datasets separate

The Phase 1 paper's baseline gain is 2.18 dB, while the Phase 2 report's baseline gain is 1.93 dB. These are phase-specific models and must not be merged into a single gain progression. Compare configurations within each phase unless the geometry, substrate, solver setup, and reference plane have been verified as equivalent.

## Tool and model inventory

- The Phase 1 paper identifies Ansys HFSS as the simulation tool.
- The repository contains `models/GNSS FINAL.aedt`, an Ansys Electronics Desktop project.
- The repository contains `models/4x4.cst`, a CST Studio Suite project for the 4×4 SRR array.
- The Phase 2 report describes CST Studio Suite in its methodology. Confirm the design name and solver setup in the native files before attributing individual plots to a specific model.

## Results organization

- `results/phase-1-dgs-slots/` contains patch and ground-plane geometry images, S11 comparisons, radiation-pattern plots, fabrication photos, and VNA measurement imagery.
- `results/phase-2-srr-metasurface/` contains single-SRR, 2×2 and 4×4 geometry images, S11 and gain plots, and E-field / H-field distributions.
- `docs/results-summary.md` provides the phase-wise numerical comparison.
- The root `README.md` presents the project narrative and embeds the principal figures.

## Interpretation notes

- Label Phase 1 simulated gain separately from measured S11.
- Treat Phase 2 gain and S11 values as simulation results unless measurement data is explicitly provided.
- The Phase 2 report gives different layer-separation values in different sections. Verify those values against the native models before treating them as definitive.
- Native project files may depend on software version, linked files, solver settings, or cached results. Their presence in the repository does not by itself guarantee reproducibility.
