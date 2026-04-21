# Traffic Volume Forecasting using Stacked LSTM Networks

## Overview
This project implements a deep learning-based traffic forecasting system using Stacked Long Short-Term Memory (LSTM) networks to predict hourly traffic volumes at urban road junctions.

The system is designed for Intelligent Transportation Systems (ITS) to enable proactive congestion management, adaptive signal control, and improved urban mobility.

Based on research: Deep Learning-Based Hourly Traffic Volume Forecasting Using Stacked LSTM Networks

---

## Key Features
- Hourly traffic prediction using deep learning
- Stacked LSTM architecture (2 layers)
- Time-series forecasting with 24-hour lookback
- 24-hour rolling forecast capability
- Multi-junction evaluation (4 different road types)
- Advanced feature engineering (30 features)
- Suitable for real-time ITS deployment

---

## Dataset
- Total observations: 48,120 hourly records
- Junctions: 4 urban road intersections
- Data fields:
  - Timestamp
  - Junction ID
  - Vehicle count

### Junction Characteristics
| Junction | Type | Avg Volume | Max |
|----------|------|-----------|-----|
| J1 | High-volume arterial | 45.1 | 156 |
| J2 | Medium | 14.3 | 48 |
| J3 | Medium (irregular) | 13.7 | 180 |
| J4 | Low-volume | 7.3 | 36 |

---

## System Pipeline
Raw Data → Feature Engineering → Normalization → Sequence Creation → Train/Test Split → LSTM Model → Predictions

---

## Feature Engineering
30 features including:
- Time-based features (hour, day, month, etc.)
- Cyclical encoding (sin/cos)
- Lag features (1–168 hours)
- Rolling statistics (mean, std, min, max)

---

## Model Architecture
Input (24 × 30)
→ LSTM (128)
→ Dropout + BatchNorm
→ LSTM (64)
→ Dropout + BatchNorm
→ Dense (32)
→ Output (1)

---

## Training Configuration
- Optimizer: Adam
- Learning rate: 0.001
- Loss: MSE
- Batch size: 64
- Epochs: 80 (with early stopping)

---

## Performance Results
| Junction | MAE | RMSE | R² |
|----------|-----|------|----|
| J1 | 7.21 | 9.68 | 0.82 |
| J2 | 3.04 | 4.12 | 0.77 |
| J3 | 4.28 | 6.71 | 0.51 |
| J4 | 2.82 | 3.95 | 0.16 |

---

## Rolling Forecast
Supports 24-hour ahead prediction using recursive forecasting.

---

## Applications
- Smart traffic control
- Congestion prediction
- Urban planning
- Smart cities

---

## Limitations
- No external data (weather/events)
- Lower accuracy on irregular traffic
- No spatial modeling

---

## Future Work
- Add weather data
- Use Graph Neural Networks
- Extend to multi-junction systems

---


## Authors
- Abidul Islam Alif


---

## License
Academic use only.
