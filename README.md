# Survival Analysis of Political Leaders' Time in Office

📓 **For the full analysis and code, see the [notebook](survival_analysis_example.ipynb).** The sections below give a brief summary of the project and its findings.

This project uses survival analysis to examine how long political leaders remain in office and whether regime type affects their risk of leaving power. It applies Kaplan–Meier estimation, log-rank testing, and Cox proportional hazards modeling to 1,808 leader spells across 200 countries from 1946 to 2008.

## Research Question

Do leaders in non-democracies stay in office longer than leaders in democracies?

## Data

The [Democracy and Dictatorship dataset](https://lifelines.readthedocs.io/en/latest/lifelines.datasets.html) (Cheibub, Gandhi & Vreeland, 2010), available through the `lifelines` Python package. Each observation is one leader's continuous spell in office; leaders who died in office or were still in office in 2008 are treated as right-censored.

## Methods

- **Kaplan–Meier estimation** of the probability of remaining in office over time, overall and by regime type
- **Log-rank test** comparing survival between democracies and non-democracies
- **Restricted mean survival time (RMST)** to compare average years in office within the first 20 years
- **Cox proportional hazards model** with standard errors clustered by country, including a check of the proportional hazards assumption

## Key Findings

- Median time in office was **3 years** for democratic leaders and **6 years** for non-democratic leaders.
- Survival curves differed significantly by regime type (log-rank χ²(1) = 260.47, p < 0.001).
- Democratic leaders faced **2.62 times** the hazard of leaving office (95% CI [2.13, 3.22]).
- The proportional hazards assumption was violated for regime type, so the hazard ratio reflects an average effect over time.

## Tools

- Python 3.13
- pandas 2.2.3
- lifelines 0.30.3
- matplotlib 3.10.0
- Jupyter Notebook 