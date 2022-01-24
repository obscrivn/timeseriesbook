## Smoothing

<small>Introductory Time Series with R. Cowpertwait and Metcalfe</small>

<small>Time Series Analysis and Its Applications With R Examples. Shumway and Stooffer</small>

> Smoothing is a technique applied to time series to remove the fine-grained variation between time steps


- Smoothing procedures usually use points before and after the time at which the smoothed estimate is to be calculated.

    - A consequence: the smoothed series will have some points missing at the beginning and the end.

Two distinct groups of smoothing methods:

- Averaging Methods
- Exponential Smoothing Methods

### Moving Average

> A moving average is commonly used with time-series data to smooth out short-term fluctuations and highlight longer-term trends or cycles

One-sided Moving Average

![](_static/ma1.png)

Two-sided Centered Moving Average (odd time periods)

![](_static/ma2.png)

Two-sided Weighted Moving Average (even time periods)

![](_static/ma3.png)

For a one-sided moving average, the moving average is placed at the end of values being averaged. For a two-sided moving average, the moving average is centered at the middle of the values being averaged. Here is an example for 3 periods moving average:

![](_static/ma4.png)

The difficulty with an even number of seasons is that there is **no midpoint**. Six is not the midpoint of 1 to 12, and neither is 7; its purely theoretical midpoint is 6.5.

>  The idea when there is an even number of seasons, is to pull that midpoint forward by half a season: That is done by taking two consecutive moving averages and averaging them.

This is our example for 4-term average. So we have MA = t-0.5 in the first case and MA = t+0.5 in the second case.
![](_static/ma5.png)

![](_static/ma6.png)

Now we can smooth overr smoothed values:

![](_static/ma7.png)





