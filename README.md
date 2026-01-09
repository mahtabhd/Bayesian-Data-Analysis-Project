# Modeling Glycohemoglobin Variation with Hierarchical Bayesian Methods

This repository contains a group project for a Bayesian Data Analysis course, investigating how glycohemoglobin (HbA1c) levels vary with age and waist circumference, and whether these relationships differ across racial and income groups using hierarchical Bayesian modeling.

## Project Overview

Glycohemoglobin (HbA1c) is a key clinical marker for long-term blood glucose control and early detection of diabetes risk.  
This project applies Bayesian regression models to NHANES data to:

- Model HbA1c as a function of **age** and **waist circumference**
- Compare **non-hierarchical** and **hierarchical (partial pooling)** models
- Assess whether **race** and **income** explain meaningful variation in HbA1c
- Evaluate robustness using **posterior predictive checks**, **PSIS-LOO cross-validation**, and **prior sensitivity analysis**

All models are implemented using **`brms`** with a **Student-t likelihood** to handle heavy tails and outliers.

## Data

- **Source:** National Health and Nutrition Examination Survey (NHANES), CDC
- **Sample size:** 6,264 individuals after filtering and preprocessing
- **Key variables used:**
  - Glycohemoglobin (HbA1c)
  - Age (standardized)
  - Waist circumference (standardized)
  - Race / ethnicity
  - Income group

Only predictors that are **easy to self-measure** and clinically meaningful were used.

## Models Implemented

1. **Intercept-only baseline model**
2. **Non-hierarchical regression**
   - Age, waist circumference, race
3. **Hierarchical model (income-level intercepts)**
4. **Hierarchical model (race-level intercepts and slopes)**
5. **Hierarchical model (race + income)**

Model comparison is performed using **PSIS-LOO**, and robustness is assessed via **power-scaling sensitivity analysis (`priorsense`)**.

## Key Findings

- **Age and waist circumference are strong predictors** of HbA1c across all models.
- **Hierarchical models with race-level variation perform best** in predictive accuracy.
- **Income-level variation contributes very little** and does not improve predictions.
- Predictor effects are largely **consistent across groups**, with limited slope variation.
- All main conclusions are **robust to prior and likelihood perturbations**.


## Requirements

- R (≥ 4.2)
- Packages:
  - `brms`
  - `cmdstanr`
  - `tidybayes`
  - `loo`
  - `priorsense`
  - `ggplot2`, `dplyr`, `gridExtra`

Stan must be installed via `cmdstanr`.

## How to Run

1. Install required R packages
2. Install CmdStan via `cmdstanr::install_cmdstan()`
3. Open `project_code.qmd`
4. Render or run interactively in RStudio / Quarto

## Authors

- Mahtab Hosseinidolama  
- An Binh Bui  
- Harsh Rathee  

## Notes

This repository is intended for **educational and methodological demonstration** purposes.  
It is **not** a clinical decision-support tool.


