# 🧠 Tumor Segmentation in MRI Brain Scans

This project performs image segmentation on MRI brain image to identify and segment tumor regions using binary masking and labeling techniques in Python.

---

## 📌 Table of Contents
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Objective](#objective)
- [Methodology](#methodology)
- [Results](#results)
- [How to Run](#how-to-run)
- [Visualizations](#visualizations)
- [Challenges](#challenges)
- [Improvements](#improvements)
- [Contributors](#contributors)
- [License](#license)

---

## 📖 Project Overview

In this project, I used binary masking technique to segment tumors in MRI brain scan slices. The segmented images highlight tumor boundaries, and distinguish multi-region tumors using intensity differences and region labeling.

This can assist medical practitioners or serve as a proof-of-concept for more advanced models.

---

## Dataset

- **Type**: MRI scan brain images
- **Format**: `.nii` (Neuroimaging Informatics Technology Initiative format)
- **Slices**: 2D grayscale slices from 3D volumes  
  📥 [Download Link](https://drive.google.com/file/d/17GweAk4-2pUUwOFV9EQZgLv70_jD0OVR/view?usp=sharing)  

- Full Data Source
- 📥 [Download Link](https://www.cancerimagingarchive.net/collection/brats-africa/)

---

## Objective

- Detect and visualize tumor regions in brain CT images.
- Label nested and overlapping tumors with separate colors.
- Improve visibility by applying masks and filtering borders.
- Enable easy inspection and interpretation of segmented regions.

---

##  Methodology

1. **Data**
   - Loaded `.nii` image using `nibabel`  
2. **Segmentation via binary masking**
   - Tumor regions identified by pixel intensities (image > 8000) & (image <= 10500) pixel values
   - Separated high and low intensity tumors using color-mesh
3. **Masking**
   - Binary masks created using NumPy
4. **Border Clearing**
   - `skimage.segmentation.clear_border()` used to remove artifacts
5. **Labeling**
   - `skimage.measure.regionprops() to identify tumor regions and their properties such as area, bounding boxes, center_of_mass  
   - `scipy.measure.label()` to label connected regions and identified region areas
6. **Visualization**
   - `matplotlib.pyplot.pcolormesh()` for color visualization
   - `scipy.ndimage.zoom() to reduce axes dimensions  
   - `plotly.graph_objects() for 3D visualisation of segmented tumors

---

## Results

Example segmented slice (slice index = 110):

| Original | Segmented |
|----------|-----------|
| ![Original](https://github.com/Amos77Robert/segmentation-of-brain-tumors-without-AI/blob/main/visualisations/original_mri_scan.png?raw=true) | ![Segmented](https://github.com/Amos77Robert/segmentation-of-brain-tumors-without-AI/blob/main/visualisations/segmented.png?raw=true) |

Nested tumors:
- Small tumor : Higher intensity
- Larger tumor: Moderately Lower intensity, re-labeled as a distinct region

---

## ▶ How to Run

```bash
git clone https://github.com/Amos77Robert/segmentation-of-brain-tumors-without-AI.git
cd segmentation-of-brain-tumors-without-A

# Setup environment
pip install -r requirements.txt

# Run the notebook in VS Code, Colab, Jupyter or any Python environment
python iMAGE sEGMENTATION sCRIPT.ipynb
