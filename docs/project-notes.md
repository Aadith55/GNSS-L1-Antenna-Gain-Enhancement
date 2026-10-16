# Project notes

## Scope

This repository documents two related but distinct gain-enhancement investigations for a printed embedded GNSS L1 antenna.

- **Phase 1:** Rectangular Defected Ground Structure (DGS) in the ground plane plus four symmetric corner slots in the patch; simulated in Ansys HFSS and followed by fabrication and VNA measurement.
- **Phase 2:** SRR superstrate, starting from a single split ring and progressing to 2×2 and 4×4 arrays; the report describes this as a metasurface / electromagnetic-lens approach.

## Keep the datasets separate

The Phase 1 paper's baseline gain is 2.18 dB, while the Phase 2 report's baseline gain is 1.93 dB. These are phase-specific models and should not be merged into a single gain progression. Compare configurations only within the same phase unless the matching geometry, substrate, solver setup and reference plane have been verified.

## Tool and model inventory

- The Phase 1 paper identifies Ansys HFSS as the simulation tool.
- The supplied AEDT project includes named designs for DGS, DGS with slots, and SRR variants.
- The supplied CST project is named for the 4×4 SRR array.
- The Phase 2 report describes CST Studio Suite in its methodology. Before assigning every plot to a specific native model, verify the design name and solver setup that produced it.

## Suggested next commit

Add final simulation exports to the matching `results/phase-*` directory and name them descriptively, e.g. `s11-baseline-vs-dgs.png`, `s11-srr-count-comparison.png`, `gain-srr-count-comparison.png`, and `array-4x4-e-field.png`.
