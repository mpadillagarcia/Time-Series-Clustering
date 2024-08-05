# Time-Series-Clustering

This project aims to develop clustering models to group cryptocurrencies based on the behavior of their price time series over a 365-day period. Using data from 234 cryptocurrencies obtained from the Binance platform, data cleaning and transformation techniques are applied to adapt them to the study's objectives. Clustering models are developed and evaluated using Python and Jupyter Notebook.

## Objective

The general objective is to apply a machine learning model to understand trends in cryptocurrency price behavior, using large datasets and various clustering techniques. Solutions are compared using machine learning techniques focused on time series analysis and validated through data visualizations.

## Data

The dataset used comes from a Kaggle repository containing information on cryptocurrencies from the Binance exchange. Work is done exclusively with USDT trading pairs due to their popularity and trading volume. The data includes fields such as opening price, traded volume, and opening time, among others.

### Data Transformation
Among the data transformation steps are the following:
1. **Elimination of Unnecessary Columns**: Columns that are not necessary for the analysis are removed (high, low, close, volume, number_of_trades, taker_buy_base_asset_volume, taker_buy_quote_asset_volume).
2. **Renaming Columns**: 
   - `open_time` to `date`
   - `open` to `price`
   - `quote_asset_volume` to `volumen_usdt`
3. **Data Grouping**: Data is grouped daily, using the arithmetic mean for prices and the sum for volume.
4. **Selection of Time Interval**: A python script is used to determine the best 365-days time interval between January 2020 and December 2022. It is selected to maximize the amount of data from different cryptocurrencies.

### Price Normalization and Smoothing

Once prices have been normalized, the volatility of this sector can lead to large price changes in a short period. This can complicate the clustering process and the comparison of asset trends. For this reason, exponential moving average (EMA) fields have been added to the files based on the normalized price.

The EMA is widely used in technical analysis of financial markets and smooths fluctuations in asset prices. EMA 50, EMA 100, and EMA 200 are used in this work, being the most popular for studying asset trends in the cryptocurrency sector.

## Clustering Models

### Implemented Methods

This work implements various methods for clustering cryptocurrency time series using specialized Python libraries.

#### tslearn

The tslearn package is one of the most widely used in the field of time series clustering and is specifically oriented towards time series clustering. Field studies use this library among others.

1. **TimeSeriesKMeans**: Based on the K-means algorithm and oriented towards time series. It uses the DTW distance measure, which considers temporal shifts.
2. **KShape**: Focuses on the shape of time series, using elastic alignment for comparison.
3. **KernelKMeans**: Uses a kernel to map time series to a higher-dimensional feature space, capturing nonlinear relationships. The RBF kernel is used in this case.

#### sktime

The alternative to tslearn for time series clustering is sktime. This library offers interoperability with other widely used libraries like sklearn, pandas, and NumPy. It provides algorithms focused on time series, including machine learning models, transformation tools, and evaluation methods.

1. **TimeSeriesKMeans**: Uses the mean of time series in each group as centroids.
2. **TimeSeriesKMedoids**: Uses the time series from the dataset as medoids.

### Hyperparameters

Default values are used for parameters like the maximum number of iterations and the algorithm's tolerance. Clustering is performed with a total of 5 iterations, using between 3 and 8 clusters, and the fields `price`, `ema50`, `ema100`, and `ema200`.

## Results

- The best field to use is `ema200` with 4 and 5 clusters.
- **TimeSeriesKMeans** outperforms other methods for the Dunn index, providing more defined and compact clusters.
- **KernelKMeans** achieves better results in the Davies-Bouldin and Calinski-Harabasz indices, with shorter execution times.

## Conclusion

The results show that using the `ema200` field and applying the TimeSeriesKMeans and KernelKMeans methods provide the best clustering of cryptocurrencies based on their time series. While TimeSeriesKMeans offers more clearly defined clusters, KernelKMeans is more efficient in terms of execution time.

**Note:** This README is a summary of the project "Time Series Clustering Applied to the Cryptocurrency Market" and is designed to provide a clear and concise overview of the study's objectives, methods, and results.

[@mpadillagarcia](https://github.com/mpadillagarcia)
