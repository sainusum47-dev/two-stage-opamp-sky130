# AES-128 Low-Power Multi-Voltage Design

![Status](https://img.shields.io/badge/status-completed-brightgreen)
![Tool](https://img.shields.io/badge/tool-OpenLane-blue)
![PDK](https://img.shields.io/badge/PDK-Sky130-orange)
![Language](https://img.shields.io/badge/HDL-Verilog-red)

## Overview

This project implements an AES-128 encryption core and explores
low-power multi-voltage design concepts using the OpenLane RTL-to-GDSII
ASIC flow and the Sky130 standard-cell library.

## Design Flow

## Objectives

- Implement AES-128 encryption in Verilog HDL
- Synthesize and physically implement the design using OpenLane
- Define multi-voltage power intent using UPF
- Analyze power, timing, area and physical-design results
- Generate final GDSII layout
- Verify the final layout using DRC and LVS

## Architecture

Two intended power domains:
- `PD_ALWAYS_ON`
- `PD_AES_CORE`

The UPF file defines separate supply intent for the always-on and AES-core domains.

## Final Results

| Parameter | Result |
|---|---:|
| Flow status | Completed |
| Total power | 70.9 mW |
| Worst setup slack | 3.46 ns |
| Worst hold slack | 0.28 ns |
| Setup violations | 0 |
| Hold violations | 0 |
| DRC violations | 0 |
| LVS errors | 0 |
| Max fanout violations | 28 |
| Final GDS | Generated |

## Final Layout 
<img width="702" height="540" alt="dc_sweep_output_swing" src="https://github.com/user-attachments/assets/f6a93776-e584-4085-86cb-f8534a7a73c0" />

<img width="697" height="530" alt="final_gain_bode_plot" src="https://github.com/user-attachments/assets/4f03069b-449f-4d7f-8ad7-7588b620437f" />
<img width="690" height="400" alt="final_phase_margin_plot" src="https://github.com/user-attachments/assets/b0b68173-a3cd-48d4-a078-293d18ed332f" />
<img width="697" height="545" alt="transient_slewrate_response" src="https://github.com/user-attachments/assets/34f7e1f1-dd80-47f1-8765-b809ecd32f38" />

## Repository Structure


## Tools Used

- Verilog HDL
- OpenLane
- Sky130
- OpenROAD
- KLayout
- UPF
- WSL2 / Ubuntu

## Important Note

The UPF file documents the intended multi-voltage architecture. The
current OpenLane v1 Sky130 flow does not physically implement separate
voltage-domain cells, level shifters, or independently powered physical
domains. This project demonstrates the multi-voltage power-intent
concept together with a complete ASIC physical-design flow, rather than
claiming a physically implemented multi-voltage silicon layout.

## Author

Sai Lakshmi
