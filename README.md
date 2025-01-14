# Stock Price Prediction Using FBProphet

This repository demonstrates step-by-step implementation of predicting stock prices using the FBProphet library. The project uses Tesla's stock data to build a forecasting model and evaluates its performance.

---

## Introduction

The objective of this project is to:
1. Analyze historical stock prices.
2. Build and train a stock price prediction model using FBProphet.
3. Visualize and evaluate the predictions.

---

## Step-by-Step Workflow

## **Methodology**
<img src="https://user-images.githubusercontent.com/7460892/207003643-e03c8964-3f16-4a62-9a2d-b1eec5d8691f.png" width="80%" height="80%">

### **1. Importing Necessary Libraries**
- Imported libraries: `pandas`, `fbprophet`, and `plotly.express`.
- Initialized `plotly.io` for visualizations.

### **2. Importing Dataset from Yahoo Finance**
- Downloaded Tesla stock price dataset from Yahoo Finance.
- Imported the dataset using `pandas`.
- Used `.info()` and `.describe()` to explore the dataset.

### **3. Data Visualization using Plotly**
- Created various visualizations:
- 
  - Area chart of `Close` prices: `px.area(df, x="date", y="Close")`
  - <img src="https://github.com/user-attachments/assets/d959b5b3-b5f9-48d7-9222-0a83df56ed7b" width="50%" height="50%">

  - Box plot of `Close`: `px.box(df, y="Close")`
    <img src="https://github.com/user-attachments/assets/17c0a220-4490-413a-bfe3-42ca96b31ccb" width="50%" height="50%">



### **4. Data Preparation and Preprocessing**
- Selected relevant columns: `date` and `Close`.
- Created a new DataFrame: `columns = ["date", "Close"]` and initialized it.
- Renamed columns for FBProphet:
  - Converted `date` to `ds`.
  - Converted `Close` to `y`.

### **5. Training the Model**
- Initialized the FBProphet model: `m = Prophet()`.
- Trained the model with the prepared DataFrame: `m.fit(prophet_df)`.

### **6. Prediction and Forecasting**
- Created a future DataFrame for 30 days: `future = m.make_future_dataframe(periods=30)`.
- Predicted stock prices: `forecast = m.predict(future)`.
- Visualized predictions:
  - plotting chart: `fig=m.plot(forecast,xlabel="ds",ylabel="y")`
    <img src="https://github.com/user-attachments/assets/98e9daf4-ef77-411d-8640-3149bfd842c8" width="50%" height="50%">
  - Trend and components: `fig = m.plot_components(forecast)`.
    <img src="https://github.com/user-attachments/assets/3ff0913f-0e89-4d69-839c-8c8cc87fbc6c" width="50%" height="50%">


### **7. Forecast Evaluation Using Google Finance**
- Exported forecasted data:
  ```python
  forecast.to_csv('forecast.csv')
  files.download('forecast.csv')
  ```
- In Google Sheets:
  1. Imported actual prices using Google Finance functions (`GOOGLEFINANCE(ticker, "price", start_date, end_date)`).
  2. Aligned actual and predicted prices.
  3. Created graphs to compare actual vs. predicted prices.
      ![Close and yhat](https://github.com/user-attachments/assets/76069d85-92bc-4cf5-9818-fd900ff10082)

  5. Visualized the last 30 days' predictions with data labels.
- Conducted evaluation and documented observations.

---
## **4. Live link**
Link: https://colab.research.google.com/github/tarunkv169/Stock_price_prediction_using_fbprophet/blob/main/Stock_price_prediction_using_fbprophet.ipynb

## Future Scope
- Incorporate additional features like trading volume and economic indicators.
- Fine-tune hyperparameters for improved accuracy.
- Experiment with alternative forecasting models for better comparison.

---

## License

This project is licensed under the MIT License.

---

## Contributing

Contributions are welcome! Fork the repository and submit pull requests with improvements.




