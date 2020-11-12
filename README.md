Hello everybody and welcome to my cyclist volume predictor project! In this project I build a machine learning model that can predict the number of cyclists out on the city streets of our great city of Ottawa using weather data.

# Motivation
The motivation behind this project was pretty simple. I'm a huge fan of professional bike racing. So I have always wanted to do a machine learning project related to bikes. I'm also very passionate about the bike industry (the business side) and my (new) city of Ottawa. So I figured why not combine those passions to create a tool that a business could use to predict the number of riders that might be buzzing around the streets on a given day. It also helped that for 2 weeks this fall I was stuck in an air BnB basement, prohibited from leaving, because I had to self-isolate after visiting family in New York. And during those 2 weeks, 2 of the most important and high-profile bike races on the calendar were going on in Europe. At the same time. So bikes were definitely on the brain. 

I figured this tool might have some business benefits in a few ways. First of all, any bike-related promotions or businesses would definitely want to make sure they were occurring on days when there are lots of cyclists out there. Both pleasure-riders and commuters. Here I'm referring to pop up shops or carts that would actually be out on the street. Cycling advocacy groups or environmental groups might also want to know this. Anyone could tell you that there's more riders out in summer than winter, and we all know there's more riders out on sunny days than on rainy days, but how do these factors affect the actual numbers? This data could be useful for city planning, event planning, cycling safety workshops, etc...

As a student of machine learning, I also spend some time browsing kaggle.com. And while over there I found an interesting competition a few years ago that made a similar attempt. 
This competition challenged the participants to predict the number of bikeshare trips occurring on any given hour of any given day in the city of Washington DC, given weather conditions. I used this competition as inspiration and put my own spin on the project.  
Https://www.kaggle.com/c/bike-sharing-demand/overview

The major differences between the kaggle competition and what I am attempting are:
- kaggle competition has accurate hourly data on how many bikeshare trips were taken. This data is clean and reliable, right from the bikeshare company. In my project, I am trying to predict the total number of cyclists out on a given day, not just bikeshares. And I have no bikeshare company whose data I can use. I need to figure this number out a different way.
- Kaggle competition has already compiled its data set such that it already merged hourly bikeshare trip counts and weather data, hour-by-hour. I will need to get the weather data a different way and link it to the cyclist counts on my own

# Data sources

## Bike sensor data

The first thing I had to figure out is how to know the number of cyclists out on a given day. Luckily the city of Ottawa open data is great for this. Actually, most big cities have their own open data portals that make great datasets for new machine learning projects. For this one, I was easily able to download the dataset at this link.
Https://open.Ottawa.ca/datasets/bicycle-trip-counters.

To summarize, all over the city, at prominent intersections or entry points to the city (ie bridges), there are sensors that sense when a bike rolls by. These exist for the exact purpose that we need, and should give a decent estimation of the total number of bikes out on the streets on any given day. Obviously there is some error in the measurements, and obviously, there are bike trips occuring that do not cross these sensors, but it's a great place to start and will give a good enough estimate for our purposes.

The output file is an xlsx spreadsheet with 4x sheets. One each for the years 2016-2019. Each sheet has data for all sensors in operation that year.

## Weather data

Of course, weather data is also public. So I just needed to find and download some historical weather data from stations in Ottawa. This was easily done by navigating to the following link: 
https://climate.weather.gc.ca/climate_data/daily_data_e.html?hlyRange=%7C&dlyRange=1889-11-01%7C2020-10-22&mlyRange=1889-01-01%7C2006-12-01&StationID=4333&Prov=ON&urlExtension=_e.html&searchType=stnProx&optLimit=yearRange&Month=12&Day=25&StartYear=2014&EndYear=2020&Year=2016&selRowPerPage=25&Line=0&txtRadius=25&optProxType=city&selCity=45%7C26%7C75%7C42%7COttawa&selPark=&txtCentralLatDeg=&txtCentralLatMin=0&txtCentralLatSec=0&txtCentralLongDeg=&txtCentralLongMin=0&txtCentralLongSec=0&txtLatDecDeg=&txtLongDecDeg=&timeframe=2

And downloading historical climate data from this station. I used the download button to get the full year's worth of daily data for 2016 to 2019. Which makes 4x csv files with the following names:  
en_climate_daily_ON_6105976_2019_P1D.csv  
en_climate_daily_ON_6105976_2018_P1D.csv  
en_climate_daily_ON_6105976_2017_P1D.csv  
en_climate_daily_ON_6105976_2016_P1D.csv  

# Ready for Modeling

As you can guess, both data sets were pretty dirty. Especially the bike sensor data. With any real-world measurement, some can't be trusted. And some straight up aren't there. So the project had a good amount of data cleaning to do at the very start.

But if you're interested to see how it all turned out, take a trip on over to the code and follow along!
