# Early Preeclampsia Detection Using XGBoost-Cox Proportional Hazard Model

This repository contains the R Markdown source code and project configuration files for preeclampsia survival modeling using the **XGBoost-Cox** algorithm.

## 📖 How to Cite

This codebase supports both the peer-reviewed journal publication and the underlying Master's thesis research. If you use or reference this repository, please cite:

### 1. Peer-Reviewed Journal Article (Primary Reference)
> Syahdwinata, A. W., & Abdullah, S. (2026). Early Preeclampsia Detection Using XGBoost-Cox Proportional Hazard Model. *Indonesian Journal of Statistics and Its Applications*, 9(1), 33–45. https://doi.org/10.29244/ijsa.v9i1p33-45

* **Journal Link**: [IJSA IPB - Article 1289](https://journal-stats.ipb.ac.id/index.php/ijsa/article/view/1289)

### 2. Master's Thesis (Extended Methodology & Analytical Framework)
> Syahdwinata, A. W. (2025). *Deteksi Dini Preeklamsia Menggunakan XGBoost-Cox Proportional Hazard Model* [Tesis magister, Universitas Indonesia]. Perpustakaan Universitas Indonesia. https://lib.ui.ac.id/detail?id=9999920583461&lokasi=lokal#parentHorizontalTab1

* **Thesis Repository**: [UI Library Catalog](https://lib.ui.ac.id/detail?id=9999920583461&lokasi=lokal#parentHorizontalTab1) *(Note: Full text access is restricted to UI Library members)*

---

## 📁 Repository Structure

* `XGB-Cox.Rmd`: Primary R Markdown script containing data analysis, model training, and evaluation.
* `XGBoost_Survival.Rproj`: RStudio project file for environment setup.
* `renv.lock`: Package dependency lockfile ensuring computational reproducibility.
* `best_params.rds`: Saved optimal hyperparameters for the XGBoost model.
* `dummy_data.csv`: Synthetic dummy dataset for testing and reproducing the pipeline.

---

## 🔒 Data Privacy & Reproducibility Notice

Due to patient confidentiality and medical data privacy regulations, the original clinical dataset (`Final.xlsx`) is excluded from this repository. 

To allow code reproducibility, a **synthetic dummy dataset (`dummy_data.csv`)** generated with identical structure and variable signatures is provided.

### 📋 Data Dictionary (Codebook)

| No | Variable Name | Type | Description | Coding / Units |
|---|---|---|---|---|
| 1 | `First Pregnancy` | Categorical | First pregnancy indicator | 0 = No, 1 = Yes |
| 2 | `class Age` | Categorical | Age category | 0 = ≥40, 1 = <40 |
| 3 | `class BMI` | Categorical | BMI category | 0 = ≥35, 1 = <35 kg/m² |
| 4 | `Conception` | Categorical | Conception mode | 0 = Spontaneous, 1 = IVF |
| 5 | `PreviousgestationalHT` | Categorical | History of gestational hypertension | 0 = No, 1 = Yes |
| 6 | `PreviousPE` | Categorical | History of preeclampsia | 0 = No, 1 = Yes |
| 7 | `APS` | Categorical | Antiphospholipid Syndrome | 0 = No, 1 = Yes |
| 8 | `DiabetesMellitusType2` | Categorical | Type 2 Diabetes status | 0 = No, 1 = Yes |
| 9 | `ChronicHT` | Categorical | Chronic hypertension status | 0 = No, 1 = Yes |
| 10 | `AnyFamilyhistoryofPE` | Categorical | Family history of preeclampsia | 0 = No, 1 = Yes |
| 11 | `Previousgestationaldiabetes` | Categorical | History of gestational diabetes | 0 = No, 1 = Yes |
| 12 | `Smoking` | Categorical | Smoking status | 0 = No, 1 = Yes |
| 13 | `UseofAspirin` | Categorical | Aspirin use during pregnancy | 0 = No, 1 = Yes |
| 14 | `UseofantiHTdrug` | Categorical | Anti-hypertensive drug use | 0 = No, 1 = Yes |
| 15 | `UseofInsulin` | Categorical | Insulin use | 0 = No, 1 = Yes |
| 16 | `CRL mm` | Numerical | Crown-rump length | mm |
| 17 | `Weeks GA Delivery` | Numerical | Gestational age at delivery (Time-to-event) | Weeks |
| 18 | `PE` | Categorical | Preeclampsia event indicator (Status) | 0 = No (Censored), 1 = Yes (Event) |
| 19 | `MAP` | Numerical | Mean arterial pressure | mmHg |
| 20 | `MeanUtAPI` | Numerical | Mean uterine artery pulsatility index | Index |
| 21 | `Opthalmica` | Numerical | Ophthalmic artery Doppler | Index |
| 22 | `PLGFconcentration pgml` | Numerical | Maternal PLGF concentration | pg/mL |

---
## 💡 Key Findings & Analytical Insights

### 1. Model Discrimination & Risk Stratification
* **Superior Predictive Accuracy**: The **XGBoost-Cox** model achieved a significantly higher $C\text{-index}$ of **0.8907** compared to **0.7547** from the baseline Cox-PH model, demonstrating superior capability in ranking patient preeclampsia risk.
* **Enhanced Risk Stratification**: Kaplan-Meier survival curves revealed that XGB-Cox cleanly separated patients into distinct risk quartiles, whereas the standard Cox-PH model suffered from overlapping moderate-risk groups.
* **Calibration Dynamics over Gestational Time**: Time-dependent **Brier Scores** showed that XGB-Cox consistently provided better-calibrated risk probabilities throughout early-to-mid pregnancy, though accuracy converged with Cox-PH towards late-stage gestation.

---

### 2. Feature Importance & Clinical Interpretability (Gain Metric)
While Cox-PH provides direct Hazard Ratios, XGBoost-Cox balances high predictive accuracy with model interpretability via **Gain-based Feature Importance** (quantifying each feature's contribution to split quality across decision trees):

* **Top Clinical Drivers**: `FinalMAP` (Mean Arterial Pressure), `FinalOpthalmica` (Ophthalmic Artery Doppler), and `FinalMeanUtAPI` (Uterine Artery Pulsatility Index) emerged as the primary predictors for early detection.
* **Secondary Biomarkers & Metrics**: `PLGFconcentration pgml` (Placental Growth Factor) and `CRL mm` (Crown-Rump Length) contributed significantly to overall model split accuracy.
* **Lower Relative Contribution**: Anamnesis history such as `PreviousPE` demonstrated lower relative importance when continuous clinical and Doppler measurements were present.

> 📊 **Data Science Takeaway**: Tree-based gradient boosting effectively captures non-linear interactions among maternal risk factors that standard linear Cox models miss, without sacrificing clinical interpretability.

---

### 3. Data Sensitivity Analysis (Censoring Rate)
* **Robustness & Stability**: Evaluation of censorship impact revealed that a censoring proportion exceeding **>55%** negatively impacts model stability, with XGB-Cox exhibiting higher sensitivity to right-censored data than traditional Cox-PH.
* **Engineering Implication**: Highlights the critical need for balanced survival data selection and careful handling of censored patient timelines in real-world clinical deployments.

## 🚀 How to Run

1. Clone this repository or download it as a ZIP.
2. Open `XGBoost_Survival.Rproj` in RStudio.
3. Run `renv::restore()` in the R console to install the exact package versions.
4. Replace the input file name in `XGB-Cox.Rmd` with `dummy_data.csv` (or your own dataset following the codebook structure) and knit/run the chunk.


