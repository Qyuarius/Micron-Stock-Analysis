# Stock Price Prediction

Proyek prediksi harga saham menggunakan **Machine Learning** dengan pendekatan **technical analysis**. Memprediksi pergerakan harga saham dalam jangka waktu **1 bulan** dan **1 tahun** ke depan menggunakan ensemble dari 5 model regresi.

## Dataset

Data harga saham diambil dari **Yahoo Finance** (`yfinance`) secara real-time. Secara default menggunakan ticker **MU** (Micron Technology).

## Fitur Teknikal

30+ fitur teknikal yang digunakan:

- **Moving Averages**: SMA 10, 20, 50, 200
- **Momentum**: RSI, MACD, MACD Signal, MACD Histogram
- **Volatility**: Bollinger Bands (Upper, Lower, Width), ATR
- **Trend Strength**: ADX, DMP, DMN
- **Volume**: Volume Ratio (vs SMA 20)
- **Lag Features**: Close & Volume lag (1-5 for 1-month, 1-21 for 1-year)
- **Derived**: Rate of Change (5, 10, 21, 63 day), Volatility (10, 21 day)

## Model

| Model | Deskripsi |
|---|---|
| **Linear Regression** | Baseline linier |
| **Random Forest** | 100-200 trees, max_depth 6-8 |
| **Gradient Boosting** | 100-200 estimators, learning_rate 0.03-0.05 |
| **SVR (RBF)** | Support Vector Regression kernel RBF |
| **Huber Regressor** | Robust terhadap outliers |

Prediksi akhir menggunakan **Ensemble Mean** dari kelima model.

## Struktur Proyek

```
├── Predict_1Month.py         # Prediksi 21 hari ke depan
├── Predict_1Year.py          # Prediksi 252 hari ke depan
├── Stock_Price_Prediction_Week.ipynb   # Notebook 1-month
├── Technical_Patterns.ipynb            # Notebook pattern recognition
└── README.md
```

## Cara Penggunaan

```bash
pip install -r requirements.txt
python Predict_1Month.py   # Prediksi 1 bulan
python Predict_1Year.py    # Prediksi 1 tahun
```

## Output

- Tabel harga prediksi harian dari masing-masing model + ensemble
- Grafik perbandingan seluruh model dengan confidence band (min-max ensemble)
- Metrik evaluasi: MAE, RMSE, Directional Accuracy, MAPE

## Dependencies

`yfinance`, `pandas`, `numpy`, `pandas_ta`, `matplotlib`, `scikit-learn`, `mplfinance`
