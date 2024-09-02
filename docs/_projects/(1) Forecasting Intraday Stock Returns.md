---
name: Forecasting Intraday Stock Returns via Machine Learning in China’s Stock Market
tools: [Python, Linux, SSH, Data Analysis, Feature Generation, Feature Selection, Machine Learning]
image: https://github.com/MuchenHu/muchenhu.github.io/blob/master/docs/IMG_2019.png?raw=true
description: This project focuses on applying advanced machine learning techniques to forecast intraday stock returns within China’s stock market. The project involves processing and cleaning a massive 2TB+ high-frequency dataset using parallel computing. Key tasks include feature engineering and selection with a focus on snapshot order book data. Initial models explored include regression models, Random Forest, and LSTM.
---

# Forecasting Intraday Stock Returns via Machine Learning in China’s Stock Market

This long-term project, advised by Professor [Dacheng Xiu](https://dachxiu.chicagobooth.edu/) at the Booth School of Business, University of Chicago, began in August 2023. A snapshot of the project's progress as of February 2024 is well documented in my Graduate Thesis at SAIF. The project is co-advised by Hetong Di from Belvedere Trading, LLC.

## Abstract

This research leverages trade-by-trade and snapshot data to develop technical indicators for predicting intraday stock returns in China’s A-share market. It finds that signals derived from the limit order book hold greater significance than those based on trade price and volume. Feature selection is conducted through rule-based filters, focusing on the Information Coefficient (IC) and inter-feature correlations, ensuring that only the most predictive and independent features are utilized.

The study applies various machine learning models to address the prediction challenge, including regression analysis, Random Forest, and Long Short-Term Memory (LSTM) networks. The thoroughness of the feature selection process allows Ordinary Least Squares (OLS) regression to achieve robust performance. Lasso and Ridge regressions deliver results comparable to OLS, highlighting the effectiveness of the feature selection in mitigating multicollinearity and enhancing model efficiency. Conversely, Random Forest does not perform as well as OLS in backtesting, indicating a potential mismatch between the model's complexity and the data structure. The LSTM model stands out by more accurately identifying extreme performers among the stocks, underscoring its capability to capture complex, nonlinear patterns in the data.

This investigation into trading signals and predictive models, specifically tailored for China’s A-share market, combines intricate numerical analysis with economic significance. The findings not only contribute to the academic understanding of financial markets but also offer practical insights into the mechanics of trading, potentially guiding strategy development for investors and analysts operating within this market.

\* Please note that the abstract above only reflects a preliminary result.