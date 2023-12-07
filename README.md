# ARIMA_ML_Models
ARIMA model for time series forecast and outlier detection
Source for multivariate anomaly detection : https://www.kaggle.com/code/vijeetnigam26/anomaly-detection-in-multivariate-time-series



Note:

CREATE OR REPLACE MODEL `project.test_table.bq_ml_covid_model`
OPTIONS (
  MODEL_TYPE = 'ARIMA_PLUS',
  TIME_SERIES_TIMESTAMP_COL='date_time',
  TIME_SERIES_DATA_COL='percent_congestion',
  TIME_SERIES_ID_COL='city_name'
) AS SELECT * FROM `bigquery-public-data.covid19_geotab_mobility_impact.city_congestion`
