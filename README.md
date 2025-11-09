<div align="center">

# 🌊 **Flood Susceptibility Mapping of Uttarkashi**

### *(GIS + Machine Learning)*

[![Open In Colab](https://img.shields.io/badge/Open%20in-Colab-F9AB00?logo=googlecolab\&logoColor=white)](https://colab.research.google.com/drive/YOUR_NOTEBOOK_ID_HERE)
![Python](https://img.shields.io/badge/Python-3.10-3776AB?logo=python\&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML%20Model-F7931E?logo=scikitlearn\&logoColor=white)
![ArcGIS](https://img.shields.io/badge/ArcGIS-GIS%20Processing-1F4F82)
![Made with Love](https://img.shields.io/badge/Made%20with-❤️-ff69b4)

**Authors:** **Dev**, **Naven**, **Arpit**

</div>

---

> [!IMPORTANT]
> After you upload your notebook, **edit this README** and replace the Colab badge link with your actual notebook URL.

## 📚 Table of Contents

* [Overview](#-overview)
* [Highlights](#-highlights)
* [Tech Stack](#-tech-stack)
* [Methodology](#-methodology)
* [How to Run](#-how-to-run)
* [Data Notice](#-data-notice)
* [Results Preview](#-results-preview)
* [Project Structure](#-project-structure)

---

## 📖 Overview

The Himalayan region is highly prone to **flash floods** and **debris flows**. This project builds a high‑resolution **Flood Susceptibility Map (FSM)** for **Uttarkashi, Uttarakhand (India)** using a **Random Forest** model + **GIS** workflows.

> Moving beyond subjective mapping, we use a **data-driven**, **reproducible** pipeline suitable for decision support in **disaster mitigation**, **land‑use planning**, and **emergency response**.

---

## 🔥 Highlights

* **Model:** Random Forest Classifier
* **Accuracy:** <mark>96.32%</mark>
* **ROC AUC:** <mark>0.9804</mark>
* **Top Factor:** <mark>Distance to River (~67%)</mark>

<div align="center">

| Metric          | Value                        |
| --------------- | ---------------------------- |
| Model           | Random Forest                |
| Accuracy        | **96.32%**                   |
| ROC AUC         | **0.9804**                   |
| Dominant Factor | **Distance to River (≈67%)** |

</div>

---

## 🧰 Tech Stack

* **GIS Processing:** ArcGIS (DEM prep, factor derivation, raster calculator)
* **Environment:** Google Colab (Python)
* **Libraries:** `scikit-learn`, `pandas`, `matplotlib`

---

## 🧪 Methodology

### 1) GIS Pre‑processing (ArcGIS)

Using **ALOS PALSAR 12.5m DEM**, we derived 6 conditioning factors:

* Elevation · Slope · Aspect · Curvature · Distance to River (**Euclidean**) · Distance to River (**Near**, for training points)

### 2) Model Training (Python / Colab)

* **Inventory:** 452 points → 226 *Flood* + 226 *Non‑Flood*
* **Dataset:** `data/training/uttarkashi_training_data_6F.csv`
* **Split:** 70/30 train‑test
* **Validation:** AUC = **0.9804**

### 3) Map Generation (ArcGIS)

* Exported RF **feature importances** → applied as weights
* Built district‑wide FSM using **Raster Calculator** (pixel‑by‑pixel)

> [!TIP]
> Keep **large rasters/shapefiles** out of Git (use Drive/Cloud). Only code + CSV live here.

---

## ▶️ How to Run

1. Click the **Open in Colab** badge (top) — replace the badge URL with your notebook link.
2. Upload/ensure `data/training/uttarkashi_training_data_6F.csv` exists.
3. Run all cells to reproduce:

   * Accuracy & AUC
   * Feature importance chart
   * Inference examples

---

## 🗂️ Data Notice

This repo includes **code + training CSV** only. **Raw/processed GIS** layers are excluded due to GitHub’s 100MB limit (~790MB total). Store heavy data in **Google Drive** or other storage.

* Excluded examples: `DEM_FINAL.tif`, `Slope.tif`, `.shp/.dbf/.prj` files, `Curvature.tif`, distance‑to‑river rasters

> [!NOTE]
> This is standard practice for GIS/DS repos. Version control *code*, store *data* externally.

---

## 🖼️ Results Preview

Add a PNG/JPG of your final map here (recommended path below). Replace the link in the image markdown with your filename.

```
results/
└── final_map.png
```

<div align="center">

*Preview placeholder:*

![Final Susceptibility Map](results/final_map.png)

</div>

---

## 🧭 Project Structure

```text
Uttarkashi_Flood_Project/
├─ README.md
├─ notebooks/
│  └─ Uttarkashi_Flood_Model.ipynb           # Colab notebook (optional)
├─ src/                                      # Scripts (optional)
│  ├─ model_training.py
│  ├─ feature_importance.py
│  └─ utils.py
├─ data/
│  ├─ training/
│  │  └─ uttarkashi_training_data_6F.csv
│  └─ gis/                                   # Large files kept OUT of Git
├─ results/
│  └─ final_map.png                          # Export your map here
└─ docs/
   └─ methodology_diagram.png                # Any figures/notes
```

---

<details>
<summary><strong>🔧 Maintainer Notes (optional)</strong></summary>

* Replace the Colab badge link with your notebook URL
* Keep big rasters out of Git; link to Drive instead
* Use branches → PR → review → merge

</details>
