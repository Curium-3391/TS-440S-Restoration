# Measurement log

Source: user measurements and oscilloscope photos during conversation, 2026-10-14. Numbers represent **reported snapshots**, not an instrument-calibrated simultaneous trace. Unit and location labels should be retained faithfully. Do not infer detailed RF relationships from readings recorded at different times.

## Digital / DC
| Node | Instrument / condition | Reported reading |
|---|---|---|
| TP5 / R70 right (initial checks) | HP 34401A | ~7.8729 V / ~7.8715 V |
| TP5 / R70 right | HP 34401A Min/Max while tuning | both ~7.86 V; ordinary ~7.87 V |
| R70 other side | DC | ~7.8715 V (initial) |
| Q16 B | HP 34401A DC | 4.084 mV |
| Q16 E | HP 34401A DC | 1.834 mV |
| Q16 C | HP 34401A DC | ~7.8 V |
| R68 two ends | HP 34401A DC | 4.1 and 4.0 mV (earlier both reported ~4.14 mV) |
| R67 IC9-side | DC | ~4.1 mV |
| IC9 Pin 8 | HP 34401A DC | 4.0 mV |
| IC1 Pin 8 | DC | 1.5 V |
| IC4 Pin 8 | DC | 1.3 V |
| IC18 Pin 8 | DC | 2.9 V |
| IC7 Pin 8 | DC | ~7.0025 V; R58 endpoints ~7.8 V and 7.0025 V; manual drawing labels 2.4 V at a nearby *different net* — do not claim typo proved |
| IC7 Pin 6/7 | DC | ~3.4 V (drawing ~3.5 V) |
| IC8 / IC12 / IC14 specified supply points | DC | ~6.9 V each |
| IC10 Pin 8 | DC | ~0.76 V |
| IC10 Pin 4 / Pin 5 / Pin 6 | DC | 1.55 / 1.55 / 4.93 V |

## RF / time domain
| Location | Reported reading or observation | Remarks |
|---|---|---|
| Q20 / R81 neighborhood | ~59.6429 MHz repeated; around ~59.6249 MHz on an earlier capture | P2200 ×10 confirmed for these measurements |
| IC9 Pin 3 | ~9.02703 MHz | RF roughly 9 MHz, limited by probe grounding / frequency-meter uncertainty |
| IC7 Pin 2 | ~2.03659 / ~1.98810 MHz in ×1 trials; ×10 waveform roughly 2 MHz by visual cycles | The ×1 probe's ~6 MHz bandwidth & added capacitance make comparisons conditional |
| IC7 Pin 5 | ~4.63889 / ~4.55455 MHz in ×1 trials; ×10 visually ~4–4.5 MHz, cursor rough estimate ~4.39 MHz | Marker placement imprecise; automatic counter sometimes cannot lock |
| IC7 Pin 1 | ~6.38217 and ~3.29605 MHz in ×1 trials; ×10 has no reliable single periodic waveform | No proof of dead mixer |
| IC8 Pin 2 | 58.2558 MHz RF | Measured on separate occasion |
| IC10 Pin 8 | 6.03614 MHz periodic waveform | HP 54503A, visibly repeatable |
| IC11 Pin 2 | 5.96499 MHz periodic RF | Via IC10 / LPF |
| IC11 Pin 5 | 35.7827 MHz RF | Separate moment from Pin 2 |
| IC11 Pin 1 | complex waveform | MIX3 output; single waveform cannot prove specific mixing product |
| C123 T10 side | 42.4576 MHz auto frequency | Complex waveform; not a spectrum |
| C70 both sides | RF-like ringing centered on scope trigger | Ground-shorted probe near PCB gave similar ringing; grounding probe away from PCB and also near PCB produced no comparable ringing. Indeterminate transient / coupling cause |
| IC11 & IC12 Pin 2 and 5 early tests | no recognizable waveform initially | Superseded for IC11 Pin2/5 by later positive RF findings |

## Measurement methodology adopted
- Keep scope channel ratio matching physical P2200 probe at ×10; short ground for RF.
- Beware of input loading and poor trigger/autofrequency on mixed/noisy waveforms; use manual cursors or spectrum tools when appropriate.
- Only infer broad frequency ranges and signal presence if RF snapshots were taken non-synchronously during PLL instability.
- Preserve unsuccessful tests, caveats, and superseding measurements rather than rewriting them as confirmed faults.

| PLL Unit J6 Pin 2 (UL) | HP 34401A DC, panel showing dots | **0.52 V**; observed lowish UL, verify pin orientation and normal-state comparison |
