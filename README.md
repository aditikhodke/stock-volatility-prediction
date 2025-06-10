<h1 align="center">STOCK-VOLATILITY-PREDICTION</h1>

<div align="center">
  <img src="https://img.shields.io/badge/last%20commit-today-brightgreen"/>
  <img src="https://img.shields.io/badge/jupyter%20notebook-100%25-blue"/>
  <img src="https://img.shields.io/badge/languages-1-lightgrey"/>
  <img src="https://img.shields.io/badge/-Markdown-black?logo=markdown"/>
  <img src="https://img.shields.io/badge/-scikitlearn-orange?logo=scikit-learn"/>
  <img src="https://img.shields.io/badge/-NumPy-013243?logo=numpy"/>
  <img src="https://img.shields.io/badge/-pandas-purple?logo=pandas"/>
</div>

---

## 🔍 Overview

**stock-volatility-prediction** is an analytical toolkit designed to forecast stock market volatility by leveraging historical price data and sentiment analysis from news headlines. It provides interactive Jupyter Notebooks for data exploration, feature engineering, model training, and evaluation, aiming to support informed investment and risk management decisions.

---
## Why Use This Toolkit?
Predicting stock volatility is crucial for traders, investors, and risk managers to optimize portfolio strategies and hedge against market uncertainties. This project combines technical analysis, natural language processing, and machine learning to deliver a comprehensive approach to volatility forecasting.

---

## Features

- **Historical Data Integration:** Utilizes daily stock price data from Yahoo Finance, covering multiple years to capture market trends.  
- **Sentiment Analysis:** Incorporates news sentiment scores derived from headlines using TextBlob, providing external market influence signals.  
- **Technical Indicators:** Calculates key technical metrics such as RSI, MACD, and EMA to enrich feature sets.  
- **Modeling Approaches:** Implements multiple models including Linear Regression, Ridge, Lasso, Random Forest, Gradient Boosting, and neural networks (MLP).  
- **Evaluation & Validation:** Uses time series-aware validation strategies and reports metrics like RMSE, MAE, and R².  
- **Visualization:** Generates insightful charts for feature importance, prediction vs actual, and model performance.

---

## Repository Structure
- `AAPL_volitality.ipynb` — Volatility prediction workflow for Apple (AAPL)
- `TSLA_volitality.ipynb` — Volatility prediction workflow for Tesla (TSLA)
- `requirements.txt` — List of required Python packages
- `data/` —> `processed_stock_data.csv` — Example of processed input data
- `.gitignore` — Standard ignores (including `data/`, notebook checkpoints, and virtual environments)
---

## Technical Architecture

### Multimodal Data Pipeline
- **Historical OHLCV Data**: 2-year window from Yahoo Finance  
- **News Sentiment Data**: 30-day rolling window via NewsAPI  

A total of 14 predictive features were generated, including:

- **Exponential Moving Average** (10-day window)
- **MACD** (Moving Average Convergence Divergence, 26/12/9 configuration)
- **RSI** (14-day Relative Strength Index)
- **Lagged Volatility Indicators** (volatility_pct_lag1, rsi_lag1)
- **Sentiment Scores** using TextBlob from financial news headlines
 

### Machine Learning Pipeline
**Model Comparison Framework:**  
- **Baseline**: Linear Regression  
- **Regularized**: RidgeCV, LassoCV  
- **Tree-Based**: Random Forest, Gradient Boosting  
- **Neural**: MLPRegressor (256-128-64 architecture)  

**Validation Strategy:**  
- TimeSeriesSplit (5 splits)  
- Walk-forward validation  
- Strict train-test temporal segregation  

---

## Model Performance & Findings

**Walk-Forward Validation Metrics for TSLA:**

| Model                       | WF_RMSE | WF_MAE | WF_R²  |
|----------------------------|---------|--------|--------|
| MLP Regressor              | 0.8113  | 0.4062 | 0.9235 |
| Baseline Linear Regression | 0.9463  | 0.5136 | 0.8959 |
| RidgeCV                    | 0.9735  | 0.4944 | 0.8912 |

**Walk-Forward Validation Metrics for AAPL:**

| Model                       | WF_RMSE | WF_MAE | WF_R²  |
|----------------------------|---------|--------|--------|
| LassoCV                    | 0.1329  | 0.0809 | 0.9902 |
| RidgeCV                    | 0.1389  | 0.0795 | 0.9893 |
| Baseline Linear Regression | 0.3496  | 0.1355 | 0.9787 |


- **Model effectiveness varied by stock**:
    - MLP Regressor performed best for **TSLA**, likely due to its ability to capture nonlinear behavior in more volatile stocks.
    - Regularized linear models like **LassoCV** and **RidgeCV** outperformed for **AAPL**, suggesting simpler relationships between features and volatility.

---
## Limitations and Challenges

### Data Constraints

- **Temporal Mismatch**: - **Text sentiment scores** from financial news headlines showed **lower predictive power**, likely due to the limited 30-day window compared to 2 years of price data.

- **Market Regime Coverage**: The 2-year window may not capture diverse market regimes (e.g., crashes, booms), which limits model generalizability.
- **Volatility-Specific Challenge**: During high-volatility periods, models showed **10–15% RMSE degradation** compared to stable intervals.

---

## Development Roadmap

### Near-Term Priorities
1. **Real-Time Prediction System**  
   - Streaming data pipeline architecture  
   - Dockerized model serving  

2. **Enhanced Sentiment Integration**  
   - Earnings call transcript analysis  
   - Social media sentiment aggregation  

---

## Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/stock-volatility-prediction.git
   cd stock-volatility-prediction
   ```
2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
3. **Get a NewsAPI key:**
   - Sign up at [NewsAPI](https://newsapi.org/) to obtain a free API key.
   - Open either notebook and paste your API key in the cell marked for `NEWSAPI_KEY`.

---

## Usage

1. **Open a notebook:**
   - Use Jupyter Notebook or JupyterLab to open `AAPL_volitality.ipynb` or `TSLA_volitality.ipynb`.
2. **Configure parameters:**
   - Update the stock ticker (if needed) and date range at the top of the notebook.
   - Paste your NewsAPI key in the designated cell.
3. **Run the workflow:**
   - Execute cells sequentially to:
     - Download historical stock data (via yfinance)
     - Fetch news headlines (via NewsAPI)
     - Calculate technical indicators
     - Perform sentiment analysis (TextBlob)
     - Train and evaluate volatility prediction models
   - Visualizations and processed data will be generated as output.

---

## API

- **NewsAPI** is required for news sentiment analysis.
- You must obtain your own API key and paste it in the notebook cell:
  ```python
  NEWSAPI_KEY = "your_api_key_here"
  ```
- NewsAPI free tier limits queries to the past 30 days.
- All API calls are handled within the notebook; no server setup required.

---

## Contributions

Open to suggestions, improvements, and pull requests! Whether you're fixing a bug or introducing a new feature — you're welcome here.

---

## License
MIT License 