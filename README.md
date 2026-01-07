# PatriotState_DashCalc

**Wire-to-Water Pump Efficiency Calculator**  
*Patriot State SWD #1 | Blackbuck Resources | Edge Controls*

---

## Overview

This interactive calculator allows operations personnel to calculate true **wire-to-water efficiency** for injection pump systems. It uses actual VFD electrical measurements (voltage, current) and field instrumentation (flow, pressure) to determine real system efficiency—not theoretical pump curve estimates.

**Live Calculator:** [https://1137fsc.github.io/PatriotState_DashCalc/](https://1137fsc.github.io/PatriotState_DashCalc/)

---

## Features

- **Real-Time Efficiency Calculation** — Input actual VFD voltage, current, and power factor
- **Wire-to-Water Metrics** — Captures VFD, motor, AND pump losses in one number
- **Cost Analysis** — Estimate operating costs based on your $/kWh rate
- **BEP Comparison** — Compare current operation vs. running at Best Efficiency Point
- **Affinity Law Visualization** — See how the cubic power relationship affects your savings

---

## Key Formulas

### Electrical Power Input
```
P_in (kW) = √3 × V × I × PF / 1000
```
- V = Line-to-line voltage (V)
- I = Motor current (A)
- PF = Power factor (typically 0.85)

### Hydraulic Power Output
```
HP_hydraulic = (GPM × Head_ft × SG) / 3960
```
- GPM = Flow rate (BPD ÷ 34.286)
- Head_ft = Differential pressure in feet (PSI × 2.31 / SG)
- SG = Specific gravity

### Wire-to-Water Efficiency
```
η_W2W = (HP_hydraulic / HP_electrical) × 100%
```

### Affinity Laws (Power)
```
P2 = P1 × (N2/N1)³
```
Power scales with speed **cubed** — reducing speed by 20% cuts power by ~50%.

---

## Equipment Reference

| Equipment | Model | Specifications |
|-----------|-------|----------------|
| Injection Pumps | CAI CJL12000 67-Stage | 12,000 BPD @ 2,652.6 PSI (BEP) |
| Motors | Hyundai 800 HP | 95.8% efficiency @ full load |
| VFDs | VACON NXP | 96% efficiency typical |
| PLC | Allen-Bradley CompactLogix 5380 | 5069-L320 |

---

## Operating Point Optimization

This facility was optimized to operate **right of BEP** to minimize total power consumption:

| Parameter | Original (BEP) | Optimized |
|-----------|----------------|-----------|
| Discharge Nominal | 2,652.6 PSI | 2,200.0 PSI |
| Flow Nominal | 12,000 BPD | 15,000 BPD |
| Pump Efficiency | 77.1% | ~65% |
| **Power Consumption** | Higher | **Lower** |

**Why?** The well formation has low back-pressure. Operating at BEP required excessive valve throttling. By shifting right, pumps run at lower speed, and the cubic power relationship (affinity laws) results in significant power savings despite reduced pump efficiency.

---

## Usage

1. Enter your **pump curve parameters** (discharge nominal, flow nominal, BEP efficiency)
2. Enter **operating data** from field instruments (frequency, flow, pressures)
3. Enter **electrical measurements** from VFD (voltage, current, power factor)
4. View calculated **wire-to-water efficiency** and cost analysis
5. Compare against BEP operation to quantify savings

---

## Files

| File | Description |
|------|-------------|
| `index.html` | Main calculator application (single-file, no dependencies) |
| `README.md` | This documentation |

---

## Deployment

This calculator is deployed via GitHub Pages. To deploy your own:

1. Fork this repository
2. Go to **Settings** → **Pages**
3. Under "Source", select **Deploy from a branch**
4. Select **main** branch and **/ (root)** folder
5. Click **Save**
6. Access at `https://<username>.github.io/PatriotState_DashCalc/`

---

## Technical Notes

- All calculations match the `AOI_PumpEfficiency` v2.0 implemented in the facility PLC
- Calculator runs entirely client-side (no server required)
- Works offline once loaded
- Mobile-responsive design

---

## Contact

**Edge Controls, LLC**  
PO Box 9939  
Midland, TX 79708

---

*Patriot State SWD #1 — Commissioned January 2026*
