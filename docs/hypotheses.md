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

## 2026-10-14 critical IC8 / SN16913P correction
- **Correct pin functions validated using SN16913P pinout:** Pin1 MIX output, Pin2 RF input, Pin5 LO input, Pin8 supply, Pin4 ground, Pins3/6/7 decoupling. Earlier assistant repeatedly inverted MIX4 IC8 Pin1 and Pin5. The claim 'IC8 Pin5/TP3 is output and output missing' is **RETRACTED**.
- IC8 Pin2 has stable ~61.1MHz periodic RF; Pin5/TP3 has not shown recognizable waveform under prior x10 probing (this is an LO input, not output), and DMM AC reading is invalid for RF amplitude. IC8 Pin1 DC=5.7848V, but **RF output NOT YET TESTED**.
- Next priority: assess LO presence at IC8 Pin5 / TP3 with known-good probe technique or directly check Pin1 RF output at safe calibrated setup. Avoid condemning IC8 until both inputs and output are understood.


## 2026-10-20 hypothesis update — IC7 to IC8 LO bandpass chain
| Claim | Status | Evidence and next discriminating test |
|---|---|---|
| IC7 MIX5 lacks an input | **WEAKENED** | Pin5 ~4.47321 MHz and Pin2 ~1.95703 MHz, each a clear periodic waveform on separate captures; levels, simultaneity, correct commanded frequencies still unknown |
| C70 is open | **WEAKENED** | Measurable periodic activity on both terminals; does not rule out degraded capacitance/connection or loading |
| Filter T3–T5 is defective or detuned | **OPEN, NOT PROVEN** | C70 T3-side shows repeated waveform, C71 T5-side shows mostly low-level noise; a normally functioning selective filter also removes out-of-band mixer products. Verify actual ~6.6 MHz component or use controlled low-loading frequency-selective test before adjusting slugs |
| C71 is open | **NOT PROVEN** | Both ends show comparably low-level noisy traces at matched 200ns/div / 50mV/div; probes and weak nominal TP3 signal limit conclusion |
| Pin5 ~4.47 MHz vs earlier ~4.96 MHz proves LO drifting | **NOT PROVEN** | Different times/instrument capture; infinite persistence also reflects jitter, trigger and EMI |
| Sequential IC7 input frequencies prove sum 6.43024 MHz outside 6.53–6.63 MHz filter | **CORRECTED — NOT A VALID CONCLUSION** | Non-simultaneous, PLL unlocked, frequency auto method only measures specific trace periods. No product spectrum measurement |
| Radio at 14 MHz means this synthesis chain does not operate | **NOT SUPPORTED** | Manual signal chain IC7 MIX5 → BPF → IC8 MIX4 participates in PLL2; neither IC7 input need equal indicated HF frequency. Check PLL3/PLL4 lock/control as an option, but establish relevant manual mode/conditions first |

Status: display dots throughout user tests, tuning knob does not produce visible response; mode unconfirmed. No RF coil adjustments or component changes. Spares purchased 2026-10-19 but **none installed**. Next step should discriminate absent/out-of-band MIX5 product vs loss in filter using valid RF measurement, or verify upstream PLL control voltages and reference signals against correct manual conditions.
