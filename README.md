# ARIMA_And_Seasonal-ARIMA

https://medium.com/analytics-vidhya/time-series-forecasting-and-analysis-arima-and-seasonal-arima-cacaf61ae863

Time series is different from more traditional classification and regression predictive modeling problems.

The temporal nature adds an order to the observations. This imposed order means that important assumptions about the consistency of those observations needs to be handled specifically.

The ability to make predictions based upon historical observations creates a competitive advantage. For example, if an organization has the capacity to better forecast the sales quantities of a product, it will be in a more favourable position to optimize inventory levels. This can result in an increased liquidity of the organizations cash reserves, decrease of working capital and improved customer satisfaction by decreasing the backlog of orders.

In the domain of machine learning, there’s a specific collection of methods and techniques particularly well suited for predicting the value of a dependent variable according to time. In the proceeding article, we’ll cover AutoRegressive Integrated Moving Average (ARIMA).

We refer to a series of data points indexed (or graphed) in time order as a time series. A time series can be broken down into 3 components.


Trend: Upward & downward movement of the data with time over a large period of time (i.e. house appreciation)
Seasonality: Seasonal variance (i.e. an increase in demand for ice cream during summer)
Noise: Spikes & troughs at random intervals.
Types of Time Series:
Stationary Time Series :
The observations in a stationary time series are not dependent on time.
Time series are stationary if they do not have trend or seasonal effects. Summary statistics calculated on the time series are consistent over time, like the mean or the variance of the observations.
When a time series is stationary, it can be easier to model. Statistical modeling methods assume or require the time series to be stationary to be effective.

Stationary Time Series
Non-Stationary Time Series:
Observations from a non-stationary time series show seasonal effects, trends, and other structures that depend on the time index.
Summary statistics like the mean and variance do change over time, providing a drift in the concepts a model may try to capture.
Classical time series analysis and forecasting methods are concerned with making non-stationary time series data stationary by identifying and removing trends and removing seasonal effects.

Non-Stationary Time Series
Before applying any statistical model on a time series, we want to ensure it’s stationary.

For a time series to be stationary it has to satisfy the below conditions:
The mean of the series should not be a function of time. The red graph below is not stationary because the mean increases over time.

The variance of the series should not be a function of time. This property is also known as Homoscedasticity. The red graph below is not stationary because of the varying spread of data over time.

Finally, the Covariance of the i’th term and the (i+m)’th term should not be a function of time, i.e. it is only a function of Gap. In the red graph you can notice that the spread becomes closer as the time increases. Hence the Covariance is not constant with time .

Let’s now discuss about ARIMA models :
AutoRegressive Model (AR)
Autoregressive models operate under the premise that past values have an effect on current values. AR models are commonly used in analyzing nature, economics, and other time-varying processes. As long as the assumption holds, we can build a linear regression model that attempts to predict value of a dependent variable today, given the values it had on previous days. p is a parameter of how many lagged observations to be taken in.

The order of the AR model corresponds to the number of days incorporated in the formula.

Integrated(I):
A model that uses the differencing of raw observations (e.g. subtracting an observation from the previous time step). Differencing in statistics is a transformation applied to time-series data in order to make it stationary. This allows the properties do not depend on the time of observation, eliminating trend and seasonality and stabilizing the mean of the time series.
For example, first-order differencing addresses linear trends, and employs the transformation zi = yi — yi-1. Second-order differencing addresses quadratic trends and employs a first-order difference of a first-order difference, namely zi = (yi — yi-1) — (yi-1 — yi-2), and so on.

Moving Average Model (MA)
Assumes the value of the dependent variable on the current day depends on the previous days error terms. The formula can be expressed as:

where μ is the mean of the series, the θ1, …, θq are the parameters of the model and the εt, εt−1,…, εt−q are white noise error terms. The value of q is called the order of the MA model.

AutoRegressive Integrated Moving Average (ARIMA):
The ARIMA (aka Box-Jenkins) model adds differencing to an ARMA model. Differencing subtracts the current value from the previous and can be used to transform a time series into one that’s stationary. For example, first-order differencing addresses linear trends, and employs the transformation zi = yi — yi-1. Second-order differencing addresses quadratic trends and employs a first-order difference of a first-order difference, namely zi = (yi — yi-1) — (yi-1 — yi-2), and so on.


Three integers (p, d, q) are typically used to parametrize ARIMA models.

p: number of autoregressive terms (AR order)
d: number of nonseasonal differences (differencing order)
q: number of moving-average terms (MA order)
Let’ walk through some code and understand time series and ARIMA models better:
The general process for ARIMA models is the following:

Visualise the Time Series Data
Make the time series data stationary
Plot the Correlation and AutoCorrelation Charts
Construct the ARIMA Model or Seasonal ARIMA based on the data
Use the model to make predictions
