# ETL_Project
__Rebecca Melo__

December 5th, 2021

Emerson College Bootcamp, Data Analytics

<h1> Project 2: ETL </h1>
<h2> Daily Vehicle Travel During the COVID-19 Public Health Emergency vs. Accidents in the US </h2>

This 

_____________________________________________________________________________________________

<h2>Extract:</h2> 
Extracted data from 2 csv files

Data Sources:
- Trips_by_Distnace.csv - Bureau of Transportation Statistics
- US_Accidents_Dec20_updated.csv - Kaggle.com

_____________________________________________________________________________________________

<h2>Transform:</h2>
Created 16 tables from both csv files. 
- Used .fillna() to replace null values for 0
- Used .loc() to filter Trips_by_Distnace.csv for National level, state  level, and county  level.
- Used .drop() to remove unwanted colunms not pertaining to analysis
- Filtered tables by dates of 2019-01-01 to 2020-12-31 to focus on analyizing data within those 2 years. Both datasets are extremely large, so I decided just to filter the Trips_by_Distance dataset & the US Accidents dataset 
-  Used .loc() to filter tables for State and County to __two States: MA & NM.__ Since both these datasets are very large and it would take a long time to load 3,000,000 rows in pgAdmin for every state's county in the US, I focused on  just two states. That way, you can compare  MA and NM and see how they differ, especially considering these two states are fairly different.
- Used .str.split to seperate Date and Time in the US_Accidents dataset. After, .join was used join this new table to the oringal table and drop the orginal combined Start_Time and End_Tiem colunms.
- Used .rename() to rename some colnms in the US_Accidents dataset to clarify data
- Used .set_index() to have the ID colunm in the US_Accidents dataset to be the index. These IDs were used as primary keys.

_____________________________________________________________________________________________

<h2>Load:</h2>
Loaded data into pgAdmin/PostgreSQL

The tables created  were as follows:
- __national_population_at_home:__ Population Stayed at Home vs Not by Nataionl Level
- __national_trips:__ Trips (in miles) taken by National Level
- __state_population_at_home:__ Population Stayed at Home vs Not by State Level
- state_trips: Trips (in miles) taken by State Level
- __ma_population_at_home:__ Population Stayed at Home vs Not in MA
- __ma_trips:__ Trips (in miles) taken in MA
- __ma_county_population_at_home:__ Population Stayed at Home vs Not in MA by County
- __ma_county_trips:__ Trips (in miles) taken in  MA by County
- __nm_population_at_home:__ Population Stayed at Home vs Not in NM
- __nm_trips:__ Trips (in miles) taken in NM
- __nm_county_population_at_home:__ Population Stayed at Home vs Not in NM by County
- __nm_county_trips:__ Trips (in miles) taken in NM by County
- __us_accidents:__ Accidents in the US by ID
- __ma_accidents:__ Accidents in the MA by ID
- __nm_accidents:__ Accidents in the NM by ID


