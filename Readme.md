# Supercapacitor Capacitance Predictor ⚡

This project focuses on predicting the **specific capacitance (F/g)** of **carbon-based supercapacitors** using machine learning techniques.  
By leveraging material properties, pore structure, electrolyte type, and electrochemical parameters, the model helps estimate performance without extensive experimental trials.

---

## 📌 Project Overview

Supercapacitors are widely used in energy storage applications due to their high power density and long cycle life.  
However, experimentally determining capacitance for new materials is time-consuming and costly.

This project:
- Cleans and preprocesses a real-world materials dataset
- Handles missing values using domain knowledge
- Applies feature encoding and scaling
- Trains machine learning regression models
- Evaluates performance using standard metrics

---

## 📊 Dataset Description

The dataset contains experimental data of **carbon-based supercapacitors**, including:

- Material composition
- Doping percentages (N, O, B, S, F, P)
- Structural properties (surface area, pore volume)
- Electrolyte type
- Voltage window
- Target variable: **Capacitance (F/g)**

### Dropped Columns
Some non-informative or text-heavy columns were removed:
- `DOI`
- `Materials-2`
- `Materials-note`

---

## 🧹 Data Preprocessing

### 1. Missing Value Handling
- Doping elements (`N`, `O`, `B`, `S`, `F`, `P`) → filled with **0** (assumed no doping)
- `Pore volume (cm³/g)` → filled using **median**
- Certain micropore-related columns were removed to avoid redundancy

### 2. Encoding
- Categorical features encoded using **Label Encoding**
  - `Materials-1`
  - `Electrolyte`

### 3. Outlier Handling
- Outliers detected using **IQR method**
- Extreme values were clipped within acceptable bounds

### 4. Feature Scaling
- **RobustScaler** used to handle skewed distributions and outliers

---

## 🧠 Models Used

### ✅ Random Forest Regressor
- `n_estimators = 200`
- Captures non-linear relationships effectively
- Robust to noise and overfitting
Example output:
```text
  R-squared: 0.5287125823002969
  Mean Absolute Error: 0.39373317320578183
  Mean Squared Error: 0.2717238289811465



### XGBoost Regressor
- Imported for experimentation and future comparison

---

## 📈 Model Evaluation Metrics

The model performance is evaluated using:

- **R² Score** – goodness of fit
- **Mean Absolute Error (MAE)**
- **Mean Squared Error (MSE)**


