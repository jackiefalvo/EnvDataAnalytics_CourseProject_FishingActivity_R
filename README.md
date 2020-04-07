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
-Data: contains folders for raw and processed data
-Code: contains separate R scripts for each stage of the general processing (data processing, data analysis)
-Output: contains outputs from analysis including charts, graphs and statistics

## Database Information

Longline fishing data: 
-CSV data 
-Downloaded from https://globalfishingwatch.org/data-download/datasets/public-training-data-v1 
-Downloaded on March 25, 2020

## Scripts and code

Within the 'Code' folder:
-Processing_LonglineData: this script reads in the raw longline CSV data, explores it, and processes it for analysis preparation. Full documentation is included as comments in the code. 

## Metadata

Longline.csv
-mmsi: Anonymized vessel identifier
-timestamp: Unix timestamp
-distance_from_shore: Distance from shore (meters)
-distance_from_port: Distance from port (meters)
-speed: Vessel speed (knots)
-lat: Latitude in decimal degrees
-lon: Longitude in decimal degrees
-is_fishing: Label indicating fishing activity.
--0 = Not fishing
--1 = Fishing. Data values between 0 and 1 indicate the average score for the position if scored by multiple people.

## Quality assurance/quality control

<detailed methods and QA/QC process will be updated iteratively as project progresses>

<describe any relevant QA/QC procedures taken with your data. Some ideas can be found here:>
<https://www.dataone.org/best-practices/develop-quality-assurance-and-quality-control-plan>
<https://www.dataone.org/best-practices/ensure-basic-quality-control>
<https://www.dataone.org/best-practices/communicate-data-quality>
<https://www.dataone.org/best-practices/identify-outliers>
<https://www.dataone.org/best-practices/identify-values-are-estimated>