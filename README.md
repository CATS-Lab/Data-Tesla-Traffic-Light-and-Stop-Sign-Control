# Data-Tesla-Traffic-Light-and-Stop-Sign-Control

## Overview

This repository hosts the **Tesla Traffic Light and Stop Sign Control – Vehicle (TLSSC-V) Dataset**, introduced in the TRB 2026 Annual Meeting paper:

> **Li, Z., Zhang, P., Liang, S., Zhou, H., Ma, C., Li, Q., Yao, H., & Li, X.**  
> _Benchmarking Tesla’s Traffic Light and Stop Sign Control: Field Dataset and Behavior Insights_  
> TRBAM-26-05481, 2025.

The dataset provides **high-resolution, synchronized vehicle trajectory and driver-perspective video data** of Tesla’s Traffic Light and Stop Sign Control (TLSSC) feature interacting with **Traffic Control Devices (TCDs)**, including both **traffic lights** and **stop signs**.

It is the **first publicly available dataset** focusing on **ADAS–TCD interactions**, supporting research in traffic operations, driving behavior modeling, safety evaluation, and simulation.

---

## Key Features

- **Vehicle platform:** Tesla Model Y with TLSSC enabled.
- **Data type:** GPS-based vehicle trajectories (10 Hz) and driver-perspective videos.
- **Geographical coverage:** Madison, Middleton, Fitchburg, and Verona, Wisconsin (USA).
- **Behavior taxonomy:**
  1. **Stopping behaviors:**
     - Stop before a red/yellow light
     - Stop before a green light (permission required)
     - Stop before a stop sign
  2. **Accelerating behaviors:**
     - Accelerate after permission at a green light (before/after stop)
     - Accelerate after permission at a stop sign
  3. **Car-following behaviors:**
     - Standard car-following (gap levels 2, 4, 7)
     - Car-following through intersections (gap levels 2, 4, 7)
- **Novel finding:** Empirical car-following detection threshold ≈ **90 m** for TLSSC-V.

---

## Data Structure

Trajectory data are stored in CSV files with the following key variables:

| Column Name                               | Description                                             |
| ----------------------------------------- | ------------------------------------------------------- |
| `Time`                                    | Timestamp in ISO 8601 format                            |
| `Longitude`, `Latitude`                   | Raw GPS coordinates of TLSSC-V                          |
| `Longitude_smoothed`, `Latitude_smoothed` | Smoothed GPS coordinates                                |
| `Speed`, `Speed_smoothed`                 | Raw & smoothed vehicle speed (m/s)                      |
| `Longitude_lead`, `Latitude_lead`         | Raw GPS coordinates of lead vehicle (if present)        |
| `Speed_lead`, `Speed_lead_smoothed`       | Lead vehicle speed (m/s)                                |
| Additional fields                         | Elevation, heading, accuracy metrics (PDOP, HDOP, VDOP) |

---

## Data Quality

- **Sampling rate:** 10 Hz
- **Smoothing:** Moving average (1-second window)
- **Quality metrics:**
  - Anomaly Acceleration (%)
  - Anomaly Jerk (%)
- **Post-processing:** Reduced acceleration & jerk anomalies to near zero.

---

## Example Use Cases

- Calibrating car-following models (e.g., Full Velocity Difference Model – FVDM)
- Investigating ADAS behavior at intersections
- Evaluating safety and comfort of ADAS–TCD interactions
- Integrating empirical ADAS behavior into microscopic traffic simulations

---
