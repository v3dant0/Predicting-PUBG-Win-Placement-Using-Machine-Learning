# 🏆 Predicting PUBG Win Placement Using Machine Learning
![.](media/giphy.gif)



## 📌 Objective

To build a regression model that accurately predicts a player’s **normalized finishing position** (from 0 to 1) using combat, survival, and movement data collected in PUBG matches.

---

## 📁 Dataset

- **File:** `pubg.csv`
- **Source:** Kaggle / PUBG game logs
- **Target:** `winPlacePerc` — normalized player rank (0 = last place, 1 = winner)
- **Features include:**
  - Combat: `kills`, `damageDealt`, `headshotKills`, `weaponsAcquired`
  - Survival: `heals`, `boosts`, `revives`
  - Movement: `walkDistance`, `rideDistance`, `swimDistance`
  - Misc: `matchId`, `groupId`, `Id`

---

## 🧹 Data Preprocessing & Cleaning

### ✅ Key Steps:
- Removed rows with missing values in `winPlacePerc`
- Filtered out matches with fewer than 75 players
- Removed **suspicious/outlier behaviors**:
  - Players with kills but **zero movement**
  - **Road kills > 5**
  - **Kills > 25**
  - **Headshot rate > 80%** with more than 5 kills
  - **Longest kill distance ≥ 600m**
  - **Weapons acquired ≥ 15**

---

## 🔧 Feature Engineering

- `totalDistance` = sum of `walkDistance`, `rideDistance`, `swimDistance`
- `headshotRate` = `headshotKills` / `kills`
- Dropped less informative or highly correlated features

---

## 📊 Exploratory Data Analysis (EDA)

- Visualized distributions of:
  - Kills, headshot rates, distances, weapons
- Count plots to identify anomalies
- Correlation heatmap to check multicollinearity

---

## 🤖 Modeling

### 🔥 Best Model: **CatBoost Regressor (Gradient Boosting)**

CatBoost was chosen for its performance on structured data, minimal preprocessing needs, and ability to handle categorical features internally.

### 🧪 Model Training:

- Dataset split: **80% training / 20% test**
- Standardized numerical features
- Used default parameters for CatBoost (no tuning)

### 📉 Evaluation Metrics:

| Metric      | Value     |
|-------------|-----------|
| R² Score    | **0.88**  |
| RMSE        | **0.04**  |

*These values indicate that the model explains 88% of the variance in placement and makes predictions with low average error.*

---

## ✅ Summary of Results

- Cleaned and preprocessed over 400,000 PUBG player records
- Conducted deep EDA to engineer features and reduce noise
- Achieved high performance with **CatBoost Regressor**
- Demonstrated the importance of domain-specific feature filtering

---

## 🚀 Future Improvements

- Hyperparameter tuning (GridSearchCV or Optuna)
- Ensemble stacking with LightGBM or XGBoost
- Deploying model with a Flask or Streamlit frontend

---

## 📂 Project Structure


