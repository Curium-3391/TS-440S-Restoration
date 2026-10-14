# Hypothesis ledger — falsifiable, not a parts-replacement list

Status tags: **OBSERVED**, **OPEN**, **WEAKENED**, **CORRECTED**, **NOT TESTED**.

| Claim | Status | Basis / next action |
|---|---|---|
| Radio shows normal-frequency digits briefly, then dots | OBSERVED | Repeatable reported front-panel symptom |
| PLL2 TP5 stays near 7.86–7.87 V under tested conditions | OBSERVED | HP34401A and Min/Max; may miss transients |
| Q16 has insufficient B-E bias at instant measured | OBSERVED / INTERPRETATION | B 4.084 mV vs E 1.834 mV, pin assignment needs independent verification |
| IC9 is defective because Pin 8 ~4 mV | **OPEN, NOT PROVEN** | PLL unlocked phase detector can command rail state; verify feedback and reference |
| IC7 has no mixer output, so is defective | **WEAKENED** | ×1 probe loading and ×10 complex waveform/trigger issues; inputs showed RF |
| IC11 and IC12 both have no RF | **WEAKENED** | IC11 later measured 5.96499 MHz at Pin2 and 35.7827 MHz at Pin5 |
| 42.4576 MHz at C123 proves mixer sum product / missing 30 MHz output | **NOT PROVEN** | Non-simultaneous RF snapshots; complex waveform automatic counter is not spectral analysis |
| Test 45 LOCK digit is PLL locked indication | **CORRECTED — FALSE** | Manual p.21 Table 11 distinguishes 8255 IC53 B0 F.LOCK switch from CPU C2 Unlock |
| Test 45 LOCK=1 proves PLL locked/unlocked | **CORRECTED — FALSE** | Likely F.LOCK switch inactive; verify with F.LOCK switching if necessary |
| Test 48 LSB key scan responds | OBSERVED | Pressing LSB changes relevant digit 1→0 |
| Probe grounded near PCB alone generates ringing | WEAKENED | Later shorted probe near PCB did not recreate waveform; experimental conditions must be tracked |

## Hypothesis discipline
For every future claim add a dated observation, exact node and schematic page, probe/instrument settings, alternatives, and a discriminating next test. Never equate 'not captured' with 'does not exist.' Avoid parts replacement or alignment changes until a failure mode is separately confirmed.
