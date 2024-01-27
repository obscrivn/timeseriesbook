## Introduction to VAR

<small>Chapter 12. Forecasting: Principles and Practice</small>

<small> Aptech. Introduction to the Fundamentals of Vector Autoregressive Models. 2021</small>

### What is VAR?

> The forecast variable is influenced by the predictor variables, but the revverse relation is not allowed.

Example: the changes in personal consumption expenditure in US are forecast based on the changes in personal income (Ch.10)

![](_static/var1.png)

A bi-directional relationship may be more suitable: an increase in Income can lead to an increase in Consimption an dvice versa -  a bi-directional relationship may be more suitable 

> Vector Autoregression (VAR) is a forecasting algorithm that can be used when two or more time series influence each other. The relationship between the time series involved is bi-directional and  all variables are treated symmetrically.

Basic Requiremenst for the VAR framework:

- At least two time series (variables)

- The time series should influence each other

> Q1: Why is it called **Autoregressive**?

-  Each variable (Time Series) is modeled as a function of the past values (the lags of the series). 
- While Autoregressive models (AR, ARMA or ARIMA) are uni-directional, Vector Auto Regression (VAR) is bi-directional.

**Advantage**

- A systematic but flexible approach for capturing complex real-world behavior
- Better forecasting performance
- Ability to capture the intertwined dynamics of time series data


- VAR models are traditionally widely used in finance and econometrics, but recently VAR models have been gaining traction in other fields like epidemiology, medicine, and biology.



**When to use it**

- forecasting a collection of related variables where no explicit interpretation is required

- testing whether one variable is useful in forecasting another (the basis of Granger causality tests)

- impulse response analysis, where the response of one variable to a sudden but temporary change in another variable is analysed

- forecast error variance decomposition, where the proportion of the forecast variance of each variable is attributed to the effects of the other variables

![](_static/var2.png)

<small>Source: https://www.aptech.com/blog/introduction-to-the-fundamentals-of-vector-autoregressive-models/ </small>

## Models

![](_static/var3.png)

- Since the Y terms in the equations are interrelated, the Y’s are considered as endogenous variables, rather than as exogenous predictors.

There are three broad types of VAR models: the reduced form, the recursive form, and the structural VAR model

### Reduced Form

Reduced form VAR models consider each variable to be a function of:

- Its own past values

- The past values of other variables in the model

**Disadvantages**

- Contemporaneous variables are not related to one another

- The error terms will be correlated across equations: we cannot consider what impacts individual shocks will have on the system

### Recirsive Form

Recursive VAR models contain all the components of the reduced form model, where each variable to be a function of:

- Its own past values

- The past values of other variables in the model

In addition, it allows some variables to be functions of other concurrent variables. 

> By imposing these short-run relationships, the recursive model allows us to model structural shocks.

### Structural VAR

> Structural VAR models include restrictions that allow us to identify causal relationships beyond those that can be identified with reduced form or recursive models. These causal relationships can be used to model and forecast impacts of individual shocks, such as policy decisions


## Model Specification

When referring to VAR models, we often need to specify:

- How many endogenous variables there are included

- How many autoregressive terms are included

if we have **2 endogenous variables** and **2 autoregressive terms** (2 lags), the model is a Bivariate VAR(2) model.

> Q2: How do we choose the number of lags in a VAR model?


