# COVID-19 US Twitter Data Visualization

This project aims to show which US states are tweeting the most about COVID-19 and whether the number of COVID-related tweets increases with the number of cases. State data is over a period of 20 days (7/25-8/13) and daily data is over a period of 19 days (7/26-8/13).

## Visualization:

![Which states are tweeting about COVID-19 the most?](https://github.com/daviddecorso/covid-tweet-viz/blob/master/Which%20states%20are%20tweeting%20the%20most%20about%20covid.png)

These charts show which states are tweeting the most about COVID-19, which states have the most cases, and which states tweet the most for the amount of cases they have. The most tweets were sent from Washington, D.C. for the number of cases in the city. Vermont was the state that tweeted the most for the amount of cases they have. The amount of tweets sent from each state was related most closely to the state's population, although New York and California tweeted more per capita than other large states, like Texas and Florida.

![Do people tweet more when cases rise?](https://github.com/daviddecorso/covid-tweet-viz/blob/master/Do%20people%20tweet%20more%20when%20cases%20rise.png)

![COVID-19 cases vs daily tweets](https://github.com/daviddecorso/covid-tweet-viz/blob/master/Tweets%20vs%20daily%20cases.png)

These graphs show the amount of tweets per day plotted against the number of new cases per day to see if tweets correlated with new cases. There seems not to be any correlation between tweets and cases, even if the tweets are compared to the previous day's cases.

For further analysis I would like to compare weekly averages of tweets and cases over a longer period of time to see if a larger correlation is present. Unless an extremely large spike in cases occurs, I wouldn't think it likely for many more people to be tweeting about COVID than the day before due to case numbers. News stories from influential people or outlets are much more likely to have an effect on day-to-day numbers. Unfortunately, the COVID-19 tweets dataset used in this project only has tweets from July 15th and later making a longer-term averaged analysis impossible to carry out with this data.

## Data Sources

**[COVID-related tweets dataset](https://www.kaggle.com/gpreda/covid19-tweets)**

**[United States COVID dataset](https://github.com/nytimes/covid-19-data)**

**[World COVID dataset](https://ourworldindata.org/covid-cases)**

## Cleaning & Methodology

### Cleaning:

The COVID-19 tweets dataset needed the most cleaning of the datasets used in this project. Twitter has an option for users to display their location on their profile, but the location is merely a text box where users can input anything they wish, or nothing at all. Therefore the user location column needed quite a bit of cleaning to be usable for this project. Below is a sample of user location data from the dataset. None of the data is standardized, although much of it is usable with some cleaning (like rows 3, 4, 8, etc.). Some of the data is completely unusable (rows 2, 5, 7, 9, etc.) and must be removed if location is being considered.

![Raw user location data from COVID-19 tweets dataset](https://github.com/daviddecorso/covid-tweet-viz/blob/master/readme_images/dirty%20tweet%20location%20data.PNG)

To clean the location data I first dropped all rows with no data. This left a large dataset of ~70,000 items. Then, I converted all city/state locations (i.e. Orlando, FL) to just their abbreviations. Next I dropped all unique locations, since these are likely unusable (an example would be row 14 from the above image). Next, I converted all locations in the format "State, US/USA/United States" to the abbreviation of the state. I chose not to just keep state names in the location field that aren't formatted, since someone could set their location as "I used to live in Florida," for example. They likely don't live in Florida, but this approach would count them as living in Florida. Since the dataset is very messy I decided to be as sure as possible of a user's location. This left me with about 13,000 tweets from the United States. I also changed the date format from MM:DD:YYYY, HH:MM to MM:DD:YYYY.

For the daily data I summed all of the tweets of a certain date from the USA and Global datasets and compared them with COVID-19 cases from the US and World COVID-19 datasets.

### Methodology:

To find the amount states tweeted relative to the amount of cases they had, I divided the number of tweets by the number of cases in each state.

For the daily data comparing tweets to amount of new cases, I plotted the two against each other in a scatter plot and checked for any correlation. Days with more new cases didn't necessarily have more COVID-related tweets for the US and Global data. As I previously mentioned, I would like to have done a longer-term look at this to see if a correlation manifests, but I couldn't find a usable longer-term dataset.
