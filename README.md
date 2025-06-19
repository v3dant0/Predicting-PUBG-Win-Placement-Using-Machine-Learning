# 🏆 Predicting PUBG Win Placement Using Machine Learning
![.](media/giphy.gif)

## 📋 Project Overview

This project performs comprehensive data analysis on PlayerUnknown's Battlegrounds (PUBG) game data to extract meaningful insights about player performance, game dynamics, and winning strategies. The analysis includes exploratory data analysis, statistical modeling, and machine learning techniques to understand factors that contribute to success in PUBG matches. Using advanced regression models, particularly CatBoost, the project aims to predict player placement percentiles based on various in-game metrics.

## 🎮 Game Background

PUBG is a player-versus-player battle royale game where up to 100 players fight to be the last person or team standing. Players parachute onto a map, search for weapons and equipment, and engage in combat while the playable area continuously shrinks, forcing confrontations. The game offers different modes, including solo, duo, and squad play, across various maps with different terrain features.

## 🎯 Project Objectives

- Analyse player performance metrics and game statistics to identify winning patterns
- Clean and preprocess raw PUBG game data to remove outliers and anomalies
- Identify key factors that influence match outcomes through feature importance analysis
- Build predictive models for player performance and placement
- Compare different machine learning algorithms for prediction accuracy
- Provide actionable insights for improving gameplay strategy

## 📊 Dataset Description
Dataset link : https://www.kaggle.com/datasets/ashishjangra27/pubg-games-dataset?select=PUBG_Game_Prediction_data.csv
The dataset contains PUBG match data with various features, including:

- **Player Performance Metrics**: Kills, damage dealt, distance travelled, healing items used
- **Match Information**: Match duration, game mode, map details
- **Survival Metrics**: Time survived, placement rankings
- **Combat Statistics**: Weapons acquired, kill streaks, headshot percentages
- **Movement Data**: Walking distance, riding distance, swimming distance

## 🧹 Data Cleaning and Preprocessing

The data cleaning process involved several steps to ensure data quality:

1. **Handling Missing Values**: Identified and dropped rows with missing win placement percentiles
2. **Removing Outliers**:
   - Removed players with kills but zero movement (potential cheaters)
   - Filtered out players with unrealistic road kills (>5)
   - Removed players with excessive kills (>25)
   - Eliminated suspicious headshot rates (>0.8 with >5 kills)
   - Removed unrealistic long-distance kills (≥600m)
   - Filtered out players with excessive weapons acquired (≥15)
3. **Feature Engineering**:
   - Created total distance feature (sum of walk, ride, and swim distances)
   - Normalised features affected by the number of players in a match
   - Combined healing and boost items into a single feature
   - Created headshot rate feature (headshot kills / total kills)

## 🛠️ Technologies Used

- **Python 3.x**: Primary programming language
- **Data Analysis Libraries**:
  - `pandas`: Data manipulation and analysis
  - `numpy`: Numerical computations
  - `matplotlib` & `seaborn`: Data visualisation
- **Machine Learning**:
  - `scikit-learn`: Data preprocessing, model evaluation, and traditional ML algorithms
  - `catboost`: Gradient boosting implementation for regression tasks
- **Development Environment**:
  - Jupyter Notebook: Interactive code development and visualisation

## 📊 Exploratory Data Analysis

### Player Distribution Analysis

The analysis began by examining the distribution of players in matches, focusing on games with at least 75 players to ensure competitive environments. This helped understand the typical match size and its impact on gameplay dynamics.

### Combat Performance Analysis

The distribution of kills showed that most players achieve 0-1 kills per match, with a long tail distribution indicating that few players achieve high kill counts. This reflects the challenging nature of PUBG's combat system, where survival often takes precedence over aggressive play.

### Movement and Survival Analysis

Analysis of player movement patterns revealed strong correlations between distance travelled and survival time. Players who balance movement between walking and vehicle usage tend to perform better than those who remain stationary or move excessively.

### Weapon Efficiency Analysis

The project examined weapon acquisition patterns and their relationship with match performance. The data showed that while having more weapons correlates with better placement, there's an optimal range beyond which additional weapons don't improve outcomes.

## 🔍 Feature Importance Analysis

Feature importance analysis revealed the most significant predictors of match placement:

1. **Kill Place**: A player's ranking based on kills (41.56%)
2. **Total Distance**: Combined movement distance (23.94%)
3. **Normalised Kills**: Kills adjusted for match size (8.55%)
4. **Kill Streaks**: Maximum consecutive kills (6.22%)
5. **Match Duration**: Time survived normalised (5.35%)

This analysis demonstrates that both combat effectiveness and survival strategy significantly impact match outcomes. The high importance of kill place suggests that eliminating opponents efficiently is crucial for success, while movement (total distance) indicates that strategic positioning is equally important.

## 🤖 Machine Learning Models

### CatBoost Regression Model

The primary model used was CatBoost Regression, a gradient boosting algorithm that handles categorical features effectively. The model was configured with:

- Loss function: RMSE (Root Mean Squared Error)
- Learning rate: Optimized through grid search
- Depth: Tested values of 2, 4, 6, and 8
- Iterations: Tested values of 100 and 150

### Model Performance

The CatBoost model achieved impressive performance metrics:

- **R² Score**: 0.9227 (indicating the model explains 92.27% of the variance in placement)
- **RMSE**: 0.0073 (showing very low prediction error)

### Comparative Model Analysis

Additional models were tested to benchmark performance:

| Model | RMSE | R² Score |
|-------|------|----------|
| CatBoost Regressor | 0.0073 | 0.9227 |
| Gradient Boosting Regressor | 0.0071 | 0.9252 |
| Random Forest Regressor | 0.0111 | 0.8832 |
| Linear Regression | 0.0187 | 0.8020 |

The Gradient Boosting Regressor slightly outperformed CatBoost in both metrics, while Random Forest and Linear Regression showed good but inferior performance. This comparison demonstrates the effectiveness of ensemble boosting methods for this prediction task.

## 🔬 Feature Selection and Optimization

After identifying the most important features, the model was retrained with a reduced feature set, dropping features with importance less than 0.1. This optimization:

1. Reduced model complexity without sacrificing performance
2. Improved training speed by focusing on relevant features
3. Enhanced model interpretability by eliminating noise

The optimized model maintained similar performance metrics (R² = 0.9227, RMSE = 0.0073), demonstrating effective feature selection.

## 🎮 Key Insights and Findings

1. **Combat Effectiveness**: Players with higher kill counts and better kill rankings show significantly better placement, confirming the importance of combat skills
2. **Strategic Movement**: Total distance traveled is the second most important factor, indicating that strategic positioning and map awareness are crucial
3. **Kill Efficiency**: Kill streaks have higher importance than raw kill count, suggesting that efficient combat engagement is more valuable than simply accumulating kills
4. **Survival Balance**: The optimal strategy combines aggressive play (kills) with smart movement and positioning
5. **Equipment Management**: Weapon acquisition shows moderate importance, indicating that having the right tools matters, but less than how they're used

## 📝 Conclusion

This PUBG data analysis project successfully identified key factors that influence player performance and match outcomes. The high R² scores across multiple models demonstrate that player placement can be accurately predicted from in-game metrics. The findings provide valuable insights for players looking to improve their gameplay strategy, emphasizing the importance of balanced combat effectiveness and strategic movement.

The project showcases the power of machine learning in understanding complex game dynamics and player behavior patterns. By leveraging gradient boosting algorithms and careful feature engineering, we've created a robust predictive model that captures the essence of successful PUBG gameplay.

