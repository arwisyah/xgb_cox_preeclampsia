# Early Preeclampsia Detection Using XGBoost-Cox Proportional Hazard Model

This repository contains the R Markdown source code and project configuration files for preeclampsia survival modeling using the **XGBoost-Cox** algorithm.

## 📖 How to Cite

If you use or reference this codebase, please cite the original article:

> Syahdwinata, A. W., & Abdullah, S. (2026). Early Preeclampsia Detection Using XGBoost-Cox Proportional Hazard Model. *Indonesian Journal of Statistics and Its Applications*, 9(1), 33–45. https://doi.org/10.29244/ijsa.v9i1p33-45 (Original work published June 24, 2025)

* **Journal Article**: [IJSA IPB - Article 1289](https://journal-stats.ipb.ac.id/index.php/ijsa/article/view/1289)
* **DOI**: [10.29244/ijsa.v9i1p33-45](https://doi.org/10.29244/ijsa.v9i1p33-45)

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

## 🚀 How to Run

1. Clone this repository or download it as a ZIP.
2. Open `XGBoost_Survival.Rproj` in RStudio.
3. Run `renv::restore()` in the R console to install the exact package versions.
4. Replace the input file name in `XGB-Cox.Rmd` with `dummy_data.csv` (or your own dataset following the codebook structure) and knit/run the chunk.
