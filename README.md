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


<br>
SELECT DATE(start_date) AS DATE_ST, start_station_id, count(*) AS NO_TRIP FROM `bigquery-public-data.san_francisco.bikeshare_trips` group by 1,2 ORDER BY 1 ASC


<br>

CREATE OR REPLACE MODEL
  `xx.test_table.bq_ml_covid_model` OPTIONS ( MODEL_TYPE = 'ARIMA_PLUS',
    TIME_SERIES_TIMESTAMP_COL='DATE_ST',
    TIME_SERIES_DATA_COL='NO_TRIP',
    TIME_SERIES_ID_COL='start_station_id' ) AS

SELECT * FROM
(SELECT DATE(start_date) AS DATE_ST, start_station_id, count(*) AS NO_TRIP FROM `bigquery-public-data.san_francisco.bikeshare_trips` group by 1,2) 

<br>

SELECT * FROM

ML.DETECT_ANOMALIES (
  MODEL  `xxx.test_table.bq_ml_covid_model`,
  STRUCT(0.8 AS anomaly_prob_threshold)
)

#### test