# Digital Financial Exclusion in Italy: Analysis of IACOFI 2023
Data Science Lab's project - Msc in Data Science (Unimib)

GRADE: 30L

This repository contains the code and analysis pipeline for the research project.

The project investigates the determinants of digital financial exclusion among Italian adults using the **2023 IACOFI survey** (Bank of Italy, $N=4,862$).

## Project Overview

The shift towards digital financial services (online banking, mobile payments, digital investment) creates a risk of exclusion for individuals who do not adopt these tools. This study explores the socio-demographic and financial literacy characteristics that predict non-adoption, and identifies specific vulnerability profiles within the excluded population.

The analysis operationalises digital exclusion at two levels:
1.  **Basic digital divide**: Absence of internet access.
2.  **Digital financial exclusion**: Internet access but low/no use of digital financial tools (measured via a composite Digital Adoption Score).

## Analytical Pipeline

The study is structured into three interconnected sequential phases, implemented across three Jupyter Notebooks:

### 1. Data Preparation (`DataPreparation.ipynb`)
- **Data Cleaning**: Handling special non-response codes (`-97`, `-98`, `-99`, `-999`).
- **Index Creation**: Building a two-level "Digital Financial Exclusion" indicator and a continuous Digital Adoption Score (DAS).
- **Literacy Scoring**: Constructing an objective Financial Literacy Score (0-7) following the standard OECD/INFE methodology.
- **Demographic Formatting**: Collapsing socio-demographic variables (age, education, employment, income) into tractable analytical categories.

### 2. Descriptive Profiling (`DescriptiveAnalysis.ipynb`)
- **Univariate Analysis**: Profiling non-adopters across socio-demographic dimensions using survey-weighted cross-tabulations.
- **Visualizations**: Generating stacked bar charts to illustrate the weighted distribution of digital exclusion status by gender, age, education, geographic area, municipality type, employment, and income.
- **Paradox Identification**: Identifying confounding effects (e.g., the apparent association between high education and exclusion, driven by the elderly cohort).

### 3. Statistical Modelling (`StatisticalModelling.ipynb`)
- **Weighted Logistic Regression**: Estimating the independent association between socio-demographic predictors/financial literacy and the binary digital-exclusion outcome, controlling for all other predictors.
- **K-Means Clustering**: Applying unsupervised clustering on internet users to identify distinct latent profiles based on Digital Adoption, Financial Literacy, Age, Income, and Education.
- **Dimensionality Reduction**: Using PCA projection for visual validation of cluster separation.

## Key Findings

1.  **Overall Exclusion**: 43% of the Italian adult population is digitally financially excluded (10.7% lack internet access, 32.3% have access but make low use of tools).
2.  **Independent Risk Factors**: Older age (60+), retirement/inactivity, low household income, and Southern residence are independent predictors of exclusion.
3.  **Financial Literacy as a Shield**: Higher objective financial literacy is significantly and independently protective against digital exclusion, even after adjusting for income and education.
4.  **Vulnerability Profiles (Clustering)**:
    *   *Doubly vulnerable* (43% excluded): Low literacy + low income.
    *   *Literate late adopters* (41% excluded): High knowledge but behavioural barriers (older adults).
    *   *Educated but excluded elderly* (72% excluded): Old, highly educated, low income, very low digital adoption.

## Repository Structure

- `/notebooks/`
  - `Phase1_Data_Prep.ipynb`: Data cleaning and feature engineering.
  - `Phase2_Descriptive.ipynb`: Descriptive statistics and visualizations.
  - `Phase3_Modelling.ipynb`: Logistic regression and K-means clustering.
- `/data/`
  - `Database_ENG.csv`: Raw IACOFI 2023 dataset (needs to be downloaded from Bank of Italy).
  - `cleaned_dataset.csv`: Processed dataset ready for analysis.
- `/output/`: Generated figures, summary tables, and regression results.
- `DSLab_report_Rubini_Villa.pdf`: The comprehensive final academic report.

## Installation and Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/iacofi-digital-exclusion.git
   ```
2. Install the required dependencies:
   ```bash
   pip install pandas numpy matplotlib scikit-learn statsmodels
   ```
3. Place the raw dataset (`Database_ENG.csv`) in the root or `/data/` directory.
4. Run the notebooks sequentially (Phase 1 $\rightarrow$ Phase 2 $\rightarrow$ Phase 3).

## 📄 Dataset Reference
Banca d'Italia (2023). *Indagine sulle competenze e le abilità finanziarie degli italiani (IACOFI) - Microdati e documentazione*.
Available at: [Banca d'Italia Website](https://www.bancaditalia.it/statistiche/tematiche/indagini-famiglie-imprese/alfabetizzazione/)

---
*Authors: Asia Rubini & Valeria Villa (University of Milano-Bicocca)*
