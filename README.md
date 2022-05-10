# Using glaciers to interpret the decision-making of deep learning hydrological models
  
This repository has all of the code to reproduce the figures and findings discussed in the presentation at the Canadian Geophysical Union in June 2022.  It is based off of the paper:  

Sam Anderson and Valentina Radic. "Interpreting deep machine learning for streamflow modelling across glacial, nival, and pluvial regimes in southwestern Canada", (in review at Frontiers in Water: Water and Artificial Intelligence, 2022). [[code]](https://github.com/andersonsam/cnn_lstm_interpret)  

In this presentation we ask: How is glacier melt represented within deep learning hydrological models?  

___
**Study region**:  

We investigate southwestern Canada, where thousands of glaciers span the Coastal and Rocky Mountain ranges leading to a wide range of basin glacier coverage.  Since a single deep learning model can successfully predict streamflow across basins with a range of glacier coverage, then there should be a mechanism within the model that represents glacier runoff.

<img src= "https://github.com/andersonsam/CGU_2022_glacier_interpret/blob/main/Figures/CGU_study_region.png" width=50% >  

**Results**:  

We find that there are a set of LSTM cell states within the LSTM component of the deep learning model that are used for simulating streamflow in glaciated basins, but are not strongly used for simulating streamflow in non-glaciated basins.  These cell states vary through time on both seasonal and daily timescales.  

<img src= "https://github.com/andersonsam/CGU_2022_glacier_interpret/blob/main/Figures/cell_states_glacial_cluster.png" width=50% >  

**Seasonal timescale**: 

We compare the seasonal signal to that of seasonal positive temperatures.  We find that the onset of the cell states lags the onset of above-freezing temperatures by approximately 1 - 2 months.  Physically, this time lag could represent the time it takes for the seasonal snow to melt and expose the glacier ice. Then, the cell state shuts off when temperatures cool.  

<img src= "https://github.com/andersonsam/CGU_2022_glacier_interpret/blob/main/Figures/LSTM_state_day_season_shade_Tday_Tseason_Tres__1_0_0_1_0.png" width=50% >  

**Daily timescale**:  

We compare the daily scale residuals of the cell states and of positive temperatures.  We find that daily-scale temperatures lead daily-scale cell state fluctuations by 2 days, and that the residuals are highly correlated only in the summer and early fall periods.  In other words, these cell states are temperature-controlled streamflow source terms that only contribute to glaciated basins.

<img src= "https://github.com/andersonsam/CGU_2022_glacier_interpret/blob/main/Figures/residuals_state_T_lag_highlight__1_1_2_1.png" width=75% >  
<img src= "https://github.com/andersonsam/CGU_2022_glacier_interpret/blob/main/Figures/correlation_state_temp_residuals.png" width=70% >  
