# 🧊 AIPC: Tomography Alignment & Spike Analysis

## 📌 Overview

This project focuses on **cryo-electron tomography (cryo-ET)** and **subtomogram averaging** to reconstruct and analyze viral spike structures.

The workflow includes:

* Tilt-series alignment
* Tomogram reconstruction
* Particle picking
* Subtomogram averaging
* Structural refinement

---

## 🎯 Objectives

* Align tilt-series data with high accuracy
* Reduce residual alignment error
* Isolate individual viral spikes
* Perform subtomogram averaging
* Generate a high-quality 3D model

---

## ⚙️ Workflow

### 1. Data Preprocessing (Binning)

* Applied binning (factor 2 → 4) to reduce data size
* Improved Signal-to-Noise Ratio (SNR)
* Trade-off: reduced resolution

---

### 2. Tilt-Series Alignment

* Used patch tracking for alignment

* Optimized parameters:

  * Patch size: 800 × 800
  * Overlap: 0.33
  * Increased iterations

* Target residual error: **0.35 nm**

---

### 3. Tomogram Reconstruction

* Generated 3D tomogram from aligned tilt-series
* Included full specimen thickness (~300 nm)

---

### 4. Particle Picking (Spike Extraction)

* Identified viral spikes manually
* Avoided selecting multiple spikes per particle
* Ensured clean and isolated subtomograms

---

### 5. Subtomogram Averaging

* Applied cylindrical mask:

  * Radius: 20
  * Height: 35
* Applied centering shift (10 units)

---

### 6. Angular Constraints & Symmetry

* Assumed **C3 symmetry (trimer structure)**
* Reduced azimuth rotation range to **120°**
* Used cone aperture: **60°**

---

### 7. Refinement & Visualization

* Iterative refinement of spike structure
* Final model visualized in Chimera

---

## 📊 Key Concepts

### 🔹 Binning

✔ Faster processing
✔ Improved SNR
❌ Reduced resolution

---

### 🔹 Template Matching vs Patch Tracking

* Patch tracking → general alignment
* Template matching → better for spherical features (e.g., gold beads)

---

### 🔹 Subtomogram Challenges

* Irregular spike distribution
* Risk of averaging multiple spikes → blurred results

---

## 📈 Results

✔ Reduced residual alignment error
✔ Improved particle alignment
✔ Clean subtomogram averages
✔ High-quality 3D spike reconstruction

---

## 🛠️ Tools & Technologies

* IMOD (newstack, alignment tools)
* Cryo-ET processing pipeline
* Chimera (3D visualization)

---

## 📂 Project Structure

```bash
report/        → Full report
scripts/       → Workflow notes
parameters/    → Alignment settings
results/       → Summary of results
figures/       → Screenshots & visualizations
```

---

## 📸 Figures (to add)

* Tilt-series alignment (fiducials)
* 3D tomogram
* Particle picking
* Masked averages
* Final Chimera model

---

## ✅ Conclusion

This project demonstrates how careful parameter tuning, masking, and symmetry constraints significantly improve subtomogram averaging and 3D reconstruction quality.

---

## 🚀 Future Work

* Automated particle picking (deep learning)
* Higher resolution refinement
* Advanced alignment methods
