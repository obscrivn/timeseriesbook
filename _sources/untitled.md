## Autocorrelation Practice

<small> Source: Tidy Time Series. Rob Hyndman. Rstudio 2020 </small>
<small> Source: Introductory Time Series in R. Cowpertwait et al. </small>

### About
> In this practice you will learn about lag and ACF plots.


**Data Needed**

Download from Canvas
- wave





### TS Objects

1. The function ```ts``` is built-in and is used to create time-series objects.

```
ts(1:10, frequency = 4, start = c(1959, 2)) # start from 2nd Quarter of 1959
```
![](_static/Part1-ts.png)

2. Upload wave.dat data and create plot. You can also slice time series. waveht is the column name. Data height (mm relative to still water level) is measured at the centre of a wave tank.

```
wave <- read.table('data/wave.dat',header=T)
plot(ts(waveht))
plot(ts(waveht[1:60]))
```
![](_static/Part1-1.png)

![](_static/Part1-2.png)

```{note}
The upper plot shows the entire time series. There are no outlying values. The lower plot is of the first sixty wave heights. We can see that there is a tendency for consecutive values to be relatively similar and that the form is like a rough sea, with a quasi-periodicity but no fixed frequency.
```

3. The function ```acf``` computes (and by default plots) estimates of the autocovariance or autocorrelation function.

The autocorrelations of x are stored in the vector $$acf(x)\$acf$$, with the lag k autocorrelation located in $$acf(x)\$acf[k+1]$$. For example, the lag 1 autocorrelation for waveht is
```
acf(waveht)$acf[2]  # 0.47

```
Object contains:
-  An index: time information about the observation
-  Measured variable(s): numbers of interest
-  Key variable(s): optional unique identifiers for each series


tsibble data ```global_economy```
- Economic indicators featured by the World Bank from 1960 to 2017

```
global_economy
```
![](_static/w1object.png)

tsibble data ```tourism```
- A dataset containing the quarterly overnight trips from 1998 Q1 to 2016 Q4 across Australia

```
tourism
```
![](_static/w1tourism.png)

<!--<img src="_static/w1object.png" width="400">-->

### Tsibble Index

**Table 1. Common Time Index variables**
|Frequency | Function |
| :-: | :-: |
|Annual | start:end|
Quarterly |yearquarter()|
Monthly |yearmonth()|
Weekly| yearweek()|
Daily |as_date(), ymd()|
Sub-daily |as_datetime()|

**Example 1: Create a table**
```
mydata <- tsibble(
  year = 2012:2016,
  y = c(123,39,78,52,110),
  index = year
)
mydata
```
<figure>
  <img src="_static/w1example1.png" width="400">
</figure>


:::{note}
If observations are more frequent than **once per
year**, use ```a time class function``` on the index (see Table 1).
:::

### Working with tsibble

We will be using some common data manipulation methods from dplyr:
- mutate() adds new variables that are functions of existing variables
- select() picks variables based on their names
- filter() picks cases based on their values
- summarise() reduces multiple values down to a single summary.
- arrange() changes the ordering of the rows.

For more information, see - [https://dplyr.tidyverse.org/](https://dplyr.tidyverse.org/)

**Example 2: Convert CSV to tsibble**

```
prison <- readr::read_csv("prison_population.csv") %>%
mutate(Quarter = yearquarter(date)) %>%
select(-date) %>%
as_tsibble(
index = Quarter,
key = c(state, gender, legal, indigenous)
)
```
:::{note}
- MUTATE -> create a new column _Quarter_ using Time Index ```yearquarter()```. All dates with the format 01/03/2020 are converted to Q1 2020, Q2 2020 etc
- SELECT -> select all columns except date
:::

**Example 3: Filter columns**

```
PBS %>%
filter(ATC2 == "A10") %>%
select(Month, Concession, Type, Cost)
```
<figure>
  <img src="_static/w1example4.png" width="400">
</figure>

**Example 4: summarise cost**

```
PBS %>%
filter(ATC2 == "A10") %>%
select(Month, Concession, Type, Cost) %>%
summarise(total_cost = sum(Cost))
```

**Example 5: mutate and create a new variable**

```
PBS %>%
filter(ATC2 == "A10") %>%
select(Month, Concession, Type, Cost) %>%
summarise(total_cost = sum(Cost)) %>%
mutate(total_cost = total_cost / 1e6) -> a10
```