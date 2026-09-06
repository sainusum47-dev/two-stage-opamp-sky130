# Two-Stage Miller-Compensated CMOS Op-Amp

A two-stage CMOS operational amplifier designed and verified in **ngspice** using the open-source **SkyWater Sky130 PDK**, targeting high DC gain with Miller compensation for stability.

## Objective

Design a two-stage op-amp with:
- Target DC Gain: 70 dB
- Phase Margin: > 60°
- Miller compensation for frequency stability

## Final Results

| Spec | Target | Achieved |
|---|---|---|
| DC Gain | 70 dB | 64.75 dB |
| Phase Margin | > 60° | 62.7° |
| Output Swing | — | ~0V to 1.8V (rail-to-rail) |
| Slew Rate | — | ~0.063 V/µs |

## Architecture

- **Stage 1**: NMOS differential pair (M1, M2) with PMOS current mirror load (M3, M4) and NMOS tail current source (M5)
- **Stage 2**: NMOS common-source amplifier (M6) with PMOS current source load (M7)
- **Compensation**: Miller capacitor (Cc = 4pF) with nulling resistor (Rz = 5kΩ) between Stage 1 and Stage 2 outputs

## Final Transistor Sizing

| Device | Role | L (µm) | W (µm) |
|---|---|---|---|
| M1, M2 | NMOS input pair | 0.2 | 2 |
| M3, M4 | PMOS mirror load | 0.2 | 5 |
| M5 | NMOS tail source | 0.5 | 4 |
| M6 | NMOS (Stage 2) | 2.0 | 6 |
| M7 | PMOS (Stage 2 load) | 2.0 | 12 |

**Bias voltages**: VBIAS ≈ 0.89V (tail), VBIAS2 ≈ 0.401V (Stage 2 load)
**Compensation**: Cc = 4pF, Rz = 5kΩ, CL = 2pF (load)

## Tools Used

- [ngspice](http://ngspice.sourceforge.net/) 45.2 — open-source SPICE simulator
- [SkyWater Sky130 PDK](https://github.com/google/skywater-pdk-libs-sky130_fd_pr) — open-source 130nm process design kit
- WSL2 (Ubuntu) on Windows

## Setup

```bash
sudo apt install ngspice
git clone https://github.com/google/skywater-pdk-libs-sky130_fd_pr.git models/sky130_fd_pr
```

**Known PDK bug fix**: The raw repo has a missing comment marker in `cells/nfet_05v0_nvt/sky130_fd_pr__nfet_05v0_nvt.pm3.spice` (line 16), which breaks ngspice parsing. Fix with:

```bash
sed -i '16s/^include/* include/' models/sky130_fd_pr/cells/nfet_05v0_nvt/sky130_fd_pr__nfet_05v0_nvt.pm3.spice
```

## Running the Simulations

```bash
cd netlists
ngspice twostage_compensated3.cir   # Final AC gain + phase margin
ngspice transient_smallsig.cir      # Slew rate / transient response
ngspice dc_sweep_swing.cir          # Output voltage swing
```
<img width="702" height="540" alt="dc_sweep_output_swing" src="https://github.com/user-attachments/assets/52e650c0-09cf-4b9a-85fe-51d026bfce6a" />

## Repository Structure
