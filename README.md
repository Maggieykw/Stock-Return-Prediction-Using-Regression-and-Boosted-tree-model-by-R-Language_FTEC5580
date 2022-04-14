# Stock-Return-Prediction-Using-Regression-and-Boosted-tree-model_FTEC5580

We are interested in predicting monthly returns of stocks using linear regres- sion models and boosted trees. Consider the following formulation:

<img width="833" alt="Screenshot 2022-04-14 at 6 53 44 PM" src="https://user-images.githubusercontent.com/30870497/163377335-3ae24d33-7e1b-4f33-9f96-049e1e5e86f8.png">

## Tasks
1. Perform ordinary least squares (OLS) regression with all 49 covariates (with and without 10-fold CV)
2. Perform regression with LASSO, PLS and boosted trees by the 10-fold CV
3. Determine which covariates are significant for predicting the return of the next month

For the modelling and the model performance, please refer to the file 'Predictive Model.ipynb'

Remark: The 49 covariates are on different scales. You need to standardize them before using them in any regression and the boosted tree model. Standardization means dividing a covariate by its sample standard deviation.

## Dataset
Data is collected from CRSP, CompuStat and WRDS Beta Suite. All three databases can be accessed through Wharton Research Data Services (WRDS). For each stock, there are 120 observations and thus the observations of all 30 stocks combined is 3600.

The data contains the following types information:
- Ticker: the tickers for 30 stocks (current constitutents of the DJIA index with DOW replaced by C).
- Month: From Dec 2009 till Dec 2019. We use covariates of the current month to predict the return of the next month.
- Covariates: There are 49 covariates in total, including the current-month return and mea- sures constructed using the price data, and beta, alpha, idiosyncratic and total volatility of a stock as well as financial ratios. For the details of financial ratios, please refer to “WRDS Industry Financial Ratio Manual.pdf”
- Response variable: RETN, which stands for return of the next month.

### Explanation of some Variables
- VOL: Trading Volume
- RETC: Return of the Current Month
- RETN: Return of the Next Month
- SPREAD: Closing Ask minus Closing Bid
- OSC: (Highest Price - Lowest Price)/Closing Price
- sprtrn: Monthly Return of S&P Composite Index
- ALPHA: Alpha
- B_MKT: Beta on MKT
- IVOL: Idiosyncratic Volatility
- TVOL: Total Volatility

The initial data downloaded from the databases contain missing values. To deal with them, we follow a common practice to use the average value of the covariates for all other companies in the same month as a replacement of the missing values. That is, if covariate Xj of Stock i is missing in Jan 2010, then the average value of Xj of the other 29 stocks in Jan 2010 is used. After data processing, we obtain the file “data.csv”, which is ready for use.
