# Capstone1_Alt_Fuels
# Predicting the Market Penetration of Alternative Fuel Stations and Vehicles across United States

This project focuses on the number of alternative fuel stations and the number alternative fuel powered vehicles across the United States, its growth trend and developing a predictive model.

Station data and vehicle inventory data has been collected from https://afdc.energy.gov/data_download/  
(https://afdc.energy.gov/data_download/). 

1. Data Wrangling
Performed data wrangling and saved the clean files as csv for future use to perform Exploratory Data Analysis and ML.  
https://github.com/glazenda/Capstone1_Alt_Fuels/blob/master/Alt_Fuel_DW.ipynb

2. Exploratory Data Analysis
Over the last 15 years the total number of alternative fuel stations has grown exponentially.
Form the individual plots we can clearly see steep increase in E85, BD and Electric fuel stations while CNG, LNG, LPG and HY show decline in the number of stations from about 2015.
https://github.com/glazenda/Capstone1_Alt_Fuels/blob/master/Alt_Fuel_EDA_ML.ipynb

3. Machine Learning
ARIMA and LSTM Models implemented to predict number of alternative fuel stations facilities will be opening yearly.

. We fit an ARIMA (0, 1, 1) model this sets the lag value to 0 for auto regression, uses a difference order of 1 to make the time series sationary, and uses a moving average model of 1. 
https://github.com/glazenda/Capstone1_Alt_Fuels/blob/master/Alt_Fuel_ML.ipynb
one-step out-of sample forecast - ARIMA:
array ([2285.93941588, 2419.5423177, 2553.14521953, 2686.74812136,2820.35102319]) 
RMSE: 710
The model predicted the growth rate of number of fuel stations to be at the rate of 5% YoY. 

. We will implement LSTM - benefit of this type of network is that it can learn and remember over long sequences and does not rely on a pre-specified window lagged observation as input. The model predicted with an RMSE of 521.

. LSTM performed well compared to ARIMA and will work on tuning the model and will consider predicting number of alternative fuel stations facilities will be opening monthly.
We repeat the experiment multiple times(30), then take the average RMSE as an indication of how well the configuration would be expected to perform on unseen data on average.
https://github.com/glazenda/Capstone1_Alt_Fuels/blob/master/Alt_Fuels_ML_Monthly_LSTM_RobustModel.ipynb

. LSTM Hyperparameter Tuning -  Each experimental scenario will be run 10 times for a given neuron and for a given epoch. Number of Neurons ranges from 1 to 5 and the number of epoch ranges from 2^0 to 2^12.  The batch_size must be set to 1. This is because it must be a factor of the size of the training and test datasets. The predict() function on the model is also constrained by the batch size; there it must be set to 1 because we are interested in making one-step forecasts on the test data. The reason for this is that the random initial conditions for an LSTM network can result in very different results each time a given configuration is trained.
A diagnostic approach will be used to investigate model configurations. This is where line plots of model skill over time will be created and studied for insight into how a given configuration performs and how it may be adjusted to elicit better performance. The model will be evaluated on both the train and the test datasets at the end of each epoch and the RMSE scores saved.
https://github.com/glazenda/Capstone1_Alt_Fuels/blob/master/Alt_Fuels_ML_Monthly_LSTM_HyperparameterTuning.ipynb

# LSTM Diagnostics
# From the mean performance alone, the results suggest a network configuration with 4 neurons as having the best performance over 128 epochs with a batch size of 1. This configuration also shows the lowest RMSE and tightest variance. 
https://github.com/glazenda/Capstone1_Alt_Fuels/blob/master/Alt_Fuels_Hyperparameter_Diagnostics.ipynb

# Conclusion
It is clear from the data and the predictions that there is significant growth in use of alternate fuels in the automobile industry especially in the recent past.  Using alternate fuels in automobiles, not only provides sustainable growth and most significantly it reduces the harmful Carbon-dioxide gases emitting to the atmosphere.  Several alternate fuels in discussion in this article burns clean and they are environmentally friendly.  In the last decade, the average retail fuel prices in the USA has been rather stable and may be slightly on a decline trend (https://afdc.energy.gov/fuels/prices.html).  I believe this trend will continue and change in years to come favoring towards alternative fuels due to the following factors: 
---- as the dependency on petroleum fuels (gasoline and diesel oil) continue to decline
---- more environmentally conscious vehicle owners interested in alternate fuel driven vehicles  
---- increased availability of the gas stations for the commuters / vehicle owners 
---- leap in technology to produce alternative fuels with lower production cost  
---- fuels that are safer to use 
 This report favors the industries that are in production of automobile vehicles enabling the use of alternative fuels, industries that produce alternative fuels, vehicle owners who are with sustainability mindset and interested in leaving positive footprints to the environment, government that continues to thrive increasing vehicle fleet with alternative fuels and gas stations providing flexibility with various fuel types. 
