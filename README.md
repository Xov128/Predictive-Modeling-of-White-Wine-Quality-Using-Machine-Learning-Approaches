# Predictive-Modeling-of-White-Wine-Quality-Using-Machine-Learning-Approaches
# 🍷 White Wine Quality Prediction
> Predictive modeling of white wine quality using Random Forest classification on physicochemical features.

**Authors:** Bryan Yiling · Cornelius Christian Setiadi · Josua Edward Budianto · Jovan Melsyah · Lubin Abhimata Susilo · Nicholas Vincent Effendi  
**Institution:** Computer Science and Statistics, Binus University, Indonesia

---

## Overview

Wine quality assessment traditionally depends on human sensory evaluation, which is subjective and inconsistent. This project applies machine learning to predict white wine quality scores from physicochemical measurements, enabling a more objective and reproducible approach.

The model achieved **69% classification accuracy** on a held-out test set, with alcohol content, volatile acidity, and density identified as the top predictors.

---

## Dataset

**Source:** [UCI Wine Quality Dataset](https://archive.ics.uci.edu/ml/datasets/wine+quality) (White Wine)  
**File:** `winequality-whiteDatasets.csv`  
**Format:** Semicolon-separated (`;`)  
**Rows:** ~4,898 samples  
**Target:** `quality` — integer score from 0 to 10, assigned by human tasters

| Feature | Description |
|---|---|
| `fixed.acidity` | Non-volatile acids in wine |
| `volatile.acidity` | Acetic acid content |
| `citric.acid` | Adds freshness and flavor |
| `residual.sugar` | Sugar remaining after fermentation |
| `chlorides` | Salt content |
| `free.sulfur.dioxide` | Free form of SO₂ |
| `total.sulfur.dioxide` | Total SO₂ (free + bound) |
| `density` | Density of the wine |
| `pH` | Acidity level |
| `sulphates` | Additive contributing to SO₂ |
| `alcohol` | Alcohol percentage |
| `quality` | **Target variable** (0–10) |

---

## Methodology

### Exploratory Data Analysis
Three types of visualizations were used to explore the data:

- **Correlation Heatmap** — reveals linear relationships between all variables
- **Scatterplot Matrix (GGally)** — pairwise distributions and correlations
- **Violin Plots** — distribution of each feature across quality classes

### Model
A **Random Forest classifier** was trained after converting the `quality` column to a factor (treating it as a categorical ordinal variable rather than a continuous value).

| Parameter | Value |
|---|---|
| `ntree` | 1300 |
| `mtry` | 4 |
| Train / Test split | 80% / 20% |
| Random seed | 123 |

### Evaluation Metrics
- Overall Accuracy
- Confusion Matrix
- Per-class Precision, Recall, and F1-Score
- Variable Importance Plot

---

## Results

| Metric | Value |
|---|---|
| Overall Accuracy | **~69%** |
| Best-predicted classes | 5 and 6 (majority classes) |
| Weakest classes | 3, 4, 8, 9 (minority classes) |

### Per-class Performance

| Quality | Precision | Recall | F1 |
|---|---|---|---|
| 4 | 0.750 | 0.240 | 0.364 |
| 5 | 0.739 | 0.694 | 0.716 |
| 6 | 0.656 | 0.822 | 0.729 |
| 7 | 0.702 | 0.535 | 0.607 |
| 8 | 1.000 | 0.250 | 0.400 |

### Top Predictors (Variable Importance)

1. Alcohol
2. Volatile Acidity
3. Density
4. Free Sulfur Dioxide
5. Total Sulfur Dioxide

---

## Getting Started

### Requirements

Install the required R packages before running the script:

```r
install.packages(c("ggplot2", "tidyr", "reshape2", "randomForest", "GGally"))
```

Optionally, install `caret` for a richer confusion matrix report:

```r
install.packages("caret")
```

### Running the Script

1. Clone this repository and place `winequality-whiteDatasets.csv` in the working directory.
2. Open `RCode.R` in RStudio or any R environment.
3. Run the script. It will:
   - Load and summarize the dataset
   - Generate the correlation heatmap, scatterplot matrix, and violin plots
   - Train the Random Forest classifier
   - Print the confusion matrix, accuracy, and per-class metrics
   - Plot variable importance

```r
source("RCode.R")
```

---

## Project Structure

```
.
├── RCode.R                          # Main analysis and modeling script
├── winequality-whiteDatasets.csv    # Dataset (semicolon-separated)
└── README.md                        # Project documentation
```

---

## Key Findings

- **Alcohol** is the strongest single predictor of wine quality — higher alcohol content correlates with higher scores.
- **Density** shows a strong negative correlation with both alcohol and quality, since denser wines tend to have more residual sugar and less alcohol.
- **Volatile acidity** and **chlorides** negatively affect quality, reflecting how excessive acidity or salinity harms sensory perception.
- The model performs well on mid-range quality classes (5 and 6) but struggles with extremes (3, 4, 8, 9) due to class imbalance.

---

## Future Work

- Handle class imbalance using SMOTE or class weighting
- Compare with Gradient Boosting (XGBoost/LightGBM) and SVM
- Hyperparameter tuning via cross-validation
- Incorporate additional sensory or categorical features

---

## License

This project is for academic purposes only.
