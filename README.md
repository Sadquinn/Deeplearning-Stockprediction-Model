# Stock Price Prediction Using RNN and LSTM (Intel Case Study)

This project investigates the effectiveness of Recurrent Neural Networks (RNN) and Long Short-Term Memory (LSTM) models for short-term stock price prediction using U.S. equity market data, with Intel Corporation (INTC) as a case study.

The study focuses on how sequence length (look-back window), feature dimensionality, and model architecture impact predictive performance in noisy financial time-series data.

---

## Problem Statement

Stock prices exhibit high volatility and non-linearity due to macroeconomic factors, market sentiment, and unexpected events. Traditional statistical models struggle to capture these dynamics.

This project frames stock price prediction as a **supervised regression problem**, predicting the next trading day’s closing price using historical market data.

---

## Data Description

- **Time range**: 2015-01-01 to 2023-11-10
- **Frequency**: Daily
- **Target variable**: Next-day closing price of Intel stock

### Input Features
- Intel stock: Open, High, Low, Close, Volume
- Philadelphia Semiconductor Index (SOX)
- Gold Futures
- Crude Oil Futures
- Volatility Index (VIX)
- U.S. Dollar Index (DXY)

### Data Sources
- Yahoo Finance
- Investing.com

---

## Data Preprocessing

- Time-based data split to prevent information leakage
- Manual separation into:
  - Training set (2015–2021)
  - Validation set (2021–2022)
  - Test set (2023)
- Min-Max normalization applied separately to:
  - Input features
  - Target variable
- Sliding window transformation with configurable look-back periods:
  - 5 days
  - 30 days
  - 60 days

---

## Model Architecture

### RNN
- Three stacked SimpleRNN layers
- Dropout regularization
- Dense output layer
- Optimizer: Adam
- Loss function: Mean Squared Error (MSE)

### LSTM
- Two stacked LSTM layers
- Dropout regularization
- Dense output layer
- Optimizer: Adam
- Loss function: Mean Squared Error (MSE)

---

## Evaluation Metric

- **Mean Squared Error (MSE)**
- Emphasizes larger prediction errors
- Commonly used for regression and time-series forecasting

---

## Key Results

- RNN achieved lower MSE in short look-back configurations
- LSTM showed instability and overfitting with longer sequences
- Increasing input feature dimensionality did not consistently improve accuracy
- Closing price alone often provided competitive predictive power

Detailed experiment results are documented in [`RESULTS.md`](./RESULTS.md).

---

## Repository Structure

