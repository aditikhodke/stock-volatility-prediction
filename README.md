# Stock Market Volatility Prediction using Sentiment Analysis

This project predicts next-day stock volatility using a combination of:
- Historical OHLCV stock data (via yfinance)
- News headlines with sentiment analysis (FinBERT)
- Technical indicators (RSI, MACD, EMA)
- Time-series models (ARIMA, LSTM)

## Features
- Real-time stock data collection using yfinance
- News headline collection using NewsAPI
- Technical analysis indicators calculation
- Sentiment analysis of news headlines
- Volatility prediction models

## Setup
1. Clone the repository:
```bash
git clone https://github.com/yourusername/stock-volatility-prediction.git
cd stock-volatility-prediction
```

2. Install required packages:
```bash
pip install -r requirements.txt
```

3. Set up your API keys:
- Get a NewsAPI key from [NewsAPI](https://newsapi.org/)
- Add your API key to the notebook

## Usage
1. Open `main.ipynb` in Jupyter Notebook
2. Update the stock ticker and date range as needed
3. Run the cells sequentially to:
   - Collect stock data
   - Gather news headlines
   - Calculate technical indicators
   - Perform sentiment analysis
   - Train and evaluate prediction models

## Requirements
- Python 3.9+
- pandas
- numpy
- yfinance
- ta (Technical Analysis library)
- NewsAPI
- Jupyter Notebook

## License
MIT License 