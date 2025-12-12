# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**OpenClassrooms Data Science Project 3: Seattle Building Energy Emissions Prediction**

This is an academic supervised learning project for the OpenClassrooms Data Science & Machine Learning program. The mission is to help the city of Seattle achieve carbon neutrality by 2050 by predicting CO2 emissions and energy consumption for non-residential buildings.

**Key Context:**
- **Dataset:** 2016 Building Energy Benchmarking data (3,376 buildings, 46 features)
- **Primary Target Variable:** `TotalGHGEmissions` (CO2 emissions in metric tons)
- **Scope:** Non-residential buildings only (Multifamily residential buildings excluded from modeling)
- **GitHub Repository:** https://github.com/Hadri2T/OpenClassroom_projet_3.git

## Project Structure

```
Projet_3/
├── 2016_Building_Energy_Benchmarking.csv  # Main dataset (DO NOT MODIFY)
├── P3_template_modelistation_supervisee_data_scientist.ipynb  # Primary work file
└── P3_template_modelistation_supervisee_data_scientist.ipynb.bak  # Backup (can be deleted)
```

**IMPORTANT:** This is a template-driven project. The notebook contains structured sections with clear instructions and placeholders for code implementation.

## Development Environment

**Python Version:** 3.11.5
**Jupyter Kernel:** oc_sql

**Required Libraries:**
```python
pandas              # Data manipulation
matplotlib          # Plotting
seaborn            # Statistical visualizations
scikit-learn       # Machine learning (model_selection, metrics, inspection, preprocessing, compose, dummy, linear_model, svm, ensemble)
```

**Note:** No `requirements.txt` file exists yet. When creating one, include the above packages.

## Dataset Details

**File:** `2016_Building_Energy_Benchmarking.csv`
- **Size:** 1.2 MB (3,377 rows including header)
- **Columns:** 46 features
- **DO NOT MODIFY THIS FILE** - It's the source data

**Key Features:**
- **Identifiers:** OSEBuildingID, PropertyName, Address, TaxParcelIdentificationNumber
- **Location:** City, State, ZipCode, Latitude, Longitude, Neighborhood, CouncilDistrictCode
- **Building Info:** BuildingType, PrimaryPropertyType, YearBuilt, NumberofBuildings, NumberofFloors, PropertyGFATotal, PropertyGFAParking, PropertyGFABuilding(s)
- **Usage Types:** ListOfAllPropertyUseTypes, LargestPropertyUseType, SecondLargestPropertyUseType, ThirdLargestPropertyUseType
- **Energy Metrics:** Electricity (kWh/kBtu), NaturalGas (therms/kBtu), SiteEnergyUse, SourceEnergyUse, SiteEUI, SourceEUI, SteamUse
- **Target Variables:** TotalGHGEmissions (PRIMARY), GHGEmissionsIntensity
- **Certification:** ENERGYSTARScore, YearsENERGYSTARCertified
- **Quality:** DefaultData, Comments, ComplianceStatus, Outlier

**Building Types:**
- NonResidential (1,460 buildings)
- Multifamily LR/MR/HR (1,708 buildings - EXCLUDED from modeling)
- SPS-District K-12 (98 buildings)
- Nonresidential COS (85 buildings)
- Campus (24 buildings)
- Nonresidential WA (1 building)

## Current Project Status

**Completed:**
✅ Section 1: Introduction and project setup
✅ Section 2: Exploratory Data Analysis (80% complete)
  - Data loading and inspection
  - Missing values analysis
  - Building type categorization
  - Outlier identification (32 outliers flagged)
  - Data filtering (removed Multifamily buildings → 1,668 rows remaining)
  - Column cleanup (dropped: Comments, Outlier, DataYear, State, City, DefaultData)

**In Progress:**
⚠️ Section 2: Feature engineering (correlation analysis, redundancy removal pending)

