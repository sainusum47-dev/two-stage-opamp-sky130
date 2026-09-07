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

## Final Layout (KLayout)

![KLayout Final Layout](klayout_view.png)

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
