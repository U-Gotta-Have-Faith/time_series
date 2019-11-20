# U Gotta have Faith

## Fitbit Project

### Faith Kane and Sean Oslin


## Goal
Analyze Fitbit data to
 - Project the two weeks of data missing at the end of the provided data
 - Determine what extra data label was included
 - Create a profile of the person who possesses the Fitbit


## Included with Github
- Cleaned data set ready for followup analyses in CSV format
- Jupyter notebook with calculations/analysis
- README with detailed notes on the project
- Text files with functions for the various stages of the product
- Projections for the missing data saved in a CSV file

## Data Source and Background on Fitbit
- 8 CSV files provided by client from the Fitbit data for a single individual
- The original data was 225 rows with 9 attributes

### From the Fitbit Website
How accurate are Fitbit devices?
https://help.fitbit.com/articles/en_US/Help_article/1136/?l=en_US&c=Topics%3AAccuracy&fs=Search&pn=1#bike

How does my Fitbit device calculate my daily activity?
https://help.fitbit.com/articles/en_US/Help_article/1141


## Data preparation (including definitions for unfamiliar or new variables)
- Because of the multiple data formats, the CSV files were manually merged into a single CSV file using Excel 
- "Calories in" (which appears twice) and "Food logs" were deleted because nearly all the values were 0
- The first row of data was dropped so we have full weeks, every week. First row was selected to avoid a break in the data at the end, the date when our two week projected will begin.
- Date was changed to DateTimeIndex when the data were read in
- Several columns were renamed
- New columns
-- active_total = total of the 3 different activity columns
-- ratio_act_sed = ratio of active time to sedentary time
-- stride = ratio of distance to steps
-- ratio_cal_steps  = ratio of calories to steps
-- ratio_sed_cal = ratio of sedentary time to calories
- NaNs were replaced with 0s
- The number of 0s per attribute were calculated dates with missing steps and/or distances were identified.




