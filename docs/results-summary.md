# Results summary

The tables below reproduce the source documents' reported values. Keep Phase 1 and Phase 2 separate because their baseline models and simulation configurations differ.

## Phase 1 — DGS + symmetric patch slots

| Metric | Basic L1 patch | Proposed DGS + slots |
|---|---:|---:|
| Simulated S11 | −19.71 dB | −20.82 dB |
| Simulated peak gain | 2.18 dB | 2.38 dB |
| Reported −10 dB bandwidth interval | 1.524–1.560 GHz | 1.540–1.577 GHz |

The paper reports measured S11 of −22.186 dB at a resonance of 1.632 GHz. The paper cites 1.559–1.610 GHz as the GNSS L1 range, so the measured resonance is above the cited range by approximately 22 MHz.

**Gain-label caveat:** the paper's results table lists 2.38 dB as simulated peak gain, but the conclusion calls it measured gain. Its experimental-validation section reports S11 measurement without specifying a gain-measurement method. The repository labels 2.38 dB as simulated pending clarification.

## Phase 2 — SRR superstrate progression

| Configuration | Reported S11 at 1.575 GHz | Reported peak realized gain | Gain change vs. Phase 2 baseline |
|---|---:|---:|---:|
| Baseline patch | −22.414 dB | 1.93 dB | — |
| Single SRR | −21.80 dB | 2.26 dB | +0.33 dB |
| 2×2 SRR array | −19.96 dB | 2.45 dB | +0.52 dB |
| 4×4 SRR array | −20.05 dB | 2.65 dB | +0.72 dB |

The gain-change values are differences against the Phase 2 baseline as tabulated in the report. These are simulation values; no measured gain for the SRR configurations is provided here.

## Parameter discrepancy to verify

The Phase 2 report's parameter table lists a 12 mm layer separation. Its array-optimization section later states 11 mm for the 2×2 configuration and 40 mm for the 4×4 configuration. Confirm the final geometry in the native CST project before reusing these values.
