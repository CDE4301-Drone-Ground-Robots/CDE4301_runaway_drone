<div align="center">

<!-- NUS LOGO DISPLAY -->
<img src="https://nus.edu.sg/images/default-source/identity-images/NUS_logo_full-horizontal.jpg" alt="NUS Logo" width="600" />

#  Drone-Vision Foreign Object Debris (FOD) Detection on Airport Runways

### Draft Report for CDE4301

_In Collaboration with the Republic of Singapore Air Force (RSAF) and Robotics & Autonomous Systems Innovation and Development (RAiD)_  
_Innovation & Design Programme | College of Design and Engineering | National University of Singapore_

</div>

---

### Project Details

_Table 0.1: Project Team and Faculty Supervision Details_
| Project Team (UGV Focus) | Student ID | Faculty | Supervision |
| :--- | :--- | :--- | :--- |
| **Charansagar Ramanujam** | `A0301658E` | Robotics Specilisation |**Dr Tang Kok Zuea**|
| **Arun** | `--------` | College of Design and Engineering |**Dr Tang Kok Zuea** |
| **Talitha** | `------------` | College of Design and Engineering |**Dr Tang Kok Zuea** |



## 1. Overview

Foreign Object Debris (FOD) — anything from loose bolts and tools to wildlife and tyre debris — left on an active runway is a serious aviation safety hazard, with consequences ranging from engine/airframe damage to catastrophic accidents. Airports today rely on a mix of manual visual inspection, fixed radar installations (e.g. mmW radar, SAR), and static optical sensor networks. These are effective but come with real trade-offs: manual inspection doesn't scale, and fixed sensor infrastructure is expensive to install and maintain across an entire runway.

This project investigates **drone (UAV)-based visual FOD detection** as a lower-cost, more flexible alternative to fixed infrastructure, and asks a practical question for stakeholders: **is this feasible, and what would it cost to actually deploy?**

## 2. Current Project Scope

This FYP is **not** building a deployment-ready FOD detection system. The current phase is a **feasibility study**, and the primary deliverable is a **budget allocation prediction** for stakeholders, derived from:

- A **scaled-down physical prototype** (drone + onboard/companion vision pipeline), and
- **Simulation under scaled-down conditions** (reduced runway area, controlled test objects, controlled flight parameters).

Findings from this scaled-down testing will later be **extrapolated to full-scale runway conditions** in a subsequent phase. Nothing in this repo at this stage should be read as a production-ready or airport-certified system.

**In scope right now:**
- Literature review of existing FOD detection approaches (traditional, radar, AI/vision, sensor fusion)
- Small-scale prototype build and flight testing
- Detection accuracy testing on a scaled-down "runway" with representative FOD items
- Cost modeling of the prototype, and a scaling model to project full-scale budget
- Feasibility report + budget allocation prediction for stakeholders

**Out of scope right now:**
- Full-scale runway trials
- Regulatory/certification pathway
- Production-grade reliability, redundancy, or weatherproofing
- Final hardware/vendor selection

## 3. Why Drone-Vision? (Background Research)

Our approach is grounded in current literature on FOD detection technology:

| Sensor type | Resolution | Weather resilience | Relative cost | Detection range |
|---|---|---|---|---|
| Optical camera | High (short range) | Poor | Low | Short |
| LiDAR | High | Moderate | High | Medium |
| mmW radar | Depends on bandwidth/antenna | High | Moderate | Long |
| SAR | Depends on bandwidth | High | Moderate | Long |

*(Adapted from the sensor comparison in Shan et al., "A Review of Foreign Object Debris Detection on Airport Runways: Sensors and Algorithms," Remote Sensing, 2025.)*

Key takeaways that motivate this project's direction:

