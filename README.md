
# 🏀 NBA Salary Prediction (2024–25)

This project uses linear regression to predict NBA player salaries for the 2024–25 season based on per-game performance statistics. 
The goal is to explore how different basketball metrics relate to player compensation and to build a simple but interpretable salary prediction model.

## 📁 Project Structure

```
NBA_Salary_Prediction/
│
├── data/
│   ├── NBA Player Salaries_2024-25_1.csv
│   └── NBA Player Stats_2024-25_Per_Game.csv
│
├── notebooks/
│   └── NBA_Salary_Prediction.ipynb
│
├── README.md
└── requirements.txt (optional)
```

## 📊 Dataset Sources

- **Salary Data**: NBA player salaries for the 2024–25 season.
- **Stats Data**: Per-game statistics for each player from the same season.

> Note: Players who played for multiple teams were consolidated using their "total" row (e.g., `2TM`, `3TM`).

## 🔍 Key Steps & Methodology

### 1. Data Cleaning
- Removed duplicate rows and missing values.
- Normalized player names and dropped unnecessary columns like `Rk`.
- Consolidated multi-team players into a single row per player.

### 2. Feature Selection
Features were selected based on:
- **Correlation analysis** with salary
- **Multicollinearity checks** (to reduce redundant or dependent variables)
- **Interpretability** and real-world basketball context

Final features for modeling:
```
PTS, MP, TOV, AST, TRB, STL, Age
```

### 3. Regression Modeling
- Used **Linear Regression** with standardized features.
- Split data into training and test sets (80/20 split).
- Evaluated with R², RMSE, and coefficient interpretation.

### 4. Model Insights
- Some surprising results emerged (e.g. negative coefficients for PTS in early models), which led to iterative refinement.
- Efficiency stats like FG% and 3P% were excluded due to their weak or misleading correlations with salary.

### 5. Prediction Function
Created a reusable function to predict a player's salary and compare it to their actual 2024–25 contract.

### 6. Sample Predictions
Tested model on players with expiring contracts:
```
- James Harden
- LeBron James
- Clint Capela
- Chris Paul
- Ty Jerome
- Jaxson Hayes
```

## 📈 Results
**Initial Model Performance:**
- Mean Squared Error (MSE): 74,323,038,271,342.59
- Root Mean Squared Error (RMSE): 8,621,081.04
- R-squared (R²): 0.5529

These values suggest the model captures general trends, but misses some context like player market value, team fit, or injury history — things that stats alone can't explain.

## 📌 Future Improvements
- Add contract metadata: years, clauses, incentives
- Incorporate advanced stats (e.g. RAPTOR, BPM, EPM, PER...)
- Use position/team as categorical variables (e.g. Big/Small Market...)
