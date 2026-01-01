## Model Comparison: RNN vs. LSTM

### Experimental Setup
- Task: Next-day stock price prediction (regression)
- Models: RNN, LSTM
- Metric: Mean Squared Error (MSE)
- Data & parameters held constant across comparisons
- Variable: Look-back window length

---

### Look-back = 5 Days

| Model | MSE | Notes |
|-----|-----|------|
| RNN  | **1.50** | Best short-term performance |
| LSTM | 1.75 | Slightly worse than RNN |

**Observation**
- RNN achieved lower error with short historical context.
- Suitable for short-term (next-day) prediction.

---

### Look-back = 30 Days

| Model | MSE | Notes |
|-----|-----|------|
| RNN  | 2.80 | Performance degradation |
| LSTM | **2.60** | Slightly more stable |

**Observation**
- Increasing look-back did not improve accuracy.
- LSTM marginally outperformed RNN but overall error increased.

---

### Look-back = 60 Days

| Model | MSE | Notes |
|-----|-----|------|
| RNN  | **2.50** | Moderate degradation |
| LSTM | 4.80 | Severe overfitting |

**Observation**
- LSTM exhibited clear overfitting with long sequences.
- Larger look-back windows introduced noise rather than useful signal.

---

### Summary: RNN vs. LSTM

- RNN:
  - Faster convergence
  - Strong short-term prediction performance
  - Better suited for next-day forecasting
- LSTM:
  - Designed for long-term dependencies
  - Highly sensitive to parameter choices
  - Prone to overfitting in noisy financial data

**Conclusion**
- Increasing model complexity or sequence length does not guarantee better performance.
- Short-term stock prediction benefits from simpler temporal models.

---

## Feature Selection Analysis

### Configurations Tested
- Single feature: Closing price only
- Multiple features: Stock prices + macro indicators (SOX, VIX, oil, gold, USD)

### Findings
- More features ≠ higher accuracy
- High-dimensional feature space increases:
  - Overfitting risk
  - Data sparsity
- For short-term prediction:
  - Closing price alone often produced the lowest error

**Conclusion**
- Feature relevance matters more than feature quantity.
- Simpler feature sets are effective for short-horizon forecasting.

---

## Limitations

- Stock prices are influenced by:
  - Political events
  - Earnings announcements
  - Macroeconomic shocks
- External factors are not fully captured by historical numerical data.
- Long look-back windows may amplify noise.

---

## Future Work

Planned improvements include:
- Alternative architectures:
  - GRU
  - CNN-based sequence models
- Additional features:
  - Technical indicators (RSI, MACD)
  - News and sentiment signals
- Longer prediction horizons
- Hybrid modeling approaches combining:
  - Deep learning
  - Traditional financial analysis

---

## Key Takeaway

Short-term stock prediction favors:
- Simpler models
- Short look-back windows
- Careful feature selection

Deep learning models must be applied cautiously in financial time-series forecasting due to high market uncertainty.

