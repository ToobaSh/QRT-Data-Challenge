# QRT-Data-Challenge


#  Predicting Survival in Adult Myeloid Leukemia Patients
> A machine learning project for survival analysis using clinical and molecular data — QRT 2025 Data Challenge (Institut Gustave Roussy)

![Leukemia](https://img.icons8.com/color/48/000000/dna-helix.png) ![Survival](https://img.icons8.com/color/48/000000/heart-with-pulse.png) ![Python](https://img.shields.io/badge/Python-3.8+-blue.svg) ![scikit-survival](https://img.shields.io/badge/scikit--survival-0.20+-orange)

---

##  Project Overview

This repository contains my solution for the **QRT 2025 Data Challenge**, conducted in partnership with [Institut Gustave Roussy](https://www.gustaveroussy.fr/), one of Europe’s largest cancer centers.

The goal: **predict overall survival (OS)** for patients diagnosed with **adult myeloid leukemias**, using clinical and genomic data collected from 24 medical centers.

---

##  Challenge Objective

1.  Predict the **risk of death** from blood cancer  
2.  Use **IPCW-Concordance Index (C-index)** as the main evaluation metric  
3.  Work with **real patient data**: clinical variables and somatic mutations  
4.  Support **personalized medicine** through risk stratification

---

##  Dataset Description

- **Train patients**: 3,323  
- **Test patients**: 1,193  
- **Data sources**:
  - Clinical features (blood counts, cytogenetics, etc.)
  - Somatic mutation profiles
- **Targets**:
  - `OS_YEARS`: Overall survival time in years
  - `OS_STATUS`: Censored survival status (1 = death, 0 = alive)

---

##  Tools & Libraries

- `pandas`, `numpy`, `matplotlib`, `seaborn`
- `scikit-survival` for survival models and IPCW-C-index
- `ExtraSurvivalTrees` (non-parametric survival model)
- `LightGBM` and `Cox Proportional Hazards` (benchmarking)

---

##  Methodology

###  Feature Engineering Highlights

 **From Molecular Data**
- Total mutation count (`Nmut`)
- Mean Variant Allele Fraction (`VAF_mean`)
- Gene-specific VAFs for `TP53`, `FLT3`, `SRSF2`
- Frameshift mutation ratio

 **From Cytogenetics**
- Duplication, deletion, and translocation event counts
- Mutation density on chromosomes 7 and X
- Abnormality complexity (`cytogenetics_abnormalities`)

###  Model

- Trained an **Extra Survival Trees** model on clinical + genomic features
- Evaluated with **IPCW-C-index** (handles right-censored data)
- Survival-aware preprocessing with median imputation

---

##  Visualizations

- Feature correlations
- Mutation load by survival outcome
- VAF distributions for high-impact genes
- Feature importance from Extra Survival Trees
- Kaplan-Meier survival curves (high-risk vs. low-risk)

---

##  Evaluation

| Model                  | IPCW C-Index (Test Set) |
|------------------------|-------------------------|
| Extra Survival Trees   | `0.76722904`                |
| CoxPH (benchmark)      | `0.66`                |