- Commercial fixed sensor-fusion systems (e.g. Tarsier, FODetect) combine radar with optical sensors, but require permanent, expensive infrastructure — a barrier for smaller or lower-budget airports.
- Static camera/radar networks are costly and complex to install and maintain across a full runway.
- The literature explicitly identifies **drone-based systems equipped with optical, thermal, or radar sensors** as a flexible, scalable alternative that reduces reliance on fixed infrastructure — while also noting that such systems are still early-stage and currently face real-time detection and safety-certification constraints. This is precisely the gap our feasibility study is probing.
- On the AI side, YOLO-family detectors (and derivatives tuned for small-object detection) have shown strong results for FOD-type objects, which informs the vision model choice for our prototype.

A second, complementary reference — Krestenitis et al., "Digitalization and Automation of Runway Inspection Using Unmanned Aerial Vehicles" (Sensors, 2026) — demonstrates an end-to-end **UAV-based runway inspection pipeline** (data capture → deep-learning segmentation → GIS-based condition mapping), validated on a real runway. While their focus is pavement *defect* inspection rather than FOD detection, it's a useful methodological blueprint and a real-world benchmark for our own flight/imaging parameters:

| Parameter | Reference value (from literature) |
|---|---|
| UAV platform | DJI Matrice 300 RTK w/ Zenmuse P1 camera |
| Camera | Full-frame RGB, 4000 × 3000 px, 63.5° FOV |
| Flight altitude (tested) | 20 m and 32 m |
| Image overlap | 70% front / 70% side |
| Ground sampling distance (GSD) | ≈ 4.3 mm/pixel at reference altitude |

We use these as **rough benchmarks**, not as a spec to replicate — our scaled-down prototype will use more modest, budget-appropriate hardware, and we'll document the actual specs we test with as we go.

## 4. Planned Methodology

1. **Literature review** — consolidate sensor trade-offs, detection algorithm options, and prior cost/feasibility discussions (in progress; see `/docs`).
2. **Scaled-down prototype build** — a consumer/prosumer drone with an RGB camera, running a lightweight on-device or ground-station object detection model.
3. **Simulated test environment** — a scaled-down mock runway area with planted test objects standing in for FOD (metal, plastic, rubber, etc.), under varied lighting/altitude conditions.
4. **Data collection & evaluation** — detection accuracy, false alarm rate, coverage speed, and flight endurance at small scale.
5. **Cost modeling** — itemized cost of the prototype (hardware, compute, flight time, personnel), then a scaling model to project costs for full-length runway coverage.
6. **Feasibility & budget report** — deliverable summarizing whether the approach is viable and what budget stakeholders should plan for, with assumptions clearly flagged for the later scale-up phase.

## 5. Deliverables (this phase)

- [ ] Feasibility report
- [ ] Budget allocation prediction (prototype-derived, scaled-up projection)
- [ ] Prototype test log & simulation results
- [ ] Literature review write-up

## 6. Repository Structure

> Placeholder — update once the repo layout is finalized.

```
├── docs/            # literature review, feasibility report, budget report
├── hardware/         # prototype BOM, drone/camera specs, wiring notes
├── software/         # detection pipeline, model training/inference code
├── simulation/        # scaled-down test setup, test object configs, results
├── data/            # test flight imagery/logs (raw + annotated)
└── README.md
```

## 7. References

- Shan, J.; Miccinesi, L.; Beni, A.; Pagnini, L.; Cioncolini, A.; Pieraccini, M. *A Review of Foreign Object Debris Detection on Airport Runways: Sensors and Algorithms.* Remote Sensing 2025, 17, 225.
- Krestenitis, M.; Petropoulos, A.; Koulalis, I.; Stipanovic, I.; Skaric Palic, S.; Ioannidis, K.; Vrochidis, S. *Digitalization and Automation of Runway Inspection Using Unmanned Aerial Vehicles.* Sensors 2026, 26, 1100.

## 8. Team & Contact

> Placeholder — add team member names, roles, supervisor, and contact details.

---
*This README covers only the current feasibility/budget-prediction phase of the project. It will be revised as the prototype and simulation results come in, and again once the project moves to full-scale evaluation.*
