## Forecasting Workflow

<small>[Arthur Mello. 2019. A Lean Forecasting Workflow](https://towardsdatascience.com/a-lean-forecasting-workflow-1a8a5eb2d4ab)</small>

<small>Forecasting: Principle and practice. Chapter 5. Rob Hyndman and George Athanasopoulos. </small>

### Request

First, you need to develop your business understanding:

- What is the goal for these forecasts (understanding the overall structure of your revenue income, guiding production decisions, reporting to shareholders…)?
- How will they be used (should they be sent to a dashboard or will they be sent to another automated system)?
- Who will use them (is it someone who is well-versed in data science, the company’s CEO, investors…)?
- Who will maintain them?
- At what level (overall, by store, by product…)?
- At what time frame (weekly, monthly…)?
- How long in advance will we generate forecasts (for the next week, the next year…)?
- Is there external data to be used (weather, holidays…)?
<small>Source: Arthur Mello. 2019.</small>

### Technical Setup
This is where you choose the tools and also workflow design. 
- Some experts recommend to have one  notebook for each step: data treatment, analysis and modelling
- Document your data sources, how they are collected, stored and merged, and where your scripts will be 

### Data Treatement
- Data Collection:
    - Queries from a database, web scrapping etc. 
    - Consider the levels of aggregation needed, external variables and timeframes.
- Data Cleaning
    - How to deal with outliers and missing values
- Feature Engineering

### Analysis

- Is there a trend? 
- Is this time series stationary? 
- Is there seasonality? At what levels (daily, weekly…)? 
- If there are external variables, how do they interact with each other (especially with the variable you are trying to predict)?
- What is the appropriate error measure for evaluation?
   - Root mean squared error: RMSE
   - Mean absolute error: MAE


![](_static/for3.png)



