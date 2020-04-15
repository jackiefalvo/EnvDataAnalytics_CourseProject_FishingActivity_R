# CFalvo_EnvDataAnalytics_FinalProject
This is a course project outlining skills learned in Environmental Data Analytics course (Duke, Spring 2020). The project processes and analyzes AIS data from Global Fishing Watch (globalfishingwatch.org).

## Summary

This repository houses a final project in an Environmental Data Analytics course, taken at Duke University in spring 2020 and taught by Kateri Salk-Gunderson. The purpose of the project is to both examplify R skills and best practices learned in the course and to pose and answer some research questions I have about commercial fishing. 

The data I am exploring for this project comes from Global Fishing Watch, a non-profit organization that strives to increase transparency in global fishing activity through providing open-source data and tools (https://globalfishingwatch.org/data-download/datasets/public-training-data-v1). Global fishing watch takes AIS data, tracking data for commercial ships that are made publically available, and runs algorithms that characterize the AIS data into various categories. 

The particular data I chose to analyze are the locations and times that two different fishing vessels were detected. The fishing vessels were characterized as longline vessels (vessels that use a longline type of fishing gear) and have several variables associated with each spatiotemporal point (speed, distance from shore, distance from port, and whether or not the vessel is believed to be fishing or not). The main objective of my project was to use a regression model to determine which variables are good predictors of fishing. 

## Investigators

Cristiana Falvo

## Keywords

fishing, global fishing watch, longline, regression model, tidyverse, statistics

## Folder structure, file formats, and naming conventions 

The following folders are included in this repository:
- Data: contains folders for raw and processed data
- Code: contains separate R scripts for each stage of the general processing (data processing, data analysis)
- Output: contains outputs from analysis including charts, graphs and statistics

## Database Information

Longline fishing data: 
- CSV data 
- Downloaded from https://globalfishingwatch.org/data-download/datasets/public-training-data-v1 
- Downloaded on March 25, 2020

## Scripts and code

Within the 'Code' folder:
- Wrangling_LonglineData: this script brings the raw data into R for some initial data frame exploration and cleaning. The script transforms the raw longline data to processed longline data by filtering and reformatting columns in order to prepare the data for analysis. More detailed documentation is included throughout the script. 

## Metadata

Longline.csv
- mmsi: Anonymized vessel identifier
  + Values:
    - Vessel 1
    - Vessel 2
- Date: Date (YYYY-MM-DD)
  + Date range: 2012-06-02 through 2013-12-31
- Time: Time (H:M:S)
  + Time range: 00:00:38 - 23:59:51
    - 24 hour time format
- lat: Latitude (decimal degrees)
  + Range: 	7.855130 - 59.72647
- lon: Longitude (decimal degrees)
  + Range: 	-178.3234 - -8.751204
- speed: Vessel speed (knots)
  + Range: 0.0 - 14.4  
- distance_from_shore: Distance from shore (meters)
  + Range: 0 - 1207965.9
- distance_from_port: Distance from port (meters)
  + Range: 0 - 1238047.1
- is_fishing: Label indicating fishing activity.
  + Values:
    - 0 = Not fishing
    - 1 = Fishing

## Quality assurance/quality control

<detailed methods and QA/QC process will be updated iteratively as project progresses>

<describe any relevant QA/QC procedures taken with your data. Some ideas can be found here:>
<https://www.dataone.org/best-practices/develop-quality-assurance-and-quality-control-plan>
<https://www.dataone.org/best-practices/ensure-basic-quality-control>
<https://www.dataone.org/best-practices/communicate-data-quality>
<https://www.dataone.org/best-practices/identify-outliers>
<https://www.dataone.org/best-practices/identify-values-are-estimated>