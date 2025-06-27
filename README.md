# LSTM-Stock-Predictor
Final Project for AI class

# LSTM-Based Stock Price Prediction for Pharma & Biotech Sectors

## 📈 Overview

This project was completed as the final assignment for **CS311: Artificial Intelligence** at Middlebury College. We developed a deep learning framework using **Long Short-Term Memory (LSTM)** networks to forecast stock prices in the **pharmaceutical and biotechnology sectors**. Our primary goal was to assess whether LSTM-based models could identify temporal patterns in financial time series and provide accurate short-term predictions.

---

## 🧠 Model Architecture

We implemented a multi-layer LSTM model with the following structure:

- **Input Shape**: `sequence_length x num_features`
- **Layers**:
  - LSTM (128 units, return sequences)
  - Dropout (0.2)
  - LSTM (64 units)
  - Dense (32 units, ReLU)
  - Dense (1 unit) → Predicts next-day price
- **Loss Function**: Mean Squared Error (MSE)
- **Optimizer**: Adam
- **Metrics**: MSE, RMSE, MAE

We trained the model using a sliding window approach to generate input sequences from historical stock data.

---

## 🧪 Data

We trained on **five years of daily stock data** (2020–2024) from **150 companies** in the **pharmaceutical and biotech sectors**, sourced via the **Alpha Vantage API**.  

Each data sequence included:
- Adjusted close prices
- Technical indicators (SMA, EMA, RSI, MACD)
- Daily returns and log-volatility

### Sample Companies
**Biotech**: Moderna (MRNA), Amgen (AMGN), BioNTech (BNTX), Gilead Sciences (GILD)  
**Pharma**: Pfizer (PFE), Merck (MRK), Johnson & Johnson (JNJ), Bristol-Myers Squibb (BMY)

---

## 🔮 Forecasting Results

We evaluated model performance by forecasting **1 week (5 trading days)** into the future after the end of the training window.

- **Short-term (1-week) forecasts** were consistently accurate across most stocks, with low RMSE and well-aligned trend direction.
- **Beyond 1 week**, prediction accuracy **declined significantly**, likely due to compounding volatility, limited input context, and the absence of macroeconomic news events.

This finding aligns with financial theory: short-term trends can be somewhat learned from past patterns, while longer-term movements are increasingly driven by exogenous events.
