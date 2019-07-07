# Project-Benson
## Metis Project-01 MTA Data Analysis


### *Primary Goals:*

Our primary goal in this presentation is to maximize the number of signatures obtained at subway station entrances/exits via street marketing teams, focusing on those individuals who will attend the gala and contribute to WTWY’s cause.

### *Methods/Write-Up:* 

To do so, we will look at MTA subway data as well as NYC Census data to determine, not just the busiest stations, but the stations with the most value-added individuals considering our prompt above. In addition, we plan to look at technology companies in the areas near stations to determine best allotment of street marketing team placement. 

Before continuing we did have some constraints on this project: 

What is their marketing budget for street teams? (to determine how many stations we can post people at)
Historical data about their previous collection efforts? (the email mentions they have done collections before...I’d be interested to see the demographic information of those that signed up...I’d also be interested in looking at who actually donated/attended the gala from the sign-ups
Primary promotional period for conventions? (how long in advance do typical conventions promote their event?)

These constraints led us to a number of assumptions: 
We should target high-income earners with a bachelor’s degree or higher. We assume those with a higher income will be more willing/able to donate.
While both males and females may be interested in the cause, we should primarily target females considering the company in question
We should target those working for tech companies in the area
We should focus on marketing the event in the Spring season leading up to summer (March - May)

Possible ways to address the problem: 
Determine the busiest stations within a set collection period
Determine time of day with highest traffic per station
Determine the demographic information for each station (focusing on those who will attend the gala and contribute to their cause)
Determine the presence of other tech companies in the areas near strations
Benchmark promotional periods for other conventions
Look at housing value data in zip codes near stations to determine high-income earners


We need to convert the date into a standard date time object by day of the week. 

### *Data URLs with labels:*




(used browser extension mass downloader to batch download all of these onto my local drive)

### *Working Steps:* 

For determining MTA stations with the greatest traffic 

Combined above txt files into singular files and read into our notebook. Note: this is a huge amount of data so we will start with a single year and branch out from there.
Get a feel for the data using general pd function (describe, info, head, columns etc.)
Determine which columns will be value-added to support our above goals. Drop any columns that are unneeded for our analysis
Critically look at data in comparison to our goals and determine what we needed to edit/clean in order to effectively answer our questions

After importing the data we find that each day of collection is broken up into 6 ‘collection periods. It appears that the a cumulative count of the turnstiles is taken at the following time:

3AM
7AM
11AM
3PM
7PM
11PM

This means there are a total of 6 4-hour collection periods within each day of the dataset. 

Looking at the collection statistics it appears that the total number of entrances and exits are cumulative. However, there are random additions and subtractions to the data that we will need to take into account. For example, the cumulative exit count at the end of one day then is lower the following day. We thus need to take into account any outliers in the data. 

Furthermore, according to the key at the web.mta site, the column: 

DESC     = Represent the "REGULAR" scheduled audit event (Normally occurs every 4 hours)
           1. Audits may occur more that 4 hours due to planning, or troubleshooting activities. 
           2. Additionally, there may be a "RECOVR AUD" entry: This refers to a missed audit that was recovered.

My assumption here is that we should filter this column for REGULAR so that we do not collect irregular patterns in the data. We should constantly be capturing 4-hour blocks of information or ‘regular’ auditing periods. 

Let’s now work through the Metis challenges to parse through this data in an effective and guided way. 

The columns are for both the entries and the exits to the station. Both are important. As an example, think of Montgomery St station at 8am vs. 5pm. We would expect to see a spike in exits (commuters going to work) in the morning and entrances (commuters leaving work) in the evening.

As a start we should take the station/turnstile data and sum to get a daily total of both entries and exits PER DAY. This will give us a look at the top stations in the dataset from an overall volume perspective.

From here, we should take these top stations in the dataset and look at day of the week in order to understand how weekday vs. weekend traffic affects their overall position in the dataset. 

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


---------

Proposed slides: (may need to update...see above)

Into + Problem Statement (Nick)
Desc of scope + methodology (Nick
(chart)Overall Traffic Patterns (Daily Entries + Exits holistically) (Shuo)
(chart)Hourly Traffic Patterns (Shuo)
External Data Sets / Zip Codes / Tech Companies (Shuo)
(chart) Integration of External Data sets with (Shuo)
Conclusions / Findings / Areas for future study (Nick
Questions? (All)
Appendices (if time permits) (All)

