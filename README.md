# BrainHack_Final_Project: VBM Analysis of sMRI Data in Healthy Individuals 

## Introduction
Previous research have suggest to neural causes for the link between adverse childhood experiences (ACEs) and later psychiatric outcomes (Keator et al., 2024). However, this link is not absolute, such that protective factors can buffer against the influence of ACEs (Crouch et al., 2018). Whilst the neurological consequences of ACEs remain a hot research topic, there exists less work on how resilience may be represented physiologically in individuals with exposure (Torres-Verrio et al., 2025). Using the NIMH Healthy Volunteers Dataset, the current project seeks to extend such work by looking into the neurological differences between healthy individuals based on their ACE exposure, as a proxy for investigating resilience. 

### Research Topic & Question
Do individuals with higher ACE exposure show structural differences compared to individuals with lower ACE exposure?

---

## Dataset Description 
This study uses the NIMH Healthy Research Volunteer Dataset, an open-access multimodal dataset collected by the National Institute of Mental Health Intramural Research Program. The dataset consists of psychiatrically screened healthy adult volunteers aged 18 and above using clinical, behavioural, cognitive, biological and neuroimaging measures. 

--- 

## Repository Structure

| File | Description |
|--------|--------|
| `BrainHack_Project_Analysis_Code.ipnyb` | Main Python Analysis Notebook |
| `Raw_Pheno_Data.xlsx` | Initial Cleaned Data |
| `NIMH_Participants.csv` | Participant Data for VBM Analysis |
| `NIMH_Scans` | Preprocessed sMRI Scans |

___

## Analysis Pipeline

### 1. Data Cleaning (Excel)
Given that the data collection protocol was modified throughout the NIMH Healthy Volunteer project, data was cleaned on excel to select for participants. This included screening of participants to ensure that they had sMRI scans required for analyses, as well as scores for ACEs, PHQ-9, and GAD-7. Regression analyses were performed on R to double-check that participants did not differ on anxiety or depression measures based on their ACE scores, and were all psychologically healthy. 

### 2. Preprocessing (MATLAB SPM12)
Preprocessing of sMRI data was conducted in MATLAB using SPM12. Information regarding initial sMRI data collection procedures are available from Nugent & Colleagues (2022). Preprocessing involved tissue segmentation, spatial normalisation across scans, modulation, and image smoothing. 

### 3. VBM Analysis (Python)
The 54 preprocessed scans were then imported onto a jupyter notebook for Python for the VBM analyses using the nilearn library. Specifically, a Mass-Univariate General Linear Model (GLM) was formulated uing ACE scores, age, sex, total intracranial volume (TIV), and intercept as predictors. This model was then fitted to the voxel-wise data, before a directional t/z-contrast vector was applied to isolate and extract the specific slope of the ACE exposure variable whilst controlling for all other covariates. 

---

## Methodological Discussion

###

---

## Use Guide

### Requirements
- Python 3.x
- Jupyter Notebook
- numpy, pandas, matplotlib, scipy, and nilearn packages.

### Steps
1. Clone this repository.
2. Place `NIMH_Participants.csv` and `NIMH_Scans` in the directory.
3. Launch Jupyter Notebook and run `BrainHack_Project_Analysis_Code.ipnyb`.
---

## Acknowledgements
- We acknowledge the use of AI tools for assistance with coding, language refinement, and technical clarification during the process. The experimental designs, analyses, interpretations, and conclusions presented in this project remain original.

---

## References
Crouch, E., Radcliff, E., Strompolis, M., & Srivastav, A. (2018). Safe, Stable, and Nurtured: Protective Factors against Poor Physical and Mental Health Outcomes Following Exposure to Adverse Childhood Experiences (ACEs). Journal of Child & Adolescent Trauma, 12(2), 165-173. https://doi.org/10.1007/s40653-018-0217-9

Nugent, A. C., Thomas, A. G., Mahoney, M., Gibbons, A., Smith, J., Charles, A., Shaw, J. S., Strout, J. D., Namyst, A. M., Basavaraj, A., Earl, E., Moraczewski, D., Guinee, E., Liu, M., Riddle, T., Snow, J., Japee, S., Andrews, M., Pavletic, A., Sinclair, S., Roopchansingh, V., Bandettini, P. A., & Chung, J. (2025). The NIMH intramural healthy volunteer dataset: A comprehensive MEG, MRI, and behavioral resource. Nature, 9, 518. https://doi.org/10.1038/s41597-022-01623-9

Torres-Berrio, A., Bortolami, A., Pena, C. J., & Nestler, E. J. (2026). Neurobiology of resilience to early life stress. American College of Neuropsychopharmacology, 51, 29-45. https://doi.org/10.1038/s41386-025-02158-4
