# 🌾 Crop Recommendation & Farmer Advisory System

A data-driven machine learning project that recommends optimal crops to farmers based on environmental and soil conditions, helping maximize agricultural yield and support informed farming decisions across India.

---

## 📌 Overview

This project leverages historical crop production data along with environmental parameters — **temperature**, **humidity**, and **soil moisture** — to predict the most suitable crop for a given region and season. It aims to serve as a smart advisory tool for farmers and agricultural policymakers.

---

## 🎯 Objectives

- Predict the best crop to cultivate based on location, season, and environmental conditions
- Provide actionable advisory insights to farmers
- Explore patterns in crop production across Indian states and districts
- Build a deployable application for real-world use

---

## 📁 Project Structure

```
crop-recommendation-farmer-advisory/
│
├── data/
│   ├── raw/                          # Raw, unprocessed dataset
│   │   └── Crop_Prediction_dataset_RAW.csv
│   └── processed/                    # Cleaned & feature-engineered data
│
├── notebooks/                        # Jupyter notebooks for EDA & modeling
│
├── app/                              # Web application (deployment)
│
├── reports/
│   └── figures/                      # Plots, charts, and visualizations
│
└── README.md
```

---

## 📊 Dataset

**File:** `data/raw/Crop_Prediction_dataset_RAW.csv`  
**Records:** ~51,000 rows

### Features

| Column | Description |
|---|---|
| `State_Name` | Indian state where crop is grown |
| `District_Name` | District within the state |
| `Crop_Year` | Year of cultivation |
| `Season` | Growing season (Kharif, Rabi, Autumn, Whole Year, etc.) |
| `Crop` | Target crop (e.g., Rice, Wheat, Tapioca, Papaya) |
| `Temperature` | Ambient temperature (°C) |
| `Humidity` | Relative humidity (%) |
| `Soil_Moisture` | Soil moisture level |
| `Area` | Area under cultivation (hectares) |
| `Production` | Total crop production (tonnes) |

> **Note:** The raw dataset contains inconsistencies in casing and whitespace (e.g., `"  WEST GODAVARI  "`, `"  Rabi         "`). Data cleaning is a key preprocessing step.

---

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3.x |
| Data Processing | Pandas, NumPy |
| Machine Learning | Scikit-learn |
| Visualization | Matplotlib, Seaborn |
| Notebook | Jupyter Notebook |
| App | *(To be defined — Flask / Streamlit)* |
| Version Control | Git |

---

## 🚀 Getting Started

### Prerequisites

```bash
python >= 3.8
pip
```

### Installation

```bash
# Clone the repository
git clone https://github.com/Rohu06/crop-recommendation-farmer-advisory.git
cd crop-recommendation-farmer-advisory

# Install dependencies
pip install -r requirements.txt
```

### Running Notebooks

```bash
jupyter notebook notebooks/
```

---

## 🔄 Workflow

```
Raw Data  →  Data Cleaning  →  EDA  →  Feature Engineering  →  Model Training  →  Evaluation  →  App Deployment
```

1. **Data Cleaning** — Normalize state/district names, handle missing values, standardize seasons
2. **Exploratory Data Analysis (EDA)** — Visualize production trends, seasonal patterns, regional distributions
3. **Feature Engineering** — Encode categorical variables, scale numerical features
4. **Model Training** — Train classification models (e.g., Random Forest, XGBoost) to predict crop type
5. **Evaluation** — Accuracy, confusion matrix, F1-score
6. **Deployment** — Serve predictions via a web application

---

## 📈 Target Crops

The dataset covers a diverse range of crops including:

> Rice, Wheat, Maize, Sugarcane, Cotton, Pulses, Tapioca, Papaya, Arhar/Tur, and many more across Kharif, Rabi, and other seasons.

---

## 🗺️ Geographic Coverage

- **States:** All major Indian states (Assam, Andhra Pradesh, Chhattisgarh, and more)
- **Time Range:** Multi-year historical data (1990s – 2010s)

---

## 📋 Future Enhancements

- [ ] Real-time weather API integration
- [ ] Fertilizer and irrigation recommendations
- [ ] Multi-language support for regional farmers
- [ ] Mobile-friendly advisory interface
- [ ] Market price prediction integration

---

## 🤝 Contributing

Contributions are welcome! Please open an issue or submit a pull request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 👤 Author

**Rohan**  
GitHub: [@Rohu06](https://github.com/Rohu06)

---

*Empowering farmers with data-driven decisions 🌱*
