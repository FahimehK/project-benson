# Project-Benson
## Metis Project-01 MTA Data Analysis


### *Primary Goals:*

Our primary goal in this presentation is to maximize the number of signatures obtained at subway station entrances/exits via street marketing teams, focusing on those individuals who will attend the gala and contribute to WTWY’s cause.

To do so, we will look at MTA subway data as well as NYC Census data to determine, not just the busiest stations, but the stations with the most value-added individuals considering our prompt above. In addition, we plan to look at technology companies in the areas near stations to determine best allotment of street marketing team placement. 


### *Data URLs with labels:*

1. Here is the link to [MTA Data](http://web.mta.info/developers/turnstile.html).
2. Here is the link to [New York Home Prices & Values Data](https://www.zillow.com/new-york-ny/home-values/).
3. Here is the link to [Data Reference: Mapping NYC's top 10 most funded zip codes](https://www.builtinnyc.com/2016/08/09/nyc-fundings-zipcode-2016).


### *Methods/Write-Up:* 

Possible ways to address the problem: 
1. Determine the busiest stations within a set collection period.
2. Determine time of day with highest traffic per station.
3. Look at housing value data in zip codes near stations to determine high-income earners.
4. Determine the presence of other tech companies in the areas near strations.
5. Determine the demographic information for each station (focusing on those who will attend the gala and contribute to their cause).
6. Benchmark promotional periods for other conventions.
7. We need to convert the date into a standard date time object by day of the week. 


### *Working Steps:* 

#### Step 1 Data Gathering
We used browser extension mass downloader to batch download all of these onto local drive. Data files come from March to May 2019 for marketing the gala event happens in early summer. We then combined above txt files into singular files and read into our notebook. 

#### Step 2 Data cleansing
Determine which columns will be value-added to support our above goals. Drop any columns that are unneeded for our analysis. Critically look at data in comparison to our goals and determine what we needed to edit/clean in order to effectively answer our questions.

After importing the data we find that each day of collection is broken up into 6 ‘collection periods. It appears that the a cumulative count of the turnstiles is taken at the following time: 3AM, 7AM, 11AM, 3PM, 7PM, and 11PM. This means there are a total of 6 "4-hour" collection periods within each day of the dataset. 

Looking at the collection statistics it appears that the total number of entrances and exits are cumulative. However, there are random additions and subtractions to the data that we will need to take into account. For example, the cumulative exit count at the end of one day then is lower the following day. We thus need to take into account any outliers in the data. 

For the DESC column we filtered this column for REGULAR so that we do not collect irregular patterns in the data. We should constantly be capturing 4-hour blocks of information or ‘regular’ auditing periods. 

As a start we should take the station/turnstile data and sum to get a daily total of both entries and exits PER DAY. This will give us a look at the top stations in the dataset from an overall volume perspective.

From here, we should take these top stations in the dataset and look at day of the week in order to understand how weekday vs. weekend traffic affects their overall position in the dataset. 

#### Step 3 Data Analysis and Visualization
To do this we need to group daily entries and exits together and see how the number trends per day of the week across the collection period
Group by Day of the Week and then sum the total traffic
Clearly the weekday traffic is much stronger
Table would be station...day of week….total traffic

Finally, we should break down this daily column into the hourly collection periods to understand how the traffic volume changes per day. This is where we’ll want to split off into both an entries and exit graph to see traffic patterns per station at certain times of the day (see above point re: montgomery station and commuters) 

Here we will need to first identify our top stations...we can start with 5-10.
We will need to group by stations and then display the hourly total of traffic

We should plot a line chart of the top stations in both above instances to visually see patterns in the data. 

Once we have an idea of the most populous hours we should correlate this data with our external datasets. We have the stations by zip code as well the following:

Prominent tech companies in the NYC area
Zillow home values in NYC 

If we find that some of our most trafficked stations are in the zip code of the prominent tech companies + the top homes. We should recommend that client staff street marketing teams there. 

### *UPDATE:*

We should focus on the quality of leads vs. the quantity of traffic at the station. While it is important to clean the data and have an understanding of how to parse by day, hour etc. We should only use the turnstile data to obtain a general understanding as to overall traffic, general peak times and trends throughout days of the week.

Through our analysis we unequivocally see that weekends have lesser traffic than weekdays. Not only that but intuitively we are trying to hit working professionals and commuters in the tech community (who are also affluent!).

Thus, once we get general data from the turnstiles we should move quickly into detailed demographic data:

Questions to answer:

Where are the high value neighborhood that people commute from (zillow data)
Where do high income earners live? (census data)
Where are major tech companies located in NY (need to research) 

Once we have this information we should map our intersects (zip codes that hit more than one bullet) with a list of stations within those zip codes. We can rank stations within those zip codes for traffic volume and then look specifically at those stations with a time-series plot to see how traffic patterns look hour by hour

Hourly Stations:

We need to get a time series plot per station (or aggregating all the stations) that looks at hourly traffic throughout the period. We don’t really care about dates, just how collection periods correlate with traffic over the entire dataset.

X axis needs to be the hourly collection period
Y axis needs to be total traffic

Time permitting we can break this down into entries and exits but for now we should start with total traffic


