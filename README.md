# Team U Gotta have Faith

## Fitbit Project

### Faith Kane and Sean Oslin


## Goal
Analyze Fitbit data to
 - Project the two weeks of missing data
 - Determine what extra data label was included
 - Create a profile of the person who possesses the Fitbit

## Presentation
- Link to talking notes: https://docs.google.com/document/d/1ZO2QyTw_OPFJiSD809HGs8NS0LZAUo3cKpqXwfmCoxg/edit?usp=sharing
- Link to slide deck: https://docs.google.com/document/d/1ZO2QyTw_OPFJiSD809HGs8NS0LZAUo3cKpqXwfmCoxg/edit?usp=sharing


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
About a dozen days when the user did not wear the Fitbit  we imputed missing values for steps and distance using rolling median, although we tried 3 additional methods as well. They all performed about the same. 


## Exploration
- Nearly all calories burned are activity calories (r = .97)
- Steps and distance are perfectaly correlated (r = 1.00)
- Sedentary minutes are negatively correlated with calories_burned (r = -.57) and activity_calories (r = -.65)
- There are 0 values for steps in the following dates/date ranges
    - 6/6 - 6/7
    - 6/11
    - 6/26 - 6/30
    - 7/3 - 7/6
- Because these dates also lacked distances, we hypothesize that the user of the Fitbit did not wear it on these days.
- All the missing days are clustered early in the user's history with the Fitbit. No missing days are found after the first quarter of usage.
- Calorie burning increased as the week progressed
- No surprise, as the active minutes increased and sedentary minutes decreased, calories increased
- Calories burned, steps and activity increased over time. Our hypothesis is that the user was motivated in some fashion to become more active
An analysis of missing values indicated that the primary ones that could be recovered without extraordinary means were steps and distance.


## Imputing missing values
- We ran 4 different methods to impute missing values for steps and distance: rolling median, rolling mean, expanding steps and exponentially weighted moving average (EWMA). Every available method except Prophet.
- All methods returned roughly the same answer (see graph). We arbitrarily chose the rolling median method to impute the missing values


## Calculating height of person X
- We calculated the stride by calculating the ratio of distance to steps
- Using the average stride we were able to calculate a rough estimate of height = 68 inches.
- Comparing the average height of men and women in the US, we established that likelihood person X is male is greater than the likelihood person X is female.



## Hypotheses
$H_0$: The Fitbit user has held a steady activity level during the time range of our data.

$H_a$: The Fitbit user has not held a steady activity level during the time range of our data.

We reject the null hypothesis that the user's activity level stayed steady based on data. Data show

- Upward trend in activity for the Fitbit wearer, including a 48% increase in steps and 358% increase in very active minutes. 
- The wearer's sedentary minutes decreased by 44%



$H_0$: The Fitbit user wore their activity band every day since the beginning of the data set range.

$H_a$: The Fitbit user did not wear their activity band every day since the beginning of the data set range.

Conclusion: we cannot assess this hypothesis definitively based on available data. However, the data seem to indicate that

- The Fitbit user did not wear their device for approximately 2 weeks during in the first quarter of the date range. Values for steps and distance were both 0 on those days. We do not believe it is possible to take 0 steps in a day, especially for several days in a row.

- The days with 0 values for steps and distance were early in the date range when the user may not have been as committed or accustomed to wearing the band.

- As the activity trend increases, the Fitbit is worn consistently.

- We believe there may have been some incentive to wear the band that motivated the user to not only continue to wear the band more and encouraged them to be more active.

