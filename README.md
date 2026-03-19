# 🧊 AIPC: Tomography Alignment & Spike Analysis

**Cryo-electron tomography (cryo-ET) and subtomogram averaging pipeline for reconstructing and analyzing viral spike structures.**

[![Cryo-ET](https://img.shields.io/badge/Method-Cryo--ET-blueviolet)]()
[![IMOD](https://img.shields.io/badge/Tool-IMOD-green)]()
[![Chimera](https://img.shields.io/badge/Viz-Chimera-blue)]()
[![Structural Biology](https://img.shields.io/badge/Field-Structural_Biology-orange)]()

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Objectives](#-objectives)
- [Workflow](#%EF%B8%8F-workflow)
- [Key Concepts](#-key-concepts)
- [Results](#-results)
- [Project Structure](#-project-structure)
- [Tools & Technologies](#%EF%B8%8F-tools--technologies)
- [Figures](#-figures)
- [Conclusion](#-conclusion)
- [Future Work](#-future-work)

---

## 🔬 Overview

This project focuses on **cryo-electron tomography (cryo-ET)** and **subtomogram averaging** to reconstruct and analyze viral spike structures.

The workflow covers the full pipeline from raw tilt-series data to a refined 3D model of viral spikes:
- Tilt-series alignment
- Tomogram reconstruction
- Particle picking
- Subtomogram averaging
- Structural refinement

---

## 🎯 Objectives

- Align tilt-series data with high accuracy
- Reduce residual alignment error
- Isolate individual viral spikes
- Perform subtomogram averaging
- Generate a high-quality 3D model

---

## ⚙️ Workflow

```
Raw Tilt-Series Data
        │
        ▼
┌───────────────────────┐
│ 1. Data Preprocessing │──→ Binning (factor 2 → 4)
│    (Binning)          │    Improved SNR, reduced size
└───────────┬───────────┘
            │
            ▼
┌───────────────────────┐
│ 2. Tilt-Series        │──→ Patch tracking alignment
│    Alignment          │    800×800 patches, 0.33 overlap
│                       │    Target residual: 0.35 nm
└───────────┬───────────┘
            │
            ▼
┌───────────────────────┐
│ 3. Tomogram           │──→ 3D volume from aligned tilt-series
│    Reconstruction     │    Full specimen thickness (~300 nm)
└───────────┬───────────┘
            │
            ▼
┌───────────────────────┐
│ 4. Particle Picking   │──→ Manual spike identification
│    (Spike Extraction) │    Clean, isolated subtomograms
└───────────┬───────────┘
            │
            ▼
┌───────────────────────┐
│ 5. Subtomogram        │──→ Cylindrical mask (r=20, h=35)
│    Averaging          │    Centering shift (10 units)
└───────────┬───────────┘
            │
            ▼
┌───────────────────────┐
│ 6. Angular Constraints│──→ C3 symmetry (trimer)
│    & Symmetry         │    Azimuth: 120°, Cone: 60°
└───────────┬───────────┘
            │
            ▼
┌───────────────────────┐
│ 7. Refinement &       │──→ Iterative refinement
│    Visualization      │    Final model in Chimera
└───────────────────────┘
            │
            ▼
    ✅ 3D Spike Structure
```

---

### 1. Data Preprocessing (Binning)

- Applied binning (factor 2 → 4) to reduce data size
- Improved Signal-to-Noise Ratio (SNR)
- Trade-off: reduced resolution for faster processing

---

### 2. Tilt-Series Alignment

Used **patch tracking** for alignment with optimized parameters:

| Parameter | Value |
|:---|:---|
| **Patch size** | 800 × 800 |
| **Overlap** | 0.33 |
| **Iterations** | Increased for convergence |
| **Target residual error** | 0.35 nm |

---

### 3. Tomogram Reconstruction

- Generated 3D tomogram from aligned tilt-series
- Included full specimen thickness (~300 nm)

---

### 4. Particle Picking (Spike Extraction)

- Identified viral spikes manually
- Avoided selecting multiple spikes per particle
- Ensured clean and isolated subtomograms

---

### 5. Subtomogram Averaging

Applied cylindrical mask for focused averaging:

| Parameter | Value |
|:---|:---|
| **Mask shape** | Cylindrical |
| **Radius** | 20 |
| **Height** | 35 |
| **Centering shift** | 10 units |

---

### 6. Angular Constraints & Symmetry

- Assumed **C3 symmetry** (trimer structure)
- Reduced azimuth rotation range to **120°**
- Used cone aperture: **60°**

---

### 7. Refinement & Visualization

- Iterative refinement of spike structure
- Final model visualized in **UCSF Chimera**

---

## 📊 Key Concepts

### 🔹 Binning

| Advantage | Disadvantage |
|:---|:---|
| ✅ Faster processing | ❌ Reduced resolution |
| ✅ Improved SNR | |
| ✅ Smaller data size | |

---

### 🔹 Template Matching vs Patch Tracking

| Method | Best For |
|:---|:---|
| **Patch tracking** | General alignment of tilt-series |
| **Template matching** | Spherical features (e.g., gold beads) |

---

### 🔹 Subtomogram Challenges

- Irregular spike distribution on viral surface
- Risk of averaging multiple spikes → blurred results
- Requires careful manual picking for clean isolation

---

## 📈 Results

| Metric | Status |
|:---|:---:|
| Reduced residual alignment error | ✅ |
| Improved particle alignment | ✅ |
| Clean subtomogram averages | ✅ |
| High-quality 3D spike reconstruction | ✅ |

Successfully reconstructed two 3D models (`3d_0-1`, `3d_0-2`) with improved alignment consistency from additional views.

---

## 📂 Project Structure

```
aipc-tomography/
│
├── report/                 # Full project report
│   └── cryo_et_report.pdf
│
├── scripts/                # Workflow notes and commands
│   └── pipeline_notes.txt
│
├── parameters/             # Alignment and averaging settings
│   └── alignment_params.txt
│
├── results/                # Summary of results
│   └── results_summary.txt
│
├── figures/                # Screenshots and visualizations
│   ├── tilt_series/        # Tilt-series alignment (fiducials)
│   ├── tomogram/           # 3D tomogram slices
│   ├── picking/            # Particle picking screenshots
│   ├── averages/           # Masked subtomogram averages
│   └── chimera/            # Final Chimera model renders
│
└── README.md               # Project documentation
```

---

## 🛠️ Tools & Technologies

| Category | Tools |
|:---|:---|
| **Alignment & Reconstruction** | IMOD (newstack, alignment tools) |
| **Processing Pipeline** | Cryo-ET processing tools |
| **Visualization** | UCSF Chimera |

---

## 📸 Figures

> - Tilt-series alignment (fiducials)
> - 3D tomogram slices
> - Particle picking visualization
> - Masked subtomogram averages
> - Final Chimera model

---

## ✅ Conclusion

This project demonstrates how **careful parameter tuning**, **masking**, and **symmetry constraints** significantly improve subtomogram averaging and 3D reconstruction quality in cryo-ET.

---

## 🔮 Future Work

- Automated particle picking using **deep learning**
- Higher resolution refinement
- Advanced alignment methods
- Integration with **RELION** / **Dynamo** / **EMAN2**
