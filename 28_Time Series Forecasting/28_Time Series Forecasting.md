[<< Day 27](../27_Natural%20Language%20Processing%20(NLP)/27_Natural%20Language%20Processing%20(NLP).md) | [Day 29 >>](../29_Working%20with%20Big%20Data/29_Working%20with%20Big%20Data.md)


# 📅 Day 28: Time Series Forecasting ⏳📊

Welcome to **Day 28** of the **30 Days of Data Science** series! 🎉 Today, we will explore **Time Series Forecasting**, one of the most critical techniques in data science used for analyzing sequential data over time. We'll cover key concepts and popular models like **ARIMA** and **Prophet**. By the end of this lesson, you’ll have the tools to forecast future trends and patterns effectively.



## 🌟 Table of Contents
- [📚 Introduction to Time Series Forecasting](#-introduction-to-time-series-forecasting)
- [📈 Understanding Time Series Data](#-understanding-time-series-data)
  - [Components of Time Series](#components-of-time-series)
- [🔮 ARIMA (AutoRegressive Integrated Moving Average)](#-arima-autoregressive-integrated-moving-average)
  - [Steps for ARIMA Modeling](#steps-for-arima-modeling)
  - [Python Example of ARIMA](#python-example-of-arima)
- [📜 Seasonal Decomposition of Time Series (STL)](#-seasonal-decomposition-of-time-series-stl)
- [📦 SARIMA (Seasonal ARIMA)](#-sarima-seasonal-arima)
- [🌍 Prophet: Time Series Forecasting Made Easy](#-prophet-time-series-forecasting-made-easy)
  - [Features of Prophet](#features-of-prophet)
  - [Python Example of Prophet](#python-example-of-prophet)
- [🧠 LSTM (Long Short-Term Memory Networks)](#-lstm-long-short-term-memory-networks)
- [✍️ Practice Exercise](#%EF%B8%8F-practice-exercise)
- [📝 Summary](#-summary)



## 📚 Introduction to Time Series Forecasting

Time series forecasting predicts future values based on previously observed data. It is widely used in areas like:
- **Finance**: Stock price prediction 📈
- **Weather Forecasting**: Temperature and rainfall prediction 🌧️
- **Retail**: Sales forecasting 🛒

Forecasting allows businesses and researchers to plan effectively and make informed decisions.



## 📈 Understanding Time Series Data

A **time series** is a sequence of data points collected or recorded at regular time intervals.

### Components of Time Series
1. **Trend**: Overall upward or downward movement over time.
2. **Seasonality**: Regular patterns that repeat over a fixed period.
3. **Cyclic Patterns**: Long-term fluctuations not tied to seasonality.
4. **Noise**: Random variations or outliers in data.

### Example: Time Series Plot
```python
import pandas as pd
import matplotlib.pyplot as plt

# Sample data
data = {
    'Date': pd.date_range(start='2023-01-01', periods=12, freq='M'),
    'Sales': [200, 220, 250, 270, 300, 350, 400, 420, 450, 470, 500, 550]
}
df = pd.DataFrame(data)

# Plot
plt.plot(df['Date'], df['Sales'], marker='o', linestyle='-')
plt.title("Monthly Sales Data")
plt.xlabel("Date")
plt.ylabel("Sales")
plt.grid()
plt.show()
```



## 🔮 ARIMA (AutoRegressive Integrated Moving Average)

### What is ARIMA?
ARIMA is a statistical modeling technique for analyzing and forecasting time series data. It combines three components:
- **AR (AutoRegressive)**: Uses past values.
- **I (Integrated)**: Differencing the data to make it stationary.
- **MA (Moving Average)**: Uses past forecast errors.

### Steps for ARIMA Modeling
1. **Visualize the Data**: Plot the series and check for trends, seasonality, and stationarity.
2. **Stationarity Test**: Use tests like the Augmented Dickey-Fuller (ADF) test.
3. **Differencing**: Transform non-stationary data to stationary.
4. **Parameter Selection**: Use `p`, `d`, `q` to define the ARIMA model.
5. **Model Training**: Fit the ARIMA model to your data.
6. **Forecasting**: Predict future values.

### Python Example of ARIMA
```python
from statsmodels.tsa.arima.model import ARIMA
import pandas as pd
import matplotlib.pyplot as plt

# Example data
data = [112, 118, 132, 129, 121, 135, 148, 145, 140, 155, 164, 170]
df = pd.DataFrame(data, columns=['Sales'])

# Fit ARIMA model
model = ARIMA(df['Sales'], order=(1, 1, 1))
model_fit = model.fit()

# Summary of the model
print(model_fit.summary())

# Forecast future values
forecast = model_fit.forecast(steps=5)
print("Forecasted Values:", forecast)
```


## 📜 Seasonal Decomposition of Time Series (STL)

Seasonal Decomposition of Time Series (STL) splits the data into **trend**, **seasonal**, and **residual** components.

### Example: STL Decomposition

```python
from statsmodels.tsa.seasonal import STL
import pandas as pd
import matplotlib.pyplot as plt

# Sample time series data
data = [112, 118, 132, 129, 121, 135, 148, 136, 119, 104, 118, 115]
df = pd.DataFrame(data, columns=['value'])

# STL decomposition
stl = STL(df['value'], period=12)
result = stl.fit()

# Plot components
result.plot()
plt.show()
```



## 📦 SARIMA (Seasonal ARIMA)

**SARIMA** extends ARIMA by incorporating seasonality.

The model is defined by parameters `(p, d, q) x (P, D, Q, s)` where:
- `(p, d, q)` are ARIMA parameters.
- `(P, D, Q, s)` are seasonal parameters.

### Example: SARIMA

```python
from statsmodels.tsa.statespace.sarimax import SARIMAX

# Fit SARIMA model
model = SARIMAX(df['value'], order=(1, 1, 1), seasonal_order=(1, 1, 1, 12))
sarima_result = model.fit()

# Forecast
forecast = sarima_result.forecast(steps=5)
print("SARIMA Forecast:", forecast)
```



## 🌍 Prophet: Time Series Forecasting Made Easy

### What is Prophet?
Prophet is an open-source library developed by Facebook for time series forecasting. It is highly flexible, easy to use, and handles missing data, holidays, and seasonal patterns effectively.

### Features of Prophet
- Handles **seasonality** and **holiday effects**.
- Robust to **missing data**.
- Requires minimal tuning.

### Python Example of Prophet
```python
from prophet import Prophet
import pandas as pd
import matplotlib.pyplot as plt

# Create example data
data = {
    'ds': pd.date_range(start='2023-01-01', periods=12, freq='M'),
    'y': [200, 220, 250, 270, 300, 350, 400, 420, 450, 470, 500, 550]
}
df = pd.DataFrame(data)

# Fit Prophet model
model = Prophet()
model.fit(df)

# Create future dataframe
future = model.make_future_dataframe(periods=6, freq='M')

# Forecast
forecast = model.predict(future)

# Plot results
fig = model.plot(forecast)
plt.show()
```


## 🧠 LSTM (Long Short-Term Memory Networks)

LSTMs are a type of **recurrent neural network (RNN)** capable of learning long-term dependencies.

### Example: LSTM Model

```python
import numpy as np
from keras.models import Sequential
from keras.layers import LSTM, Dense

# Sample data
data = np.array([112, 118, 132, 129, 121, 135, 148, 136, 119, 104, 118, 115])
X = data[:-1].reshape((1, len(data)-1, 1))  # Features
y = data[1:]  # Labels

# Define LSTM model
model = Sequential()
model.add(LSTM(50, activation='relu', input_shape=(X.shape[1], 1)))
model.add(Dense(1))
model.compile(optimizer='adam', loss='mse')

# Train
model.fit(X, y, epochs=200, verbose=0)

# Forecast
forecast = model.predict(X)
print("LSTM Forecast:", forecast)
```



## ✍️ Practice Exercise

Try the following:
1. Load a **time series dataset** of your choice (e.g., stock prices, weather data).
2. Preprocess the data to handle missing values.
3. Train an **ARIMA** model and forecast future values.
4. Compare the performance of **ARIMA** and **Prophet** on the same dataset.



## 📝 Summary

In this lesson, we covered the fundamentals of **Time Series Forecasting**, explored **ARIMA**, and demonstrated the use of **Prophet** for efficient predictions. Forecasting is a powerful tool for uncovering trends and patterns in sequential data. Mastering these techniques will empower you to tackle real-world problems in diverse domains.

---



