# Fair Multimodal Deep Learning System for Skin Cancer Detection

## 📌 Project Overview
This research project addresses the critical issue of algorithmic bias in automated skin cancer diagnosis. Standard datasets (like HAM10000) predominantly feature fair-skinned patients. This project develops a **Fair Multimodal Diagnostic System (FMDS)** that integrates dermoscopic images with patient metadata (age, sex, localization) and utilizes diverse data sources (Fitzpatrick17k) to improve inclusivity and accuracy.

## 🎯 Research Objectives
1.  **Multimodality:** To implement a Fusion Architecture combining CNN (EfficientNetV2) for image processing and MLP for clinical metadata.
2.  **Fairness by Design:** To apply a Data-Centric AI approach by integrating underrepresented skin tones to mitigate racial bias.
3.  **Explainability (XAI):** To implement Grad-CAM visualization, ensuring the model's decisions are clinically relevant and interpretable.

## 📅 Project Timeline & Milestones
| Phase | Milestone | Status | Completion Date |
| :--- | :--- | :--- | :--- |
| 1 | Literature Review & Problem Definition | ✅ Completed | Oct 15, 2025 |
| 2 | Social Relevance Survey ($N=11$) | ✅ Completed | Oct 20, 2025 |
| 3 | Data Collection & Preprocessing | ✅ Completed | Nov 05, 2025 |
| 4 | **Iteration 1:** Baseline Unimodal Model | ❌ Failed (Low Accuracy) | Nov 10, 2025 |
| 5 | **Iteration 2:** Multimodal Fusion Dev | ⚠️ Integration Challenges | Nov 14, 2025 |
| 6 | **Final:** Transfer Learning (ImageNet) + Grad-CAM | ✅ Success (~62% Acc) | Nov 18, 2025 |

## 🛠 Methodology & Justification
### 1. Architecture Selection
We selected a **Late Fusion** architecture.
* *Justification:* Unimodal (image-only) models fail to capture the clinical context used by dermatologists. Combining structured data (age/sex) mimics real-world diagnostic procedures.

### 2. Transfer Learning Strategy
We utilized **EfficientNetV2B0** pre-trained on ImageNet.
* *Justification:* Initial training from scratch yielded poor results (~20% accuracy). Transfer learning provided the necessary feature extraction capabilities for our limited dataset size.

### 3. Data-Centric Fairness
We merged HAM10000 with Fitzpatrick17k.
* *Justification:* To actively counter the "fair skin bias" inherent in standard medical datasets.

## 📂 Repository Structure
This repository documents the entire research process:
* `/docs` - Research proposal, survey instruments, and draft reports.
* `/notebooks` - Code evolution. Contains both the final successful model and previous experimental iterations.
* `/data` - Processed metadata CSV files used for training.
* `/results` - Visual evidence of model performance (Accuracy graphs, Grad-CAM heatmaps).

## 🚀 How to Reproduce Results
1.  Open `notebooks/final_multimodal_fusion.ipynb` in Google Colab.
2.  Upload the CSV files from the `/data` folder to your Colab session.
3.  Run the cells sequentially. The script automatically handles image downloading and processing.
4.  Execute the final cell to generate the XAI (Grad-CAM) visualization.

---
**Author:** Nurbol Agybetov, Yermek Khaknazar, Baglan Yessenkeldi, Tokhtar Nuralin, Alisher Mukanov 

**Course:** Research Methods and Tools

**Institution:** Astana IT University

**Date:** 18 November 2025
