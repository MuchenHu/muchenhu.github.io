---
name: A Profitable Pair Selection Framework for Pairs Trading Based on CMS Open Payments Data
tools: [Python, Pairs Trading, Feature Engineering, Machine Learning, Project Management]
image: https://github.com/MuchenHu/muchenhu.github.io/blob/master/docs/certificate.png?raw=true
description: This project focuses on developing a pair trading strategy using CMS Open Payments Data. Key tasks included designing data processing procedures and encoding rules for categorical features. For feature engineering, Relief-based algorithms were implemented, and DBSCAN was used to detect comparable companies. 
---

# A Profitable Pair Selection Framework for Pairs Trading Based on CMS Open Payments Data

This project originated from the Citadel 2022 APAC Datathon Competition, where we proposed a creative pair selection framework for a pair trading strategy using the CMS Open Payments Data. Although our report was imperfect in writing, we were awarded 3rd place in the competition, recognized for the creativity of our trading ideas.

## Background and Questions
The Center for Medicare and Medicaid services (CMS) was founded in 1965 to “provide access to high quality care and improved health at lower costs”. The open payments databases of the CMS are collected and published to provide the public with a more transparent health care system. In academia, there have been various researches and investigations conducted based on this public dataset, ranging from physician targeting to compliance risks identification and COVID-19 impact.

In this report, we are going to explore the following interesting questions based on general payments, research payments, and ownership/investment interests data for 2020(Refresh publication) and 2021(Initial publication).

- From investors’ point of view, do the payments to entities and individuals(such as physicians) contain hidden information not fully captured by any other public data source and thus the markets? For example, is similar payment behavior a good indicator of comparability between companies? Does payment behavior give a clue to the potential growth of the company?

- Based on the CMS Open Payments database, is it possible to detect comparable companies using data analysis and machine learning algorithms? Furthermore, is it profitable to adopt pairs trading among ‘similar’ companies that we find?


## Executive Summary

The whole research is about how to learn the behaviors of medical industry participants and select stocks for pairs trading.

First of all, we collect, understand and clean the data. We remove all the irrelevant information from the raw data and encode the context information to numerical values. We do some statistical analysis to get intuition. This inspires us to consider building stock pools for pairs trading.

Secondly, we utilize a customized Relief-based feature extraction model to reduce the number of features. We treat the payments records as time series and combine them with associated daily stock returns.

Thirdly, we consider the information in general payments data and research payments data, and apply Density-Based Spatial Clustering of Applications with Noise method (DBSCAN) to do unsupervised clustering. For each year, we have several stock pools containing candidate stocks for pairs trading.

Lastly, we select stocks from our stock pool and apply Kalman filter to the adjusted closed price return and build a day-frequency trading strategy. We build a backtesting framework and choose stock price data from 2022.01.21 (the date after the Open Payments released) to 2022.04.15 (the latest trading day) to check the performance of our strategy. 

## Post-competition Review and Improvement
After the competition, we realized that our final step of building a trading strategy to evaluate the effectiveness of our pair selection could be further improved. We took a different approach by focusing on statistical arbitrage opportunities within the same stock pool. We forecasted the next day's price spread using ARMA and LSTM models, with the backtested strategy achieving a 72% winning rate in out-of-sample performance.

See the latest report:
<div>
    {% include elements/pdf.html src="https://github.com/MuchenHu/muchenhu.github.io/blob/master/docs/Pairs_Trading_Project.pdf?raw=true" %}
</div>