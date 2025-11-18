# Fair Multimodal Deep Learning System for Skin Cancer Detection

##  Project Overview
This research project addresses the critical issue of algorithmic bias in automated skin cancer diagnosis. Standard datasets (like HAM10000) predominantly feature fair-skinned patients. This project develops a **Fair Multimodal Diagnostic System (FMDS)** that integrates dermoscopic images with patient metadata (age, sex, localization) and utilizes diverse data sources (Fitzpatrick17k) to improve inclusivity and accuracy.

## Research Objectives
1.  **Multimodality:** To implement a Fusion Architecture combining CNN (EfficientNetV2) for image processing and MLP for clinical metadata.
2.  **Fairness by Design:** To apply a Data-Centric AI approach by integrating underrepresented skin tones to mitigate racial bias.
3.  **Explainability (XAI):** To implement Grad-CAM visualization, ensuring the model's decisions are clinically relevant and interpretable.

## Project Timeline & Milestones
| Phase | Milestone | Status | Completion Date |
| :--- | :--- | :--- | :--- |
| 1 | Literature Review & Problem Definition | Completed | Oct 15, 2025 |
| 2 | Social Relevance Survey ($N=11$) | Completed | Oct 20, 2025 |
| 3 | Data Collection & Preprocessing | Completed | Nov 05, 2025 |
| 4 | **Iteration 1:** Baseline Unimodal Model | Failed (Low Accuracy) | Nov 10, 2025 |
| 5 | **Iteration 2:** Multimodal Fusion Dev | Integration Challenges | Nov 14, 2025 |
| 6 | **Final:** Transfer Learning (ImageNet) + Grad-CAM | Success (~62% Acc) | Nov 18, 2025 |

## Methodology & Justification
### 1. Architecture Selection
We selected a **Late Fusion** architecture.
* *Justification:* Unimodal (image-only) models fail to capture the clinical context used by dermatologists. Combining structured data (age/sex) mimics real-world diagnostic procedures.

### 2. Transfer Learning Strategy
We utilized **EfficientNetV2B0** pre-trained on ImageNet.
* *Justification:* Initial training from scratch yielded poor results (~20% accuracy). Transfer learning provided the necessary feature extraction capabilities for our limited dataset size.

### 3. Data-Centric Fairness
We merged HAM10000 with Fitzpatrick17k.
* *Justification:* To actively counter the "fair skin bias" inherent in standard medical datasets.

## Repository Structure
This repository documents the entire research process:
* `/docs` - Research proposal, survey instruments, and draft reports.
* `/notebooks` - Code evolution. Contains both the final successful model and previous experimental iterations.
* `/data` - Processed metadata CSV files used for training.
* `/results` - Visual evidence of model performance (Accuracy graphs, Grad-CAM heatmaps).

## How to Reproduce Results
1.  Open `notebooks/final_multimodal_fusion.ipynb` in Google Colab.
2.  Upload the CSV files from the `/data` folder to your Colab session.
3.  Run the cells sequentially. The script automatically handles image downloading and processing.
4.  Execute the final cell to generate the XAI (Grad-CAM) visualization.

##  Experiments & Code Evolution
This repository contains the full history of our code development, demonstrating the iterative research process:
### `/docs`

* **`01_Research_Question_and_Concept_Map.pdf` (Problem Definition)**
    * *Focus:* Established the foundational scope using the "5Ws" technique and defined the preliminary research question.
    * *Key Features:*
        * **Mind Map** visualizing the ecosystem of Deep Learning in dermatology.
        * Identification of key stakeholders (Patients, Clinicians) and impact areas.
    * *Outcome:* Confirmed the necessity of a "Fair Multimodal Diagnostic System" (FMDS).

* **`02_Research_Aims_Objectives_and_Gaps.pdf` (Strategic Goals)**
    * *Focus:* Formulated the specific Research Aim and detailed Objectives for the project.
    * *Key Features:*
        * Identification of 3 critical **Research Gaps**: Data Fairness, Limited Metadata, and Explainability.
        * Objective to create a "Fairness by Design" protocol.
    * *Outcome:* Defined the roadmap for a paradigm shift from "Black Box" AI to trustworthy systems.

