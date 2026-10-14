# Diagnostic status — Kenwood TS-440S

Last reviewed: 2026-10-14 (Taiwan local time). **In progress; fault not isolated.**

## Symptoms
- Normal-frequency display may appear briefly after startup or VFO operation; display subsequently becomes dots.
- Semi-Self Test is accessible; Test 0 lights display segments. This makes a wholesale dead display less likely, but does not validate every digital circuit.
- No component has been conclusively identified as faulty. Do not replace PLL ICs or adjust tuned coils on current evidence.

## Highest-confidence measurements
| Area | Observation | Caveat |
|---|---|---|
| PLL Unit TP5 / R70 right side | ~7.86–7.87 V; HP 34401A Min/Max ~7.86 V during tuning/display changes | Meter may miss short transients; exact interpretation of TP5 as control voltage should follow schematic |
| Q16 | B 4.084 mV, E 1.834 mV, C ~7.8 V | Depends on correct B/C/E probing; suggests no forward B-E drive at instant tested, *not* proven bad Q16 |
| IC9 Pin 8 | 4.0 mV DC | Static/average only, does not exclude narrow pulses |
| R67 at IC9 side | ~4.1 mV | Other endpoint not independently characterized in all operating states |
| R68 both ends | ~4.1 and 4.0 mV | Similar DC levels do not prove component good/bad |
| Q20 / R81 RF | around 59.6429 MHz, waveform observed | Non-simultaneous; frequency can change while PLL is unlocked |
| IC10 Pin 8 | 6.03614 MHz RF; ~0.76 V DC | Different capture from R81; pins 4 and 5 ~1.55 V, pin 6 ~4.93 V |
| IC11 MIX3 Pin 2 | 5.96499 MHz | RF is delivered after IC10 and filter chain; amplitude not formally qualified |
| IC11 MIX3 Pin 5 | 35.7827 MHz | Non-simultaneous snapshot |
| C123 T10-side | 42.4576 MHz *automatic frequency reading* | Complex waveform: value does not establish spectral components or missing 30 MHz difference product |

## Semi-Self Test results
- Enter: POWER OFF; hold **4 (AM)** and **T-F SET** while switching power ON; rotate VFO through tests. Exit by POWER OFF (manual pp.25–26).
- Test 0: display elements illuminated.
- Tests 45–53: entered and photographed; most scans NOT functionally verified.
- Test 45 first LOCK column consistently displays **1**. **Correction: this is the front-panel F.LOCK (lock switch) input (8255 IC53 port B0), not PLL's Unlock status.** Must not infer PLL lock/unlock from this digit.
- Test 48: pressing LSB changed its assigned digit from 1 to 0, supporting this key scan pathway.
- True **PLL Unlock** is a separate input at µPD7800 CPU port C2: low when unlocked (manual p.21 Table 11). PLL UL outputs low on unlock (p.17).

## Leading hypotheses (NOT conclusions)
1. At least one PLL loop is unlocked, producing high/saturated-looking TP5 and the display dots.
2. PLL2's control/feedback path should be tested with actual UL line(s), supply and reference checks before suspecting IC9.
3. RF mixer/filter outputs cannot be assigned from a single auto-frequency number on a complex waveform.

## Best next discrimination
1. Confirm ordinary receive mode still shows the dots after exiting self-test.
2. Using manual pp.17,21,72–73,76–77, trace actual **PLL UL → Digital Unit → CPU C2** (do not confuse with 8255 IC53 B0 LOCK switch).
3. With power OFF, identify safe, accessible test nodes for actual UL. Then probe DC logic state while powered, under controlled receive-only conditions. Compare individual PLL unlock indications only where manual schematic supports the routing.
4. If needed, check PLL2 reference to IC9 pin 3 and feedback to pin 16, along with supply / control data, while avoiding conclusions based only on non-synchronous frequency snapshots.

## Safety
Receive-only tests; do not press PTT or perform unintended TX. De-energize to reposition a probe, avoid shorting adjacent IC pins, and avoid detuning T3–T12/T9 or other adjustments until evidence warrants it.

## New UL measurement — 2026-10-14 19:38 local
- User reports **PLL Unit J6 Pin 2 (UL) = 0.52 V DC while front panel shows dots**. Manual p.17 states UL becomes L on unlock. Conditional on verified J6 pin identification, this supports an asserted unlock report; exact electrical logic thresholds and individual loop source not yet isolated.
- Next: compare J6 Pin 2 voltage during brief normal-frequency display if feasible, or check repeatability; no parts condemned.
