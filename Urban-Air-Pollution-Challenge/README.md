# Urban Air Pollution Challenge by #ZindiWeekendz
Can you predict air quality in cities around the world using satellite data?

You may have seen recent news articles stating that air quality has improved due to COVID-19. This is true for some locations, but as always the truth is a little more complicated. In parts of many African cities, air quality seems to be getting worse as more people stay at home. For this challenge we’ll be digging deeper into the data, finding ways to track air quality and how it is changing, even in places without ground-based sensors. This information will be especially useful in the face of the current crisis, since poor air quality makes a respiratory disease like COVID-19 more dangerous.

We’ve collected weather data and daily observations from the Sentinel 5P satellite tracking various pollutants in the atmosphere. Your goal is to use this information to predict PM2.5 particulate matter concentration (a common measure of air quality that normally requires ground-based sensors to measure) every day for each city. The data covers the last three months, spanning hundreds of cities across the globe.

The objective of this challenge is to predict PM2.5 particulate matter concentration in the air every day for each city. PM2.5 refers to atmospheric particulate matter that have a diameter of less than 2.5 micrometers and is one of the most harmful air pollutants. PM2.5 is a common measure of air quality that normally requires ground-based sensors to measure. The data covers the last three months, spanning hundreds of cities across the globe.

The data comes from three main sources:

`Ground-based air quality sensors`. These measure the target variable (PM2.5 particle concentration). In addition to the target column (which is the daily mean concentration) there are also columns for minimum and maximum readings on that day, the variance of the readings and the total number (count) of sensor readings used to compute the target value. This data is only provided for the train set - you must predict the target variable for the test set.

`The Global Forecast System (GFS)` for weather data. Humidity, temperature and wind speed, which can be used as inputs for your model.

`The Sentinel 5P satellite.` This satellite monitors various pollutants in the atmosphere. For each pollutant, we queried the offline Level 3 (L3) datasets available in Google Earth Engine (you can read more about the individual products here: https://developers.google.com/earth-engine/datasets/catalog/sentinel-5p). For a given pollutant, for example NO2, we provide all data from the Sentinel 5P dataset for that pollutant. This includes the key measurements like NO2_column_number_density (a measure of NO2 concentration) as well as metadata like the satellite altitude. We recommend that you focus on the key measurements, either the column_number_density or the tropospheric_X_column_number_density (which measures density closer to Earth’s surface).
Unfortunately, this data is not 100% complete. Some locations have no sensor readings for a particular day, and so those rows have been excluded. There are also gaps in the input data, particularly the satellite data for CH4.

## Variable Definitions: Read about the datasets at the following pages:

`Weather Data`: https://developers.google.com/earth-engine/datasets/catalog/NOAA_GFS0P25

`Sentinel 5P data:` https://developers.google.com/earth-engine/datasets/catalog/sentinel-5p - all columns begin with the dataset name (eg L3_NO2 corresponds to https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S5P_OFFL_L3_NO2) - look at the corresponding dataset on GEE for detailed descriptions of the image bands - band names should match the second half of the column titles.

## Files available for download:

`Train.csv` - contains the target and supporting data for 349 locations. This is the dataset that you will use to train your model.

`Test.csv`- resembles Train.csv but without the target-related columns, and covers 179 different locations.This is the dataset on which you will apply your model to.

`SampleSubmission.csv` - shows the submission format for this competition, with the ‘Place_ID X Date’ column mirroring that of Test.csv and the ‘target’ column containing your predictions. The order of the rows does not matter, but the names of the Place_ID X Date must be correct.