**Not Started:**
❌ Section 3: Feature preparation for modeling
❌ Section 4: Model comparison (DummyRegressor, LinearRegression, SVR, RandomForestRegressor)
❌ Section 5: Model optimization (GridSearchCV) and feature importance analysis

## Workflow and Deliverables

**Project Objectives (per Project Lead Douglas):**
1. **EDA:** Short analysis highlighting key insights about different buildings
2. **Model Testing:** Test multiple supervised learning models to predict energy consumption
3. **Feature Importance:** Determine main factors impacting the selected model

**Required Deliverables:**
- Trained model for predicting `TotalGHGEmissions`
- Performance metrics: R², MAE, RMSE (both train and test sets)
- Feature importance rankings
- Insights on key drivers of emissions

## Key Decisions Made

**Data Cleaning Decisions:**
- **Dropped Columns:** Comments (100% null), Outlier (marker only), DataYear (constant), State (constant), City (constant), DefaultData (unexplained)
- **Retained Columns:** All other features for potential use in modeling
- **Filtered Buildings:** Removed all Multifamily buildings (residential) to focus on non-residential only
- **Outliers:** 32 flagged (23 low, 9 high) - handling strategy TBD

**Feature Engineering:**
- Created `is_multi_usage` boolean: buildings with secondary uses
- Created `building_category` categorical: "Résidentiel pur", "Résidentiel mixte", "Non-résidentiel"

## Modeling Instructions

**Models to Test (imports already in notebook):**
1. DummyRegressor (baseline)
2. LinearRegression
3. SVR (Support Vector Regression)
4. RandomForestRegressor

**Required Steps:**
1. Train-test split with cross-validation
2. Feature scaling (StandardScaler) for algorithms sensitive to scale (Linear, SVM)
3. Model training on train set
4. Inference on test set
5. Calculate R², MAE, RMSE for both train and test
6. Select best model
7. GridSearchCV on 3+ hyperparameters
8. Feature importance (`.feature_importances_` for tree models, `permutation_importance` for others)

## Important Constraints

**Academic Project Rules:**
- This is a template-guided project - follow the structure provided
- Implement code in designated placeholder sections (`# CODE PREPARATION DES FEATURES`, etc.)
- Focus on non-residential buildings only
- Primary target: `TotalGHGEmissions`
- Must test at least 3 different model types
- Must optimize best model with GridSearchCV
- Must provide feature importance analysis

**Data Integrity:**
- NEVER modify the CSV file directly
- Always work on DataFrame copies when experimenting
- The notebook already created `copy_building_consumption` for safety

## Git Workflow

**Current State:**
- Branch: `main`
- Remote: https://github.com/Hadri2T/OpenClassroom_projet_3.git
- Commits: Only 1 ("Début du projet")
- Uncommitted changes: Modified notebook file

**Best Practices for This Project:**
- Commit after completing each major section
- Use meaningful commit messages in French (project language)
- Do not commit the `.bak` backup file (should be gitignored)

## Code Style Notes

**Language:** Comments and markdown cells are in French (this is a French academic program)

**Notebook Structure:**
- Markdown cells explain each section
- Code cells contain implementation
- Visualizations use matplotlib/seaborn with French labels
- Results are displayed inline

**Naming Conventions:**
- DataFrame: `building_consumption` (main working copy)
- Backup: `copy_building_consumption`
- Features: typically keep original column names from CSV
- New engineered features: snake_case (e.g., `is_multi_usage`, `building_category`)

## References

**Kaggle Example:** https://www.kaggle.com/code/pmarcelino/comprehensive-data-exploration-with-python
(Referenced in notebook as inspiration for EDA approach - not a strict template)

## Next Immediate Steps

When continuing work on this project:
1. Complete correlation matrix and heatmap for redundancy analysis
2. Finalize outlier handling strategy
3. Implement feature encoding (OneHot or Label encoding for categoricals)
4. Prepare X (features) and y (target) split
5. Implement model comparison code in Section 4
6. Proceed with optimization in Section 5
