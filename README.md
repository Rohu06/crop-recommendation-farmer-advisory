# Crop Recommendation & Farmer Advisory

An academic machine learning project covering two agricultural prediction problems: **crop recommendation** (classification) and **crop yield prediction** (regression). The project uses real-world soil and climate data sourced from NASA POWER and SoilGrids APIs, applied to Indian agricultural datasets.

---

## Overview

| Problem | Type | Dataset | Crops / Target |
|---|---|---|---|
| Crop Recommendation | Multi-class classification | 11,000 rows, 7 features | 22 crops |
| Crop Yield Prediction | Regression | 5,060 rows, 16 features | Yield in kg/ha |

---

## Project Structure

```
crop-recommendation-farmer-advisory/
├── app/
│   └── models/              # Reserved for deployed model artifacts
├── data/
│   ├── Crop_Recommendation_Dataset.csv       # Original clean dataset
│   ├── Crop_Recommendation_RAW_garbled.csv   # Intentionally dirtied (for cleaning exercise)
│   ├── Crop_Recommendation_CLEANED.csv       # Cleaned output
│   ├── crop_yield_dataset.csv                # Maharashtra crop yield (5,060 rows)
│   ├── india_yield_augmented.csv             # Augmented with climate + soil features
│   └── .cache/                               # ~358 cached NASA POWER & SoilGrids responses
├── models/
│   ├── yield_model.joblib
│   ├── yield_linear_model.joblib
│   └── maharashtra_linear_model.joblib
├── notebooks/
│   └── crop_recommendation_assignment.ipynb  # Classification pipeline (main notebook)
└── scripts/
    ├── Crop_Yield_Data_Preprocessing_Assignment_1.ipynb
    ├── Assignment2_EDA_Linear_Regression.ipynb
    └── Assignment_3_CropYield.ipynb
```

---

## Notebooks

### `notebooks/crop_recommendation_assignment.ipynb`
End-to-end crop recommendation pipeline:
- Deliberately garbles clean data, then applies a full cleaning pipeline
- Exploratory data analysis (EDA)
- Trains `RandomForestClassifier` and `LogisticRegression`
- Evaluates overfitting and classification assumptions

### `scripts/Crop_Yield_Data_Preprocessing_Assignment_1.ipynb`
Data preprocessing for yield prediction:
- Handles missing values, duplicates, inconsistent text, type errors, outliers
- Feature encoding and scaling on the 5,060-row Maharashtra yield dataset

### `scripts/Assignment2_EDA_Linear_Regression.ipynb`
EDA and multiple linear regression:
- Visualizations and statistical analysis
- Baseline MLR model evaluated with MAE, MSE, and R²
- 5-fold cross-validation

### `scripts/Assignment_3_CropYield.ipynb`
Regularization and model comparison:
- Ridge (L2) and Lasso (L1) regression vs. baseline MLR
- Segregates sugarcane (~62,000 kg/ha) from grain crops to prevent regression distortion
- Log-scale grid search for optimal alpha via 5-fold CV

---

## Tech Stack

| Layer | Technology |
|---|---|
| Language | Python 3.14 |
| Notebooks | JupyterLab 4.6.3 / Jupyter Notebook 7.6.2 |
| Data | pandas 3.0.5, numpy 2.5.2 |
| ML | scikit-learn 1.9.0 |
| Model serialization | joblib 1.5.3 |
| Visualization | matplotlib 3.11.1, seaborn 0.13.2 |
| Statistics | scipy 1.18.1 |
| External APIs | NASA POWER, SoilGrids, geocoding |
| HTTP | requests 2.34.2 |

---

## External Data

A geocoding utility fetched coordinates for ~262 Indian districts. Climate and soil data were then pulled for each district and cached locally:

- **NASA POWER API** — monthly solar radiation, precipitation, temperature (min/max/mean), humidity, wind speed
- **SoilGrids API** — soil composition per district

All responses are cached under `data/.cache/` to avoid repeated API calls.

---

## Setup

1. Clone the repository:
   ```bash
   git clone <repo-url>
   cd crop-recommendation-farmer-advisory
   ```

2. Create and activate a virtual environment:
   ```bash
   python -m venv .venv
   # Windows
   .venv\Scripts\activate
   # macOS / Linux
   source .venv/bin/activate
   ```

3. Install dependencies (based on notebook imports):
   ```bash
   pip install pandas numpy scikit-learn joblib matplotlib seaborn scipy requests jupyterlab
   ```

4. Launch JupyterLab:
   ```bash
   jupyter lab
   ```

---

## Models

Pre-trained serialized models are stored in `models/` and can be loaded directly:

```python
import joblib

model = joblib.load("models/yield_model.joblib")
prediction = model.predict(X)
```

---

## Dataset: Crop Recommendation

- **Rows:** 11,000 (500 per crop, perfectly balanced)
- **Features:** N, P, K (soil nutrients), temperature, humidity, pH, rainfall
- **Target:** One of 22 crops (e.g., rice, maize, chickpea, mango, coffee)

## Dataset: Crop Yield

- **Rows:** 5,060
- **Features:** District, Year, Crop, Season, soil nutrients, climate variables, irrigation type, area cultivated
- **Target:** Yield (kg/ha)
- **Note:** Sugarcane is modeled separately due to its anomalously high yield values
