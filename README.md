# CFalvo_EnvDataAnalytics_FinalProject
This is a course project outlining skills learned in Environmental Data Analytics course (Duke, Spring 2020). The project explores and analyzes Global Fishing Watch data supplemented with SESYNC data to assess which variables are the best predictors of fishing activity. 

## Summary

This repository houses a final project in an Environmental Data Analytics course, taken at Duke University in spring 2020 and taught by Kateri Salk-Gunderson. The purpose of the project is to both examplify R skills and best practices learned in the course and to pose and answer some research questions I have about commercial fishing. 

The data I am exploring for this project comes from Global Fishing Watch, a non-profit organization that strives to increase transparency in global fishing activity through providing open-source data and tools (https://globalfishingwatch.org/data-download/datasets/public-training-data-v1). Global fishing watch takes AIS data, tracking data for commercial ships that are made publically available, and runs algorithms that characterize the AIS data into various categories. 

The particular data I chose to analyze are the locations and times that two different fishing vessels were detected. The fishing vessels were characterized as longline vessels (vessels that use a longline type of fishing gear) and have several variables associated with each spatiotemporal point (speed, distance from shore, distance from port, and whether or not the vessel is believed to be fishing or not). I obtained net primary productivity data for the observed vessel locations to serve as an additional predictor variable. My primary goal in this exploration was to investigate which variables are the best predictors of fishing activity.  

## Investigators

Cristiana Falvo

## Keywords

fishing, global fishing watch, longline, binomial regression model, statistics, tidyverse, mapview, leaflet, SESYNC

## Folder structure, file formats, and naming conventions 

The following folders are included in this repository:

+ Data: contains folders for raw and processed data
+ Code: contains separate R scripts for each stage of the general processing (data processing, data analysis)

## Database Information

#### Data from Global Fishing Watch (GFW): Longline Vessel Tracking Data (CSV)
+ These longline data, like many data sets from Global Fishing Watch, originated from raw automatic identification system (AIS) data and were processed and released. By analyzing movement patterns, Global Fishing Watch’s neural networks transform raw AIS data into contextual information about fishing activity. 
+ The longline data I obtained is a CSV file that includes locations, times and fishing activity status of two different vessels. There are additional attributes of ‘distance from shore’ and ‘vessel speed’.
+ Link to data source: https://globalfishingwatch.org/datasets-and-code/ (accessed on 3/18/2020)

#### Data from the National Socio-Environmental Synthesis Center (SESYNC): Net Primary Productivity Data (CSV)
+ SESYNC’s Marine Socio-Environmental Covariates Shiny App provides oceanographic information based on latitude longitude locations that can be fed into the app. To supplement my longline fishing dataset, I obtained net primary productivity (NPP) data from each vessel observation location in my dataset. Majority of the NPP values lined up with the coordinates I provided, and a portion of the values were interpolated. 
+ Net primary productivity (NPP) data are reported as average values in milligrams of carbon per meter squared per day (mg C/m^2^ day).
+ Link to data source: https://shiny.sesync.org/apps/msec/ (accessed on 3/25/2020)

## Scripts and code

Within the 'Code' folder:

- Wrangling_LonglineData.Rmd: This script brings the raw data into R for some initial data frame exploration and cleaning. The script transforms the raw longline data to processed longline data by filtering and reformatting columns in order to prepare the data for analysis. More detailed documentation is included throughout the script. 

- Wrangling_NPP.Rmd: This script transforms the raw NPP data (downloaded from SESYNC) into processed data (fields are put into appropriate formats for exploration and analysis) and joins the NPP data to the processed longline data to make the combined data set.

- Exploration_Mapping.Rmd: Using mapview and leaflet packages, this script explores the data set at its full extent and focused in on each vessel extent. This mapping script was used as a way to visually explore the different predictor variables and their correlations with fishing activity. 

- Exploration_GLM.Rmd: This script was used for the analysis of the project. The analysis process involved creating a binomial regression model for the predictor variables of fishing activity, running an AIC step analysis to determine the optimal combination of variables, viewing individual variable correlations and outputting model statistics such as AIC values and percent deviance explained. All of these steps were run for the full data set, vessel 1 data and vessel 2 data separately. 

## Entity and Attribute information for processed data set:

Data Field | Definition | Units | Source
------------- | ------------- | ------------- | -------------
ID | Unique identifier for observation | NA | GFW
MMSI | Unique identifier for vessel | NA | GFW
Date | Date of observation | YYYY-MM-DD | GFW
Latitude | Latitude coordinate of observation | Decimal Degrees | GFW
Longitude | Longitude coordinate of observation | Decimal Degrees | GFW
Vessel_Speed | Speed of vessel at observed point | Knots | GFW
Distance_From_Shore | Distance vessel is observed from shore | Meters | GFW
NPP_Mean | Mean net primary productivity value | mg C/m^2^ day | SESYNC
Fishing_Activity | Indication of whether observed vessel is determined to be fishing (1) or not fishing (0) based on GFW algorithms | NA | GFW

## Quality and Usage Information

These data have been made accessible for anyone to explore and use, but users should understand the limitations of knowledge based on the level of uncertainty associated with the information. See below for details specific to each data source:

+ Global Fishing Watch Data: Global Fishing Watch runs raw AIS data through neural networks that have been expertly trained so that the algorithm can distinguish between different types of commercial fishing activities just by analyzing the movement patterns gathered from satellites. Users should be aware that the certainty associated with the fishing activity status (used as the explanatory variable in this analysis) is less than 100%. More information about how the raw AIS data were processed and classified can be found on the source site: https://globalfishingwatch.org/

+ SESYNC Data: The mean net primary productivity data that was added to the global fishing watch data and used as a predictor variable in models was obtained by feeding coordinates into the SESYNC shiny app and downloading the resulting values associated with these locations. Users should be aware that most of these values line up with the inputted coordinates, and thus return data extracted from 8-day composite layers from 2003-2013 produced by NOAA CoastWatch, but a portion of these values are interpolations due to locations not exactly lining up with inputs. Full methods are documented in the shiny app report: https://docs.google.com/document/d/1o264v5JS3MTZoOCO2nWOMRh4Z-DMVGZTba6kz9RSj7I/edit. 