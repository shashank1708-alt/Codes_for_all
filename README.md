# Codes_for_all
# 🌿 Spatial Ecology R-Suite: Automated Workflows for Field Biologists

> **Stop fighting with R syntax and get back to the science.** This repository contains a suite of automated, production-ready R scripts designed to streamline data wrangling, spatial preprocessing, and statistical modeling for field biologists, ecologists, and conservation researchers. 

These scripts solve the most common bottlenecks in preparing ecological data for peer-reviewed publication, including `unmarkedFrame` formatting, spatial thinning for MaxEnt, collinearity checks, standardized survey effort aggregation, and multi-model inference.

---

## 📦 What's Included in the Suite?

### 1. Automated GLM Engine (`glm_ecological_workflow.R`)
Perfect for habitat modeling and species distribution analysis.
* **Auto-Scaling:** Standardizes continuous predictors.
* **Collinearity Checks:** Runs Variance Inflation Factor (VIF) scans to catch overlapping variables.
* **Model Selection:** Uses an AICc information-theoretic framework to test parameter combinations and extract the top-performing model.
* **Metrics:** Outputs McFadden’s Pseudo-R², AUC scores, and automatically generates a clean ROC curve graphic.

### 2. Single-Season Occupancy Modeler (`occupancy_workflow.R`)
Bypasses the formatting headaches of the `unmarked` package.
* **Instant Compilation:** Automatically splits raw CSVs into detection histories (y) and site covariates to build `unmarkedFrameOccu` objects.
* **Pre-Built Models:** Fits null, single-covariate, and global models.
* **Ranking & Plotting:** Ranks models via AICc and includes a module to plot occupancy probability against your strongest environmental variable.

### 3. Line Transect & Encounter Rate Calculator (`encounter_rate_calculator.R`)
Automates survey effort tabulation across multiple administrative boundaries (e.g., Reserve Forests).
* **Effort Aggregation:** Sums total kilometers walked per forest block.
* **Zero-Sighting Handling:** Automatically accounts for transects where zero target sightings occurred to ensure unbiased effort calculations.
* **Standardized Output:** Calculates Encounter Rates (e.g., sightings per 10km) and prints a markdown-ready table for easy export to Word/Excel.

### 4. SDM Data Prep Engine (`species_occurrence_sdm_prep.R`)
Processes raw GPS coordinates into MaxEnt-ready spatial data.
* **Spatial Thinning:** Uses `spThin` to remove grid/trail sampling bias from clustered GPS coordinates or camera trap arrays.
* **Background Generation:** Automatically generates random pseudo-absences across the defined study extent using the `terra` package.
* **Data Extraction:** Extracts environmental covariate values from raster stacks (`.tif`) for both presence and background points.
* *(Note: A variation of this script is included for True Presence/Absence datasets).*

### 5. Multi-Model Inference & Averaging Engine (`multi_model_inference.R`)
Automates the rigorous Information-Theoretic approach required by top-tier journals.
* **Environment Safety:** Automatically configures `na.action = "na.fail"` to prevent dataset mismatch errors during dredging.
* **Exhaustive Dredging:** Uses `MuMIn` to test every possible sub-model combination from your global model.
* **Smart Model Averaging:** Isolates competitive models (Delta AICc < 2) and averages their coefficients.
* **RVI Visualization:** Automatically calculates Relative Variable Importance (RVI) and generates a clean, publication-ready horizontal bar chart of the drivers of wildlife abundance.

---

## 🚀 Getting Started

### Prerequisites
* **R** (v4.0.0 or higher recommended)
* **RStudio** ### Installation
1. Clone this repository to your local machine:
   ```bash
   git clone [https://github.com/YourUsername/Spatial-Ecology-R-Suite.git](https://github.com/YourUsername/Spatial-Ecology-R-Suite.git)
