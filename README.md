# Temporal Analysis of Electricity Use Across NYC Boroughs

## Project Overview

This project analyzes monthly electricity consumption patterns across New York City's five boroughs using the NYC Electric Consumption and Cost dataset from 2010 through September 2025. The goal is to understand long-term trends, seasonal behavior, borough-level differences, and future electricity consumption patterns through time-series analysis.

The project focuses on three main questions:

1. How has electricity consumption changed across NYC boroughs over time?
2. Do boroughs show consistent seasonal electricity usage patterns?
3. Can historical monthly consumption be used to forecast borough-level electricity demand through 2026?

## Dataset

The analysis uses the **Electric Consumption and Cost dataset**, containing utility billing and electricity usage records for NYC developments.

Key fields used:

- `Borough`
- `Revenue Month`
- `Consumption (KWH)`
- `Current Charges`

The original dataset contained over **553,000 records**. For this analysis, the data was cleaned, filtered, and aggregated to a monthly borough-level time series.

## Data Cleaning and Preprocessing

The preprocessing steps included:

- Loaded the raw CSV file into a pandas DataFrame.
- Selected relevant columns for borough, revenue month, electricity consumption, and current charges.
- Converted `Revenue Month` into datetime format.
- Cleaned currency and numeric fields by removing dollar signs and commas.
- Excluded non-borough categories such as `FHA` and `NON DEVELOPMENT FACILITY`.
- Aggregated electricity consumption by borough and month.
- Checked for missing values and temporal gaps.
- Selected the modern continuous period from **2019 onward** for time-series modeling.

After aggregation, the final monthly dataset contained electricity consumption values for each of the five NYC boroughs:

- Bronx
- Brooklyn
- Manhattan
- Queens
- Staten Island

## Exploratory Data Analysis

The exploratory analysis examined overall citywide trends and borough-level patterns.

### Trend Analysis

A 12-month moving average was used to smooth short-term variation and identify broader electricity consumption trends. This helped reduce monthly noise and highlight long-term changes in borough-level consumption.

### Seasonality Analysis

Monthly boxplots and seasonal decomposition were used to examine whether electricity usage followed recurring annual patterns. The analysis explored whether consumption varied by month, likely due to seasonal weather-driven demand such as heating and cooling needs.

### Borough-Level Comparison

The analysis compared electricity usage across boroughs to identify which boroughs had higher or lower baseline consumption and whether their patterns changed similarly over time.

## Time-Series Methods

The project used several time-series techniques:

### Seasonal Decomposition

Multiplicative seasonal decomposition was applied to each borough's monthly electricity consumption series. This separated each time series into:

- Observed values
- Trend component
- Seasonal component
- Residual component

This helped distinguish long-term movement from recurring seasonal patterns and unexplained variation.

### Stationarity Testing

The Augmented Dickey-Fuller test was used to evaluate whether the time series was stationary. Since time-series models such as ARIMA generally require stationarity, first differencing was applied before examining the ACF and PACF plots.

### ACF and PACF Diagnostics

Autocorrelation and partial autocorrelation plots were used to inspect lag structure after first differencing. These plots helped guide the selection of ARIMA parameters by showing how current electricity consumption relates to previous months.

## Forecasting Approach

ARIMA models were fitted separately for each borough's monthly electricity consumption series. The model was used to forecast electricity consumption through the end of 2026.

The forecasting workflow included:

1. Preparing borough-level monthly time series.
2. Applying first differencing.
3. Reviewing ACF and PACF plots.
4. Fitting ARIMA models.
5. Generating monthly forecasts.
6. Creating confidence intervals around forecast estimates.
7. Summarizing projected 2026 annual electricity consumption by borough.

## Key Findings

The analysis found that:

- NYC electricity consumption shows clear borough-level differences.
- Monthly electricity demand follows recurring seasonal patterns.
- A 12-month moving average helps reveal broader trends that are not obvious from raw monthly values.
- Borough-level consumption can be forecasted using ARIMA-based time-series modeling.
- Forecast uncertainty increases as the forecast moves further into the future, which is expected in time-series forecasting.

## Visualizations

The notebook includes the following visualizations:

- Monthly electricity consumption by borough
- 12-month moving average trend lines
- Seasonality boxplots by month
- Seasonal decomposition plots for each borough
- ACF and PACF plots after first differencing
- ARIMA residual diagnostic plots
- Borough-level electricity consumption forecasts through 2026
- Projected 2026 annual electricity consumption by borough

## Tools and Libraries

This project was completed using Python and the following libraries:

- pandas
- numpy
- matplotlib
- seaborn
- statsmodels

## Project Structure

```text
.
├── Temporal Analysis of Electricity Use Across NYC Boroughs.ipynb
├── README.md
└── data/
    └── Electric_Consumption_And_Cost_(2010_-_Sep_2025).csv
