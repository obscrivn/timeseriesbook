## Graphics

### Exercice 1. plot
Let's reproduce Time Series plots you saw earlier in the introduction.

- Install a library ```astsa```

```
plot(jj, type="o", ylab="Quarterly Earnings per Share")
```
- Change type "o" to 1) "l", 2) "b", 3) "s"

```
plot(globtemp, type="o", ylab="Global Temperature Deviations")
```
- Type colors() and select one color

```
colors()
```
- Change line color, example col="blue"
```
plot(globtemp, type="o", ylab="Global Temperature Deviations", col="blue")
```

- Install library xts
```
library(xts) 
djiar = diff(log(djia$Close))[-1] # approximate returns 
plot(djiar, main="DJIA Returns", type="n") 
lines(djiar)
```
- To learn about diff, type ```?diff``` in the console. Note $[-1]$ specify which row to remove. The first row in diff is alway NA (can you see why?).

```
par(mfrow=c(2,1)) 
plot(EQ5, main="Earthquake") 
plot(EXP6, main="Explosion")
```
- Change the layout by modifying mfrow integers from 2x1 to 1x2

## Exercice 2. autoplot

Let's explore more customizable plotting methods. Follow along with Chapter 2.2 [https://otexts.com/fpp3/time-plots.html](https://otexts.com/fpp3/time-plots.html)

```
melsyd_economy <- ansett %>%
  filter(Airports == "MEL-SYD", Class == "Economy") %>%
  mutate(Passengers = Passengers/1000)
autoplot(melsyd_economy, Passengers) +
  labs(title = "Ansett airlines economy class",
       subtitle = "Melbourne-Sydney",
       y = "Passengers ('000)")
```
- First rerun the code from tsibble practice

```
PBS %>%
  filter(ATC2 == "A10") %>%
  select(Month, Concession, Type, Cost) %>%
  summarise(TotalC = sum(Cost)) %>%
  mutate(Cost = TotalC / 1e6) -> a10
```

- Now run autoplot with a10

```
autoplot(a10, Cost) +
  labs(y = "$ (millions)",
       title = "Australian antidiabetic drug sales")
```

- Plot Seasons

```
a10 %>%
  gg_season(Cost, labels = "both") +
  labs(y = "$ (millions)",
       title = "Seasonal plot: Antidiabetic drug sales")
```
To learn more about gg_season, type ?gg_season in console

>Produces a time series seasonal plot. A seasonal plot is similar to a regular time series plot, except the x-axis shows data from within each season. This plot type allows the underlying seasonal pattern to be seen more clearly, and is especially useful in identifying years in which the pattern changes.

- Multiple sesonal plots

```
vic_elec %>% gg_season(Demand, period = "day") +
  theme(legend.position = "none") +
  labs(y="MWh", title="Electricity demand: Victoria")
```
- Change period from "day" to "week" and "year"

- Subplots

```
a10 %>%
  gg_subseries(Cost) +
  labs(
    y = "$ (millions)",
    title = "Australian antidiabetic drug sales"
  )
```

> A seasonal subseries plot facets the time series by each season in the seasonal period. These facets form smaller time series plots consisting of data only from that season. If you had several years of monthly data, the resulting plot would show a separate time series plot for each month. The first subseries plot would consist of only data from January. 

> The horizontal lines are used to represent the mean of each facet, allowing easy identification of seasonal differences between seasons. This plot is particularly useful in identifying changes in the seasonal pattern over time.

## Exercice 3. Case study - Australian Tourism

- Follow along with Chapter 2.5 [https://otexts.com/fpp3/subseries.html](https://otexts.com/fpp3/subseries.html)

## Exercice 4. Scatterplots

- To study the relationship between two variables, we will use scatterplots

```
vic_elec %>%
  filter(year(Time) == 2014) %>%
  ggplot(aes(x = Temperature, y = Demand)) +
  geom_point() +
  labs(x = "Temperature (degrees Celsius)",
       y = "Electricity demand (GW)")
```

## Exercice 5. Correlation

- Make sure to activate library GGally

```
visitors <- tourism %>%
  group_by(State) %>%
  summarise(Trips = sum(Trips))
  
visitors %>%
  pivot_wider(values_from=Trips, names_from=State) %>%
  GGally::ggpairs(columns = 2:9)
```
