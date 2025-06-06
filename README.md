
# 🏀 Predicting NBA Salary Through Different Models

This project built three different models to predict NBA player salaries for 2025-2026 season based on traditional per-game statistics.
Through these models, the goal is to explore how traditional stats correlate to player compensation and to build a simple and interpretable salary prediction model.

## 🚀 Getting Started

### Prerequisites

- Python 3.8+

### Required Libraries

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- xgboost
- plotly
- torch

### Running

1. Download both folders (data, notebooks)
2. Open any notebook inside notebooks folder (Linear Regression, Random Forest, or Deep Learning)
3. Run it and try putting any name of current NBA player in the end of the notebook, section called 'Prediction Function'


## 📁 Project Structure

```
NBA_Salary_Prediction/
│
├── data/
│   ├── 2022 NBA Team Market Size.csv
│   └── NBA Player Salaries_2000-2025.csv
|   └── NBA Player Salaries_2024-25_1.csv
|   └── NBA Player Stats and Salaries_2000-2025.csv
|   └── NBA Player Stats and Salaries_2010-2025.csv
|   └── NBA Player Stats_1998-2025.csv
|   └── NBA Player Stats_2024-25_Per_Game.csv
│
├── notebooks/
|   ├── NBA Salary Project_DL_Traditional.ipynb
│   └── NBA Salary Project_LR_Traditional.ipynb
│   └── NBA Salary Project_RF_Traditional.ipynb
│
├── NBA Salary Project Data Preparation.ipynb
└── README.md
```

## 🔍 Description & Overview

Three different models were built in this project:
- Linear Regression model (NBA Salary Project_LR_Traditional.ipynb)
- Random Forest model (NBA Salary Project_RF_Traditional.ipynb)
- Deep Learning model (NBA Salary Project_DL_Traditional.ipynb)

Each model used different sets of features from different timeframe and scale of data. All three models try to predict a player's salary for 2025-26 season as accurate as possible through further tuning and adjustments.

## 📊 Datasets Used

- NBA Player Stats_2024-25_Per_Game.csv: Every player's per-game stats for 2024-25 season.
- NBA Player Salaries_2024-25_1.csv: Every player's salary for 2024-25 season.
- 2022 NBA Team Market Size.csv: Includes NBA teams' metro population, TV market size, team revenue from 2022.

**NBA Salary Project Data Preparation.ipynb** includes full scrapping script for below datasets:
- NBA Player Salaries_2000-2025.csv
- NBA Player Stats_1998-2025.csv
- NBA Player Stats and Salaries_2000-2025.csv
- NBA Player Stats and Salaries_2010-2025.csv

## 📏 Evaluation Metrics

- **Root Mean Squared Error (RMSE)** measures the model’s prediction error in dollar terms.
- **R-squared (R²)** explains the proportion of variance in salary that is predictable from the features used.

These two metrics help balance interpretability and accuracy in evaluating model performance.

## 📈 Linear Regression

Linear Regression model only used stats and salary data for 2024-25 season, since LR model can be skewed by some outliers with a larger dataset.
To filter out the features (stats) that will be fed to the model, I did: 
1) dropped stats that showed low correlation with salary
2) and also dropped stats with high [VIF](https://www.investopedia.com/terms/v/variance-inflation-factor.asp) score.
These processes has successfully minimized multicollinearity and overfitting issues, which are very often problematic when building LR models.
As a result of filtering process, I used PTS, AST, REB, STL, BLK, and Age of a player as a set of features.
Finally, testing results were:
- **Root Mean Squared Error (RMSE)**: $9,240,772.81
- **R-squared (R²)**: 0.5261

## 🌳 Random Forest Regression

After building linear regression model, I wanted to improve the accuracy of prediction model. So I tried to compare various non-linear regression models, including **Random Forest**, **Gradient Boost**, **XGBoost**, and **Extra Trees** Regressor. 

Without any tuning and adjustment, Random Forest regressor showed best test result among four. So I chose Random Forest to build a prediction model.

Since Random Forest is less vulnerable to multicollinearity and overfitting issues, I tried four combinations to find best set for prediction:
- Using 2024-25 data and limited features (stats that I used for LR)
- Using 2024-25 data and all features (including every stats on dataset)
- Using 2010-25 data and limited features
- **Using 2010-25 data and all features**

Among these four, using 2010-25 data and all features performed the best. Then I conducted some hyperparameter tuning to further improve performance of the model.

Testing results were:
- **RMSE**: $4,199,705.10
- **R-squared (R²)**: 0.7440

## 🧠 Deep Learning

I lastly built Deep Learning model through **PyTorch**. Since it is DL which requires lots of data, I used 2010 data with all the features, just like my RF model. I trained up to 50 epochs, and testing results were:
- **RMSE**: $4,931,571.61
- **R-squared (R²)**: 0.6501

Obviously testing results vary every time I train it, but R^2 score does not dramatically increase or decrease by more than 0.02.

## ⚖️ Comparing Models

| Model             | RMSE           | R-squared (R²)     |
| ----------------- | -------------- | ------------------ |
| Linear Regression | \$9,240,772.81 | 0.5261             |
| Random Forest     | \$4,199,705.10 | 0.7440             |
| Deep Learning     | \$4,931,571.61 | 0.6501             |

Random Forest model outperforms the others with the lowest RMSE and highest R², indicating strong predictive power and better fit to the data. While Deep Learning also performs well, it slightly underperforms Random Forest in both metrics. However, there is a big room for improvement for enhancing Deep Learning model.

## 📌 Future Work

- Incorporate player popularity metrics (e.g., social media followers)
- Add injury history or availability data
- Include market size and team success as additional features (already collected)
- Improve Deep Learning model with more epochs, regularization, or advanced architectures (e.g., dropout, batch normalization)
- Deploy as a simple web app to input stats and predict salary

## 🙌 Acknowledgments

- [Basketball Reference](https://www.basketball-reference.com/)
- [HoopsHype](https://hoopshype.com/salaries/)
- [HoopSocial](https://hoop-social.com/nba-team-market-size-rankings/)
- [Statista](https://www.statista.com/)
- [Koki Ando](https://www.kaggle.com/koki25ando)

