# Service manual index

Reference copy: **Kenwood TS-440S Service Manual**, supplied by the owner on 2026-10-14: `kenwood--ts-440s--service--ID2607.pdf` (116 pages). The PDF is *not* redistributed in this repository. Page numbering below is the PDF/printed manual pagination as seen in this copy.

| Pages | Use |
|---|---|
| 5 | PLL frequency configuration Fig.2 |
| 15–17 | PLL theory, block diagram Fig.12; PLL2 / PLL1 feedback and unlock behavior |
| 17 | PLL loops: UL output low when unlocked, sent to Digital Unit |
| 18–22 | Digital control, port mapping, static inputs, PLL data |
| **21, Table 11** | CPU µPD7800 **C2 Unlock**: L when unlock. 8255 IC53 **B0 Lock switch**: L when physical F.LOCK switch is on. Distinct signals! |
| 25 | Semi-Self Test entry, Test 0–56 |
| 26 | SW Monitor columns and switch inputs (Test45 is **front-panel LOCK switch**, not PLL UL) |
| 27–34 | Semiconductor functional descriptions and pin diagrams |
| 50–55 | Parts listings for PLL Unit X50-2050-00, including IC9 MN6147, IC10 M54460L, IC11 SN16913P, Q16/17 2SC3113(B) |
| **72** | PLL Unit X50-2050-00 component side diagram |
| **73** | PLL Unit full circuit diagram; inspect actual nets when deciding test points |
| **76–77** | Control/Display Unit placement and circuit |
| 89 onward | Adjustment — DO NOT apply until fault isolated |

## Key functional chain for diagnosis
PLL2 Q18 VCO → Q19 MIX4 path → Q15 / IC9 Pin16 PLL feedback; VCO2 also → Q20 → IC10 ÷10 → low-pass filter → IC11 MIX3 Pin2. IC11 Pin5 is other MIX3 input; Pin1 is output via C123/T10–T12. These relationships are from the manual and are *not* evidence every stage is operating correctly.

Note: reference schematics may label expected node voltages for a particular state. A measured difference requires checking exact net, operating mode, supply and original measurement conditions before declaring documentation erroneous.
