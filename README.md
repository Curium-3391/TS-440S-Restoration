# TS-440S-Restoration

Kenwood TS-440S restoration and diagnostic lab notebook.

## Current state
**2026-10-14: Investigation ongoing. No root cause or failed part confirmed.**
The TS-440S occasionally displays a frequency before reverting to dots. The PLL2 TP5 voltage was observed near 7.86–7.87 V with very little DMM-captured change. The next priority is verifying **actual PLL Unlock/UL signals in normal receive**, rather than interpreting the Semi-Self Test's physical F.LOCK switch check as a PLL diagnosis.

## Read first
- [Diagnostic status](docs/diagnostic-status.md) — concise evidence, caveats, and next tests
- [Measurement log](docs/measurement-log.md) — reported voltages, RF snapshots and measurement limitations
- [Hypothesis ledger](docs/hypotheses.md) — observed vs. open vs. corrected claims
- [Service manual index](docs/service-manual-index.md) — page map for user's original Kenwood Service Manual
- [2026-10-14 session notes](logs/2026-10-14.md)

## Scientific discipline
1. Measurements at different RF nodes are **not simultaneous**; unstable/unlocked PLL can change between probe placements. Prefer trends and presence of recognizable signals to overly precise arithmetic on snapshots.
2. Record physical probe attenuation, oscilloscope channel compensation, coupling, ground lead, bandwidth, timebase, trigger and expected waveform when possible.
3. Preserve negative and conflicting evidence. A frequency counter result on a complex mixer waveform does not provide a spectrum.
4. **Important correction:** Test 45 'LOCK' refers to the front-panel F.LOCK switch read by IC53 8255 port B0. The CPU µPD7800 C2 PLL **Unlock** line is distinct (manual p.21, Table 11). Do not conflate them.
5. No RF alignment, coil adjustment, or component replacement based solely on the present data.

## Source manual
The owner supplied a 116-page Kenwood TS-440S Service Manual (filename `kenwood--ts-440s--service--ID2607.pdf`). It is not redistributed here. Use the manual index to locate PLL Unit pp.72–73, Digital/Control pp.76–77, and Semi-Self Test pp.25–26.

Maintenance convention: after each meaningful diagnostic stage, update the dated session log, measurement ledger, hypothesis ledger and current status, referencing the relevant schematic and distinguishing observation from interpretation.
