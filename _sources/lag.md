## Lagged Value and Autocorrelation

**Lagged Plots**

A lag plot is a special type of scatter plot in which the Y-axis represent time units (Y) and the X-axis represents time units behind (Y - lag) or ahead (Y + lag). The difference between these time units is called ```lag``` or ```lagged``` and it is represented by k.

The lag plot is used to answer the following questions:

1. Distribution of Model (Model Suitability) 
    - Distribution of model here means deciding what is the shape of data on the basis of the lag plot: 
        - If the lag plot is linear, then the underlying structure is of the autoregressive model
        - If the lag plot is of elliptical shape, then the underlying structure represents a continuous periodic function such as sine, cosine, etc.
2. Outliers 
   - Outliers are a set of data points that represent the extreme values in the distribution
   
3. Randomness in data 
   - The lag plot is also useful for checking whether the given dataset is random or not. 
4. Seasonality
   - If there is seasonality in the plot then, it will give a periodic lag plot.
5. Autocorrelation
   - If the lag plot gives a linear plot, then it means the autocorrelation is present in the data 
   - If more data is concentrated on the diagonal in lag plot, it means there is a strong autocorrelation
   
   
   https://www.geeksforgeeks.org/lag-plots/