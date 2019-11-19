# U Gotta Have Faith

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

## Data Source
8 CSV files provided by client

## Data preparation (including definitions for unfamiliar or new variables)
- Because of the multiple data formats, the CSV files were manually merged into a single CSV file using Excel 
- "Calories in" and "Food logs" were deleted because nearly all the values were 0
- Commas were deleted from the numbers
- Extraneous headings were deleted
- The CSV file of the data was then uploaded in Python

Drop first row of data so we have full weeks, every week. First row was selected to avoid a break in the data at the end since we need to project out 2 weeks from the end.
Add column that totals all 

