# Time series modeling

# Presiqutes

* Python 3.9+
* Pip 

It recomends to create a virtual environment to run the notebook

```shell
python -m venv .venv
source .venv/bin/activate
jupyter lab
```

# Data

The data file `input/data.csv` has been consolidated from several files, as explained in detail in the notebook [0_make_data.ipynb](0_make_data.ipynb). This dataset consists of a time series of purchase and redemption amounts for a financial product spanning approximately 14 months.

In addition to these core financial data, the dataset also includes various supplemental information, as summarized in the table below.

In this repository, our primary focus is on predicting the `total_purchase_amt` variable, which serves as the target of interest for our analysis.

**Attribute**|**Type**|**Description**|**Example**
:-----:|:-----:|:-----:|:-----:
total\_purchase\_amt|double|Today total purchase = direct purchase + revenue|21876
total\_redeem\_amt|double|Today's total redemption amount = consumption + transfer amount|10261
mfd\_daily\_yield|double|Revenue per 1000,000 fen|1.5787
mfd\_7daily\_yield|double|7-DayAnnualizedYield (%)|6.307
Interest \_ O\_N|double|Overnight SHIBOR (%)|2.8
Interest \_ 1\_W|double|1-week SHIBOR (%)|4.25
Interest \_ 2\_W|double|2-week SHIBOR (%)|4.9
Interest \_ 1\_M|double|1-monthSHIBOR (%)|5.04
Interest \_ 3\_M|double|3-monthSHIBOR (%)|4.91
Interest \_ 6\_M|double|6-monthSHIBOR (%)|4.79
Interest \_ 9\_M|double|9-monthSHIBOR (%)|4.76
Interest \_ 1\_Y|double|1-YearSHIBOR (%)|4.78


# Models
The models in demostration are:
* ARIMA
* prophet
* xgboost
* lstm

### ARIMA (AutoRegressive Integrated Moving Average)

ARIMA is a widely used time series forecasting method. It stands for AutoRegressive Integrated Moving Average. ARIMA models capture time-dependent patterns and trends in data. It has three key components:

- AutoRegressive (AR): This accounts for the linear relationship between the current observation and previous observations, indicating how past values influence future values.
- Integrated (I): The 'I' denotes differencing to make the time series stationary, which helps remove trends and seasonality.
- Moving Average (MA): This accounts for the relationship between the current observation and a weighted average of past prediction errors.

ARIMA models are effective for capturing **linear relationships** and are suitable for data with known temporal structures.

### Prophet

Prophet is a forecasting model developed by Facebook. It is designed to handle time series data that may have missing values, outliers, and irregular patterns. Prophet decomposes time series data into three components: **trend**, **seasonality**, and **holidays**. It uses a customizable additive model to capture these components and provides a reliable way to forecast time series data, even when the patterns are complex or unpredictable.

Prophet is user-friendly and requires minimal parameter tuning, making it a popular choice for business and financial time series forecasting.

### XGBoost

XGBoost is a machine learning algorithm that can be applied to time series forecasting by treating it as a supervised learning problem. It is a gradient boosting algorithm that builds an ensemble of decision trees. To use XGBoost for time series forecasting, you need to **transform your time series data into a supervised learning format**, considering time lags as features.

XGBoost is known for its flexibility and high performance. It can capture complex patterns and relationships in time series data and is often used when more advanced models are needed.

### LSTM (Long Short-Term Memory)

LSTM is a type of recurrent neural network (RNN) that excels at handling sequential data, making it suitable for time series prediction. LSTMs can capture long-term dependencies and learn intricate temporal patterns within the data.

LSTMs consist of memory cells, which can store information over long sequences, and gates that control the flow of information. These features make LSTMs particularly effective for time series forecasting, especially when dealing with complex and non-linear relationships in the data.

LSTMs require more data and parameter tuning compared to the previous models but can provide powerful results for challenging time series forecasting tasks.


# Caveats and Remarks

In the context of our analysis, it's important to consider the following caveats and remarks:

1. The notebooks provided here may not be finely tuned for the models, which means that the results obtained do not necessarily establish one model as superior to another. While they serve as a valuable starting point, further optimization may be required to achieve more conclusive findings.

2. It is worth noting that some models may require less fine-tuning to yield reasonably good results, making them attractive choices when time or resources are limited.

3. When working with time series models, it is imperative to avoid the leakage of future information. To maintain the integrity of your analysis:

   - When filling missing values, always apply the fill-forward method to ensure that no information from the future is incorporated into the data.
   - When splitting the test dataset, ensure that you use the most recent data points to reflect real-world forecasting scenarios accurately.
   - When creating features, consider using lagged features to capture past patterns and dependencies in the time series data.

These considerations are essential for conducting sound and reliable time series analysis.




