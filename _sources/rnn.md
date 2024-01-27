## Introduction to RNN

<small>Introduction to Time Series Forecasting with Python. Jason Brownlee.</small>

<small> Deep Learning. Subir Varma and Sanjiv Das</small>

### What is RNN?

> Recurrent Neural Nets or RNNs, are DLN systems that are designed to detect patterns present in sequences of observations (e.g. speeech signals, language sentences, time series sequences). 



### Data Format

- For a general supervised learning problem aand Multilayer Perceptron, time series observations must be converted into a collection of samples where each sample has a specified number of time steps (input X) and a single time step for output (Y) - [samples, features].

![](_static/rnn1.png)

> LSTM (CNN) requieres three-dimensional format [samples, timesteps, features]:

- **Samples**. One sequence is one sample. A batch is comprised of one or more samples

- **Time Steps**. One time step is one point of observation in the sample. One sample is comprised of multiple time steps

- **Features**. One feature is one observation at a time step. One time step is comprised of one or more features.


