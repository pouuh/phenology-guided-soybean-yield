# Phenology-Guided Soybean Yield Dataset

This repository is primarily for the dataset used in soybean yield prediction research.

### Dataset Overview
This section loads the pre-processed satellite-derived time series data for soybean yield prediction. The dataset consists of:

- **Training Set**: Multi-temporal observations from multiple growing seasons
- **Test Set**: Holdout data for final model evaluation
- **Features**: 14 environmental variables captured at regular intervals throughout the growing season
- **Target**: County-level soybean yield measurements (bushels per acre)

### Data Structure
- **Input Shape**: `(samples, timesteps, features)` - 3D array representing time series
- **Temporal Resolution**: Weekly to bi-weekly observations during growing season
- **Spatial Resolution**: County-level aggregated values
- **Years Covered**: 2018-2021 for model development and testing

### Loading

#### Input Features (X)
The input data for our models (`X_train.npy`, `X_test.npy`, `[year]_X.npy`) are time series with a shape of `(samples, timesteps, features)`, where `timesteps` represent 6 phenological stages and `features` include 14 predictors:

* **EVI2 (Enhanced Vegetation Index 2):**
	* *Description:* A satellite-derived measure of vegetation greenness and canopy health.
	* *Significance for Yield:* Higher EVI2 generally indicates a healthier, more photosynthetically active crop, which is essential for biomass accumulation and ultimately for producing higher yields through processes like pod development and seed fill. Stress events affecting EVI2 can signal potential yield reductions.

* **LST_Day (Daytime Land Surface Temperature in °C):**
	* *Description:* The temperature of the ground surface during the day.

* **LST_Night (Nighttime Land Surface Temperature in °C):**
	* *Description:* The temperature of the ground surface during the night.

* **tmax (Maximum daily air temperature in °C):**
	* *Description:* Highest air temperature recorded in a day.

* **tmin (Minimum daily air temperature in °C):**
	* *Description:* Lowest air temperature recorded in a day.

* **ppt (Precipitation in mm):**
	* *Description:* Accumulated rainfall.

* **vpdmax & vpdmin (Maximum/Minimum Vapor Pressure Deficit in hPa):**
	* *Description:* Measure of atmospheric dryness (the difference between how much moisture the air can hold and how much it actually holds).

* **Evap_tavg (Average Evapotranspiration in kg/m^2/s or mm/day):**
	* *Description:* Actual water loss from the soil surface (evaporation) and plant tissues (transpiration).

* **PotEvap_tavg (Average Potential Evapotranspiration in W/m^2 or mm/day):**
	* *Description:* The amount of evapotranspiration that would occur if sufficient water were available.

* **SoilMoi0_10cm (Soil moisture at 0-10 cm depth in kg/m^2 or mm):**
	* *Description:* Water content in the top soil.

* **SoilMoi10_40cm, SoilMoi40_100cm, SoilMoi100_200cm (Soil moisture at increasing depths):**
	* *Description:* Water content in deeper soil layers.

#### Target Variable (Y)
The target variable for prediction (`Y_train.npy`, `Y_test.npy`) is:
* **County-Level Soybean Yield:**
	* *Unit:* Bushels per acre (bu/ac).
	* *Significance:* This is the primary measure of agricultural productivity for soybeans. Accurate and timely yield prediction is crucial for farmers, policymakers, insurers, and commodity markets for planning, risk assessment, and economic forecasting.