* **`03_Thematic_Literature_Review_and_Matrix.pdf` (Literature Analysis)**
    * *Focus:* Conducted a thematic analysis of 20 academic sources (2016-2025).
    * *Key Features:*
        * Analysis of architectural evolution from Transfer Learning to **Ensemble Methods**.
        * Evaluation of Data Strategies (Preprocessing, Class Imbalance, Taxonomy).
    * *Conclusion:* Existing models excel at accuracy but fail at fairness and clinical integration.

* **`04_Methodology_Architecture_and_Fairness_Protocol.docx` (System Design)**
    * *Solution:* Proposed a novel **2-Branch Hybrid Architecture**:
        * **EfficientNetV2** for dermoscopic images.
        * **MLP** for structured metadata (including Fitzpatrick skin type).
    * *Key Features:* Implemented a **"Fairness by Design" Protocol** using algorithmic skin tone stratification and fairness-aware loss functions.
    * *Outcome:* A rigorous experimental design for ablation studies.

* **`05_Midterm_Report.pdf` (Consolidated Report)**
    * *Focus:* Synthesized the introduction, literature review, and methodology into a formal report.
    * *Key Features:*
        * Detailed **Problem Statement** regarding systemic algorithmic bias.
        * **Research Schedule** spanning 5 phases from preparation to dissemination.
    * *Outcome:* Validated the project feasibility and theoretical contribution.

* **`06_Questionnaire_Results_and_Model_Training_Logs.pdf` (Implementation & Results)**
    * *Focus:* Presented empirical evidence from public surveys ($N=11$) and data preparation steps.
    * *Key Features:*
        * **Survey Data:** 90.9% of respondents rated AI explainability as critical, justifying the XAI module.
        * **Dataset Preparation:** Prepared the dataset for training and organized images by diagnosis labels using Google Colab scripts.
    * *Outcome:* Successfully structured and stratified the data for the deep learning pipeline.
    
###  `/notebooks`
* **`v1_baseline_unimodal.ipynb` (Initial Draft)**
    * *Approach:* Attempted to train a simple model on images only.
    * *Result:* Low accuracy (~20%). The model failed to generalize due to the small dataset size and lack of clinical metadata.
    
* **`v2_experiment_custom_transfer.ipynb` (Second Draft)**
    * *Hypothesis:* Tried to improve performance by transferring weights from a previously trained custom model ("Brain Transplant" method).
    * *Challenges:* Encountered technical issues with input shape compatibility (300x300 vs 224x224) and weight freezing.
    * *Conclusion:* This approach was deemed unstable for the final production environment.

* **`v3_final_solution_multimodal.ipynb` (Final Version)**
    * *Solution:* Implemented a clean **Fusion Architecture** using **EfficientNetV2B0 (ImageNet weights)**.
    * *Key Features:* * Correct data preprocessing (handling missing metadata).
        * Data-Centric fairness adjustments.
        * **Grad-CAM** implementation for XAI.
    * *Outcome:* Successful training with ~62% accuracy and clear interpretability.


### `/results`
This folder contains the evidence of the model's performance and our error analysis:

* **`gradcam_visualization.png`**: The XAI heatmap demonstrating that the model correctly focuses on the lesion area, validating clinical relevance.
* **`/success`**: A collection of correctly classified cases, showcasing the model's strength in distinguishing clear diagnostic features.
* **`/fail` (Error Analysis)**:
    * *Purpose:* We openly document cases where the model failed.
    * *Observation:* Most errors occur between clinically similar classes (e.g., classifying *Benign Keratosis* as *Melanoma*).
    * *Value:* Analyzing these failures provides transparency and points out directions for future improvements (e.g., need for more hard-negative mining).

---
**Author:** Nurbol Agybetov, Yermek Khaknazar, Baglan Yessenkeldi, Tokhtar Nuralin, Alisher Mukanov 

**Course:** Research Methods and Tools

**Institution:** Astana IT University

**Date:** 18 November 2025
