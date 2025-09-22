# 📊 IoT Pond Data Analysis & Fish Weight Prediction

This project performs **data cleaning, exploratory data analysis (EDA), outlier detection, and linear regression modeling** on an IoT Pond dataset (`IoTPond7.csv`).  
The goal is to understand water quality parameters and build a predictive model to estimate **fish weight from fish length**.

---

## 📂 Project Structure

- `IoTPond7.csv` → Raw dataset with pond monitoring data.
- `analysis.ipynb` → Jupyter Notebook containing data preprocessing, visualization, and modeling.
- `README.md` → Project documentation.

---

## 📑 Dataset Information

The dataset contains **279,612 rows** and **14 columns**, including:

- `created_at` → Timestamp of data collection  
- `Date` → Date of record  
- `temperature(C)` → Water temperature in Celsius  
- `turbidity (NTU)` → Water turbidity level  
- `Dissolved Oxygen (g/ml)` → Oxygen concentration  
- `PH` → Water pH level  
- `ammonia(g/ml)` → Ammonia content  
- `nitrate(g/ml)` → Nitrate concentration  
- `Length` → Fish length (cm)  
- `Weight` → Fish weight (g)  

Some unnamed columns (`Unnamed: 11, 12, 13`) contain null values and were dropped during preprocessing.

---

## ⚙️ Steps Performed

### 1. Data Loading & Inspection
- Loaded dataset using **pandas**.
- Checked shape: `(279612, 14)`.
- Renamed `Fish_length(cm)` → `Length`, `Fish_weight(g)` → `Weight`.

### 2. Data Cleaning
- Dropped irrelevant columns: `created_at, Unnamed: 11, 12, 13`.
- Handled missing values (`ammonia(g/ml)` had ~94k nulls).
- Removed records with invalid weight values (≤ 0).
- Final dataset shape after cleaning: `(279611, 10)`.

### 3. Exploratory Data Analysis (EDA)
- **Correlation Matrix & Heatmap** using Seaborn.
- **Pairplots** to explore relationships between features.
- **Boxplots** to detect outliers in `Weight` and `Length`.

### 4. Outlier Detection
- Implemented **IQR method** to detect outliers in `Length` and `Weight`.
- Removed extreme outliers for better model performance.

### 5. Linear Regression Model
- Selected **Length** as independent variable (X).
- Target variable: **Weight** (y).
- Split into train/test (80/20).
- Trained **Linear Regression** model using `sklearn`.

📈 **Model Results:**
- Coefficient: `16.27`  
- Intercept: `-218.23`  
- R² Score: `0.9773` (very high accuracy)

### 6. Visualization of Predictions
- Scatter plot of **actual vs predicted weights**.
- Comparison graph of fish `Length` vs `Weight` (Actual vs Predicted).

---

## 📊 Key Findings
- Strong positive correlation between **Length** and **Weight** (`0.988`).
- Linear Regression is highly effective for predicting fish weight.
- Water quality features (PH, Turbidity, Oxygen) also influence fish health but were not included in the final regression model.

---

## 🛠️ Technologies Used
- **Python**
- **NumPy**
- **Pandas**
- **Matplotlib**
- **Seaborn**
- **Scikit-learn**

---

## 🚀 How to Run
1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/IoTPond-Analysis.git
